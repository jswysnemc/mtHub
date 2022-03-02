### Easyx图形库

#### 以下代码打开一个图像窗口,并设置背景色

``` c
initgraph(640,480);
setbkcolor(RGB(234,20,23));
cleardevice();//刷新窗口
closegraph();//关闭图形化窗口
```

#### 以下代码绘制带边框的填充矩形

```c
setlinecolor(BLACK);
setfillcolor(YELLOW);
fillrectangle(10,10,80,80);
```

#### 画无边框的填充圆

```
setfillcolor(food.color);
fillellipse(food.fd.x, food.fd.y, food.fd.x + 10, food.fd.y + 10);
```

```c
// 绘图函数

COLORREF getpixel(int x, int y);				// 获取点的颜色
void putpixel(int x, int y, COLORREF color);	// 画点

void line(int x1, int y1, int x2, int y2);		// 画线

void rectangle	   (int left, int top, int right, int bottom);	// 画矩形
void fillrectangle (int left, int top, int right, int bottom);	// 画填充矩形(有边框)
void solidrectangle(int left, int top, int right, int bottom);	// 画填充矩形(无边框)
void clearrectangle(int left, int top, int right, int bottom);	// 清空矩形区域

void circle		(int x, int y, int radius);		// 画圆
void fillcircle (int x, int y, int radius);		// 画填充圆(有边框)
void solidcircle(int x, int y, int radius);		// 画填充圆(无边框)
void clearcircle(int x, int y, int radius);		// 清空圆形区域

void ellipse	 (int left, int top, int right, int bottom);	// 画椭圆
void fillellipse (int left, int top, int right, int bottom);	// 画填充椭圆(有边框)
void solidellipse(int left, int top, int right, int bottom);	// 画填充椭圆(无边框)
void clearellipse(int left, int top, int right, int bottom);	// 清空椭圆形区域

void roundrect	   (int left, int top, int right, int bottom, int ellipsewidth, int ellipseheight);		// 画圆角矩形
void fillroundrect (int left, int top, int right, int bottom, int ellipsewidth, int ellipseheight);		// 画填充圆角矩形(有边框)
void solidroundrect(int left, int top, int right, int bottom, int ellipsewidth, int ellipseheight);		// 画填充圆角矩形(无边框)
void clearroundrect(int left, int top, int right, int bottom, int ellipsewidth, int ellipseheight);		// 清空圆角矩形区域

void arc	 (int left, int top, int right, int bottom, double stangle, double endangle);	// 画椭圆弧(起始角度和终止角度为弧度制)
void pie	 (int left, int top, int right, int bottom, double stangle, double endangle);	// 画椭圆扇形(起始角度和终止角度为弧度制)
void fillpie (int left, int top, int right, int bottom, double stangle, double endangle);	// 画填充椭圆扇形(有边框)
void solidpie(int left, int top, int right, int bottom, double stangle, double endangle);	// 画填充椭圆扇形(无边框)
void clearpie(int left, int top, int right, int bottom, double stangle, double endangle);	// 清空椭圆扇形区域

void polyline	 (const POINT *points, int num);								// 画多条连续的线
void polygon	 (const POINT *points, int num);								// 画多边形
void fillpolygon (const POINT *points, int num);								// 画填充的多边形(有边框)
void solidpolygon(const POINT *points, int num);								// 画填充的多边形(无边框)
void clearpolygon(const POINT *points, int num);								// 清空多边形区域

void polybezier(const POINT *points, int num);									// 画贝塞尔曲线
void floodfill(int x, int y, COLORREF color, int filltype = FLOODFILLBORDER);	// 填充区域

```

### 获取按键 鼠标消息

``` c
char c;
if(kbhit())
c=getch();

MOUSEMSG m;
while (true)
{
	m = GetMouseMsg();
	if (m.uMsg == WM_MOUSEMOVE)
	{
		putpixel(m.x, m.y, WHITE);
	}
} 
```

```c
/ “鼠标操作”相关函数
// 鼠标消息
// 支持如下消息：
//		WM_MOUSEMOVE		鼠标移动
//		WM_MOUSEWHEEL		鼠标滚轮拨动
//		WM_LBUTTONDOWN		左键按下
//		WM_LBUTTONUP		左键弹起
//		WM_LBUTTONDBLCLK	左键双击
//		WM_MBUTTONDOWN		中键按下
//		WM_MBUTTONUP		中键弹起
//		WM_MBUTTONDBLCLK	中键双击
//		WM_RBUTTONDOWN		右键按下
//		WM_RBUTTONUP		右键弹起
//		WM_RBUTTONDBLCLK	右键双击
struct MOUSEMSG
{
	UINT uMsg;				// 当前鼠标消息
	bool mkCtrl		:1;		// Ctrl 键是否按下
	bool mkShift	:1;		// Shift 键是否按下
	bool mkLButton	:1;		// 鼠标左键是否按下
	bool mkMButton	:1;		// 鼠标中键是否按下
	bool mkRButton	:1;		// 鼠标右键是否按下
	short x;				// 当前鼠标 x 坐标
	short y;				// 当前鼠标 y 坐标
	short wheel;			// 鼠标滚轮滚动值 (120 的倍数)
};
_EASYX_DEPRECATE							bool MouseHit();			// 检查是否存在鼠标消息
_EASYX_DEPRECATE_WITHNEW(getmessage)		MOUSEMSG GetMouseMsg();		// 获取一个鼠标消息。如果没有，就等待
_EASYX_DEPRECATE_WITHNEW(peekmessage)		bool PeekMouseMsg(MOUSEMSG *pMsg, bool bRemoveMsg = true);	// 获取一个鼠标消息，并立即返回
_EASYX_DEPRECATE_WITHNEW(flushmessage)		void FlushMouseMsgBuffer();	// 清空鼠标消息

```

### 图像输出

```c
IMAGE img[1];
loadimage(img, L"./0.png");
putimage(100, 100, img,NOTSRCERASE);//遮罩
putimage(100, 100, img+1,SRCINVERT);
```

### 声音播放

```c
#pragma comment(lib,"Winmm.lib")
//函数外引用api
//循环播放
mciSendString(L"open ./0.mp3 alias bkmusic", NULL, 0, NULL);
mciSendString(L"play bkmusic repeat", NULL, 0, NULL);

//播放一次
mciSendString(L"open ./0.mp3 alias jpmusic", NULL, 0, NULL);
mciSendString(L"play jpmusic", NULL, 0, NULL);

//播放多次
mciSendString(L"close jpmusic", NULL, 0, NULL);//先关闭一次
mciSendString(L"open ./0.mp3 alias jpmusic", NULL, 0, NULL);//打开播放
mciSendString(L"play jpmusic", NULL, 0, NULL);
```

#### 枚举

```c
enum DIR//蛇的方向
{
	UP, DOWN, LEFT, RIGHT,
};
```

### 其他

```c
GetTickCount();//获取当前开机时间,ms
BeginBatchDraw();//开启双缓冲绘图
FlushBatchDraw();
```

