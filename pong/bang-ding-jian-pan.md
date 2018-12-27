# 綁定鍵盤

1. ##### 定義鍵盤觸發事件

   當使用者按下控制的鍵盤時，我們需要觸發一些事件來讓球拍移動。

   設定playerspeed，為每次玩家按按鈕時，球拍能移動的像素。  
   設定p1\_up\(\)函式，當使用者按下時player1球拍會向上移動。  
   設定p1\_down\(\)函式，當使用者按下時player1球拍會向下移動。  
   設定p2\_up\(\)函式，當使用者按下時player2球拍會向上移動。  
   設定p1\_down\(\)函式，當使用者按下時player2球拍會向下移動。

   我們首先透過ycor\(\)函式取得玩家球拍的y座標，將其存入變數y。  
   每呼叫一次這個函式，y座標就會 增加/減少 我們設定好的playerspeed值。  
   最後透過sety\(\)函式讓球拍移動到新的y座標。

   ```py
   playerspeed = 50

   def p1_up():
      y = player1.ycor()
      y = y + playerspeed
      player1.sety(y)

   def p1_down():
      y = player1.ycor()
      y = y - playerspeed
      player1.sety(y)

   def p2_up():
      y = player2.ycor()
      y = y + playerspeed
      player2.sety(y)

   def p2_down():
      y = player2.ycor()
      y = y - playerspeed
      player2.sety(y)
   ```

2. ##### 綁定鍵盤

   透過onkey\(\)函式，傳入參數\(函式,鍵盤名稱\)。  
   玩家1的上下移動鍵為s和x鍵，每當有人按按鍵時，便會呼叫p1\_up或p1\_down  
   玩家1的上下移動鍵為【方向鍵上】和【方向鍵下】，每當有人按按鍵時，便會呼叫p2\_up或p2\_down

   ```py
   screen.onkey(p1_up,'s')
   screen.onkey(p1_down,'x')
   screen.onkey(p2_up,'Up')
   screen.onkey(p1_down,'Down')
   ```



