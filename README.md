自动浇花系统
==========================
使用Arduinuo开发的一套简易自动浇花系统。基本原理是，利用土壤湿度传感器探测的土壤干燥程度来控制微型水泵向花盆浇水，避免花盆过于干旱或过浇。

##设备清单
* Arduinuo nuo 开发版一套
* 数字继电器模块一个
* 土壤湿度传感器多个
* 杜邦线若干
* 微型静音潜水泵一个 （12V DC）
* 912主管若干米
* 47毛管若干米
* 可调流量滴头若干

##算法主要原理

程序为了实用性，并非是简单的根据实时土壤湿度是否大于阈值进行浇水。而是设置了两个定时器，一个定时器决定下一次探测土壤湿度的时间间隔，另一个定时器防止土壤探测模块被拔出或失效所带来的过浇问题。

程序启动首先会监测一次土壤湿度，如果探测值超过设定阈值，则认为土壤过于干燥，直接进行浇水。如果探测值低于设定阈值，则根据探测值与阈值的差值更新下一次探测土壤的湿度的时间间隔，差值与时间间隔为简单的线型关系。其主要思想是，土壤湿度越大，则下一次探测土壤湿度的时间间隔越大。具体查看代码。

土壤湿度传感器可能会被拔出或者损坏，可能会导致每次探测值过高导致频繁浇水。为了避免该问题，设置了防过浇定时器，24小时之内最多浇一次水。如果土壤传感器被拔出或损坏，自动浇花系统将退化为定时浇水系统，每天浇一次水，在保证不过浇的情况下还能继续工作。

##成果图

##可改进地方

##缺点
 