# 1. spark 计算pv uv

[使用Spark计算PV、UV - 三分地 - CSDN博客](https://blog.csdn.net/laozhaokun/article/details/43196425)


pv

![image](http://static.lovedata.net/jpg/2018/12/18/9be0350c5362fdc31f7a79683ecad84d.jpg)


uv
![image](http://static.lovedata.net/jpg/2018/12/18/2a71bbfacd89969993a813b35c9e7757.jpg)



# 2. spark中使用groupByKey进行分组排序

[spark中使用groupByKey进行分组排序 - 蚂蚁搬家 - CSDN博客](https://blog.csdn.net/hongxingabc/article/details/81638011)

val topItem_set= data_set.map(ele => (ele._1, (ele._2, ele._3, ele._4))).groupByKey()
  .flatMap(line => {
      val topItem = line._2.toArray.sortBy(_._3)(Ordering[Int].reverse).
        take(2)
      topItem.map(line._1,_.1)
  })
