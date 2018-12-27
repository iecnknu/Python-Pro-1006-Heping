# 設定玩家、球

1. ##### 設定玩家1

   設定一支畫筆為玩家1，  
   再設定其大小、形狀、比例、顏色，並移動到最靠左\(- court\_width/2,0\)的位置，不過要稍微遠離邊界，往右20像素。

   ```py
    player1 = turtle.Turtle()
    player1.shape('square')
    player1.shapesize(4,0.6)
    player1.color('white')
    player1.penup()
    player1.goto(-court_width/2 + 20, 0)
    player1.speed(0)
   ```

2. ##### 設定玩家2

   設定一支畫筆為玩家2，  
   再設定其大小、形狀、比例、顏色，並移動到最靠右\( court\_width/2,0\)的位置，不過要稍微遠離邊界，往左20像素。

   ```py
    player2 = turtle.Turtle()
    player2.shape('square')
    player2.shapesize(4,0.6)
    player2.color('white')
    player2.penup()
    player2.goto(court_width/2 - 20, 0)
    player2.speed(0)
   ```

3. ##### 設計球

   設定一支畫筆為球，  
   形狀為圓形，紅邊、用紅色填滿，大小為預設的兩倍。  
   記得抬起這支畫筆，免得等一下球移動的路徑都被記錄下來。

   ```py
   ball = turtle.Turtle()
   ball.shape('circle')
   ball.shapesize(2)
   ball.color('red','red')
   ball.penup()
   ball.speed(0)
   ```

   ![](https://drive.google.com/uc?export=download&id=1RdthGKC3_D9x1YL6CJrHlzwjzypwroe0)

---

# 球的函式

每次遊戲開始，或有人得分時，球必須要回到正中心，並選擇一個隨機的角度發射出去。  
我們將這個功能寫成一個resetBall\(\)函式，當上述事件發生時，就會歸位然後發球。

> 大家切記，函式需要被定義在程式的上方\(import模組之後\)，好讓他們在程式載入時就能被存在記憶體之中，當事件被觸發時，能及時呼叫自定義的函式。

函式被呼叫時，球會回到中心。  
透過randint\(1,2\)隨機選擇向某一邊發球，  
如果向右的話，球的角度使用randint\(\)隨機從300~60度之間選一個。\(60度多繞一圈就是420度，這樣randint\(\)才能發揮作用\)  
向左的話，球的角度使用randint\(\)隨機從120~240度之間選一個。

![](https://drive.google.com/uc?export=download&id=1ASz1oOfSRUOIIZw_JsaRUCXOQdEKbmYW)

```py
import random

def resetBall():
    ball.goto(0,0)

    if random.randint(1,2) == 1:
        ball.setheading(random.randint(300,420))
    else:
        ball.setheading(random.randint(120,240))
```



