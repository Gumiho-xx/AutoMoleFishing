# AutoMoleFishing
## 摩尔手游 按键精灵自动钓鱼
## 可以看图片详解，图片在上面2.bmp 3.bmp
## [如果你要傻瓜版本，直接点我](#1)

首先得是模拟器
然后调参数，怎么调下面讲，然后点击钓鱼，运行脚本即可，注意：第一个版本遇到骨头你自己调整
```
For 30 //先钓30次吧，但是遇到骨头记得关了重启，暂时没做处理骨头的功能
a = 0
c = 0
While a = 0
	Delay 100
	IfColor 1060, 368, "7CE2FF", 2 Then  //1060,368是坐标，按prtsc截屏到ps(画图应该也行)，然后找黄色感叹号，7CE2FF是16位颜色代码
		a = 1
		MoveTo 1592,732 // 钓鱼按钮的位置，默认即可
		Delay 10
		LeftClick 1
	End If
	Wend
Delay 1500
While c = 0
	Delay 100
	FindColorEx 892,620,898,640,"6F6647",1,0.9,x,y   // 区域寻找颜色，前面4个数是坐标，6F6647是颜色同上，但是这个颜色可能会变(天气、环境、时间)，上面的黄色一般不变。0.9是颜色相似度，一般不变，如果你觉得快了就调低到0.88左右，慢了就到0.92左右
If x>50 and y>50 Then  
		c = 1
		MoveTo 1592,732
		Delay 10
		LeftClick 1
End If
Wend
Delay 3000
MoveTo 1592,732
Delay 10
LeftClick 1
Delay 1500
LeftClick 1
Next
```

下面是修正后的版本，请先根据图片知道第一个版本怎么设置的，然后可以用第二个，解决了钓到骨头和极少数脱钩的问题，可以直接钓一天。
```
For 100
Delay 1500
MoveTo 1592,732 // 这是右边那个钓鱼按钮坐标，有可能要改
Delay 50
LeftClick 1
a = 0
c = 0
While a = 0
	Delay 100
	IfColor 1070, 360, "82F3FF", 2 Then //人物头上黄色感叹号的坐标。
		a = 1
		MoveTo 1592,732
		Delay 10
		LeftClick 1
	End If
	Wend
Delay 1000
IfColor 1070, 360, "82F3FF", 2 Then// 一秒后感叹号还在表示钓的确实是鱼不是骨头
	While c < 60//设置超时时间，不超过6+1(上面的delay1000)秒，60这个数字不建议改，真超过7秒就放了吧，不然可能导致来不及判断
		Delay 100
		c = c+1
		FindColorEx 883, 622, 980, 673, "775D3B", 1, 0.88, x, y// 最重要的一步，第二个必改参数，前4个数字，前2个是绿圈内接矩形左上角坐标，后面是右下角。
		// 第三个必改参数，775D38是蓝色，用PS截图取色，比如R0 G100 B255,在网站上转换记得变成R255 G100 B0，这个最终要，取色取不好会导致不拉钩。这个颜色可能根据时间、天气、环境变化。
		// 0.88是屏幕找色要求的相似度，越大越稳但是可能会超时，一般0.88-0.92左右
		If x>50 and y>50 Then
			MoveTo 1592,732
			Delay 10
			LeftClick 1
			c = 100 
		End If
	Wend
	Delay 5000 // 此时3种可能，拉到了，没拉到，根本没拉，但是根据是否出现“是否获得”就可以判断，如果自家钓鱼钓一天，这个delay最好有5000
		IfColor 928, 253, "8CF0F8", 2 Then// 928，253，8CF0F8，是你“是否获得”的坐标和颜色。
			MoveTo 1592,732
			Delay 10
			LeftClick 1
		Else // 脱钩了或者超时，极少发生，什么都不干即可
		End If
Else //开始拉钩1秒后感叹号就没了表示钓到了骨头，直接点一下确认，继续下一轮
	Delay 5000
	MoveTo 1592,732
	Delay 10
	LeftClick 1 
End If
Next
```

---

<h1 id='1'>全世界最无脑的钓鱼脚本：</h1>
+ 不用调参
+ 全自动循环
+ 智能处理骨头、MISS、超时
+ 成功率99%
+ 失败不影响下一轮钓鱼
## 目前只更新雪山渔场，如果你能看懂上面的，把下面的改改就行了就变成别的地方的脚本了。跟第二部分的差不多
1. 设置，同屏只显示你自己
2. 设置，强制晴朗白天
3. 到雪山，图片里的位置，这个位置会卡住，然后就可以运行了
4. 模拟器开全屏(完全全屏不是窗口全屏)，分辨率1920x1080
![Image text](https://github.com/Gumiho-xx/AutoMoleFishing/blob/main/weizhi.jpg)
```
For 100
Delay 1500
MoveTo 1650,735 // 这是右边那个钓鱼按钮坐标，有可能要改
Delay 50
LeftClick 1
a = 0
c = 0
While a = 0
	Delay 100
	IfColor 1113, 267, "82F3FF", 2 Then
		a = 1
		MoveTo 1650,735
		Delay 10
		LeftClick 1
	End If
	Wend
Delay 1000
IfColor 1113, 267, "82F3FF", 2 Then
	While c < 50
		Delay 100
		c = c+1
		FindColorEx 880, 626, 977, 688, "AE7131", 1, 0.88, x, y
		If x>50 and y>50 Then
			MoveTo 1650,735
			Delay 10
			LeftClick 1
			c = 100 
		End If
	Wend
	Delay 5000
		IfColor 937, 240, "8CF0F8", 0 Then
			MoveTo 1650,735
			Delay 10
			LeftClick 1
		Else
		End If
Else
	Delay 5000
	MoveTo 1650,735
	Delay 10
	LeftClick 1 
End If
Next
```

