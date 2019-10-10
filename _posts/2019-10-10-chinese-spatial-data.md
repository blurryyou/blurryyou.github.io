---
layout: post
title: China's spatial data
featured: true
tags: [visulization]
---

Sometimes, we need to combine the data with the geographic information, plotting choropleth maps, for example. 

There are a looooot of applications for choropleth maps. 

Besides, we can use Python to plot the maps more freely. 

A few Python libs support this feature, such as Pyecharts, Plotly.graph_objs, Matplotlib, Geopandas, etc.

Among the options above, [pyecharts](https://pyecharts.org/) and plotly.graph_objs do not require to import the geometric data. You just need to specify the location you need. 

[Geopandas](http://geopandas.org/) depends on [Matplotlib](http://matplotlib.org/) for plotting, in an easier way. They both need to import the geometric data, so that Matplotlib knows how to line out the map and then filling the shapes up. 

I came across [a post, which pulled up dozens of examples of "wrong" China maps from academic thesis](https://zhuanlan.zhihu.com/p/25634886). 

I have used the [GADM data](https://gadm.org/data.html) to plot a China map of provinces, and I also found that Taiwan, Hong Kong and Macao are missing from the map. (I have no deep understanding of the Tibet so I have no idea it is right or not.)

Actually, that is because GADM defines the "country" as "any entity with an ISO country code", so that you need to combine 4 data sets, China, Hong Kong, Macao, and Taiwan, to plot a complete China map. 

(BTW, quite a lot of acts of offenses against China's sovereignty, I think, especially from companies and small businesses, are due to the different definitions of "country".)

Or you can access the China's geometric data from other sources.

* [GMT/China](https://docs.gmt-china.org/latest/), maintained by Chinese volunteers, provides [China geometric data](https://gmt-china.org/data/) in `.dat` files.
* [Resource and Environment Data, China Science Academy](http://www.resdc.cn/Default.aspx), maintained by CSA, provides `.shp` files.
* More



有时候我们需要结合地理信息呈现数据，例如绘制等值线图。

除了很多已经成熟的工具应用之外，Python 画图更自由。

Python 很多 lib 都支持地图绘制，像是 Pyecharts, Plotly.graph_objs, Matplotlib, Geopandas。

其中 [pyecharts](https://pyecharts.org/) 和 plotly.graph_objs 直接声明地区即可，不需要自己导入地理信息。

[Geopandas](http://geopandas.org/) 是基于 [Matplotlib](http://matplotlib.org/) 进行绘图的，只是作为地图专精，所以方法更简单一些。二者都需要导入地理数据，因为 Matplotlib 需要地理数据来描绘地图的形状轮廓，然后把相关的数据可视化上去。

我之前看过一篇知乎文章，里面举了十几个论文中的例子，说很多中国地图都是错的。

我自己也用过 [GADM 的数据](https://gadm.org/data.html)来绘制中国省级地图，结果发现画出来的地图里没有台湾、香港和澳门。（我看不出来藏南之类的地方有没有问题。）

但实际上，这是因为 GADM 将“国家/地区”定义为“具有 ISO 国家/地区代码的任何实体”，因此使用他们的数据，需要将中国和港澳台一共四个数据集合并，才能画出完整的中国地图。

（说句题外话，我怀疑很多企业、小公司所谓“侵犯中国主权”的行为，都是因为 "country" 经常指的是“国家或地区”。）

为了省事儿，也可以干脆从国人的数据来源获取地理数据。

- [GMT 中文社区](https://docs.gmt-china.org/latest/)是中国志愿者维护的，提供 `.dat` 格式的[中国地理数据集](https://gmt-china.org/data/)。
- [中科院资源环境科学数据中心](http://www.resdc.cn/Default.aspx)提供 `.shp` 格式的中国地理数据。
- 肯定还有更多。

