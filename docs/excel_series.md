## SERIES
SERIES是生成图表系列的专用函数，它**无法在单元格中使用，只能用在excel图表中，**  
它的语法为：=SERIES（标题,显示在分类轴上的标志,数据源,系列顺序）
  
### 数据源
  
月份  |  A   | B
---  | ---  | ---
1月|  11| 33
2月|  22| 44
3月|  33| 55
4月|  44| 66
5月|  55| 77

### 公式
=SERIES(Sheet1!$C$1,Sheet1!$A$2:$A$6,Sheet1!$C$2:$C$6,1)  
 
=SERIES(Sheet1!$B$1,Sheet1!$A$2:$A$6,Sheet1!$B$2:$B$6,2)

### 图

![pic](https://github.com/lofty77/Picture/blob/master/pic/excel_series.png)


### 注意

- Series 公式只支持一组数据，如果是多组数据，需要不断的添加公式（一个公式对应一组数据），注意公式最后一个参数代表排序顺序
- 趋势图 路径： Design-> Add Chart Element
