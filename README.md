# AutoMoleFishing
## 摩尔手游 按键精灵自动钓鱼
## 可以看图片详解，图片在上面2.bmp 3.bmp

首先得是模拟器
然后调参数，怎么调下面讲，然后点击钓鱼，运行脚本即可，注意：遇到骨头你自己调整
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
