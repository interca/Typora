# Java方法

## 一、序列化

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221107225338.png)



## 二、类型转换

可以将公共属性赋值给另一个对象

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221108190655.png)



## 三、解析excel



```JAVA
<!--解析Excel-->
<!-- https://mvnrepository.com/artifact/org.apache.poi/poi-ooxml -->
<dependency>
    <groupId>org.apache.poi</groupId>
    <artifactId>poi-ooxml</artifactId>
    <version>4.1.2</version>
</dependency>
```



```JaVA
/**
 * 解析Excel表格
 */
public class ParseExcel {
    public static String[][] submitFile(MultipartFile excel) {
        String [][] FileData;
        try {
            Workbook workbook = new XSSFWorkbook(excel.getInputStream());
            //获取Excel中的第一个工作簿
            Sheet sheet = workbook.getSheetAt(0);
            //注意这里获取的是下标
            int n = sheet.getLastRowNum();
            //存放数据的二维数组
            FileData = new String[n + 1][];
            for (int i = 0; i <= n; i++) {
                //获取一行数据
                Row row = sheet.getRow(i);
                short m = row.getLastCellNum();
                   String []FileDataRow = new String[m];
                    for (int j = 0; j < m; j++) {
                        Cell cell = row.getCell(j);
                        if(cell == null)
                            continue;
                        CellType type = cell.getCellType();
                        if(type.equals(CellType.STRING))
                        FileDataRow[j] = cell.getStringCellValue();
                       else if(type.equals(CellType.NUMERIC))
                         FileDataRow[j] = String.valueOf(cell.getNumericCellValue());
                    }
                    FileData[i]= FileDataRow;
            }
        } catch (Exception e) {
            throw new GlobalSystemException(GlobalResponseCode.USER_FORMAT_ERROR.getCode(),
                    GlobalResponseCode.USER_FORMAT_ERROR.getMessage());
        }
        return FileData;
    }

}
```