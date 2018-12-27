# 畫出場地

首先建立場景！我們來參考經典的遊戲畫面吧！

![](https://drive.google.com/uc?export=download&id=1ioVQIwvnOejWc2MhYKdIYyffFcS9vWCG)

---

1. ##### 建立背景

   使用Screen\(\)函式，建立畫布。貼上screen這個變數名稱。  
   使用setup\(\)函式，設定畫布長為螢幕的75%，寬為螢幕的75%。  
   使用title\(\)函式，設定畫布標題為'PONG!'。  
   使用bgcolor\(\)函式，設定畫步顏色為黑色

   同時，別忘了要匯入turtle模組，同時還要讓turtle的物件進入無窮迴圈喔！

   ```py
   import turtle

   screen = turtle.Screen()
   screen.setup(width=0.75, height=0.75)
   screen.title('PONG!')
   screen.bgcolor("black")

   screen.mainloop()
   ```

   ![](https://drive.google.com/uc?export=download&id=1Or-QsnsoXPplEekLICenJoqVViRnZ6mr)

2. ##### 畫出邊界

   為了讓等等的碰撞更好判別，我們將場地的長寬分別用court\_height和court\_width來定義。  
   設定一隻名為court的畫筆，依照設定的長寬來繪製方框。  
   畫筆都應該先penup\(\)抬起、同時hideturtle\(\)隱藏，設定速度為0，顏色為白色，粗度為10。  
   開始畫邊界時用pendown\(\)落下畫筆。  
   畫筆繪製的順序是：先到左上角的邊界，再依序右上角、右下角、左下角，最後回到左上角。

   ```py
   court_width = 1000
   court_height = 600

   court = turtle.Turtle()
   court.hideturtle()
   court.penup()
   court.speed(0)
   court.color('white','white')
   court.pensize(10)

   court.goto(-court_width/2,court_height/2)
   court.pendown()
   court.goto(court_width/2,court_height/2)
   court.goto(court_width/2,-court_height/2)
   court.goto(-court_width/2,-court_height/2)
   court.goto(-court_width/2,court_height/2)
   ```

   ![](https://drive.google.com/uc?export=download&id=1PdkzxN_k47F6MolqO9Ro-vsvJnQO3Ve9)

3. ##### 畫出中線

   畫出中線，我們透過一個迴圈，控制畫筆頻繁但規律的抬起與落下，設法畫出虛線。  
   首先抬起畫筆，移動到中線的位置\(0,ourt\_height/2\)，接著放下畫筆，粗度也調整為3。

   記得將畫筆的頭，朝270度的方向\(向下\)。

   我們把整條中線切成30等分，讓迴圈執行20次。

   中線總長600，迴圈總共執行20次，代表每次要移動30像素，如果要填滿，並且空白與畫線等長，則每次畫線與抬起畫筆移動皆為15像素。

   每次進入迴圈後，畫筆往前畫15像素，再將畫筆抬起往前15像素。

   ```py
   court.penup()
   court.goto(0,court_height/2)
   court.pensize(3)
   court.pendown()
   court.setheading(270)

   for x in range(court_height//30):
    court.forward(15)
    court.penup()
    court.forward(15)
    court.pendown()
   ```

   ![](https://drive.google.com/uc?export=download&id=1KwLHnc6-uP141PBDydapupgRcRpqZjWB)



