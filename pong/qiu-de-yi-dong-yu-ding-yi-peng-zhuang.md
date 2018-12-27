# 球的移動與定義碰撞

1. ##### 球的移動

   設定一個變數ballSpeed來決定球的移動速度。  
   設定move\(\)函式，每次被呼叫時，都會讓球使用forward\(\)函式往前進。

   使用screen畫布的ontimer\(\)方法，讓程式每過20毫秒，會再次呼叫move函式，以此作為無窮迴圈。

   ```py
   ballSpeed = 15

   def move():
      ball.forward(ballSpeed)
      screen.ontimer(move,20)
   ```

2. ##### 定義碰撞

   在move\(\)函式中定義碰撞，也就是每過20毫秒，程會會判斷一次球與牆壁和球拍之間的狀況。  
   使用position\(\)取得球的位置，並用x、y兩個變數來儲存。  
   ![](https://drive.google.com/uc?export=download&id=1uL8xzax3fXrptz8Mt0UyBcR7qrfI1mV8)  
   使用heading\(\)函式取得球目前的角度。  
   1.如果球碰到上下兩側的牆壁，我們要使之改變彈道，使用setheading\(\)改變其行進角度。  
   新角度為\(360度 - 舊的角度\)。  
   2.如果球超過左右邊界，呼叫resetBall\(\)重新發球。  
   3.使用distance\(\)函式，判斷球與球拍間的距離，若小於一定的值，則判定打到了需要反彈。  
   使用setheading\(\)改變其行進角度，新角度為\(180度 - 舊的角度\)。

   ```py
   def move():
      ball.forward(ballSpeed)

      x,y = ball.position()

      if y <= -court_height/2 or y >= court_height/2:
         ball.setheading(360-ball.heading())
      elif x > court_width/2 or x < -court_width/2:
         resetBall()
      elif player1.distance(ball) < 30 or player2.distance(ball) < 30:
         ball.setheading(180-ball.heading())

      screen.ontimer(move,20)
   ```

3. ##### 初始化遊戲

   最後在mainloop\(\)之上，呼叫screen畫布的listen\(\)方法，讓電腦聚焦在畫布上。  
   同時使用resetBall\(\)初始化我們的球，並第一次呼叫move\(\)函式。

   ```py
   resetBall()
   screen.listen()
   move()
   ```

   ![](https://drive.google.com/uc?export=download&id=1T5eWEEtiMkLF8yxD5EOxRa1Fx2Vo62Mr)

4. ##### 分數與優化

   我們已經完成了大致上的架構，大家可以試著調整一些參數，讓球的碰撞看起來更完美。  
   最後也可以加入分數的統計，讓玩家間一較高下；甚至是發球前的時間暫停，讓玩家有更充足的反應時間！



