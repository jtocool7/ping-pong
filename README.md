# ping-pong<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Ping Pong</title>
  <style>
  
  </style>
</head>
<body>
<center>
<canvas id="pong" width="850" height="650" ></canvas>
</center>

  <script>
  const cvs = document.getElementById('pong');
  const cxt = cvs.getContext('2d');
  
  // create user paddle
  const user = {
  x : 0,
  y : cvs.height/2 - 100/2,
  width : 10,
  color: "white",
  score : 0
  }
  
  // create the ball
  const ball = {
  X : cvs.width/2,
  y : cvs.height/2,
  radius : 10,
  velocityX : 5,
  velocityY : 5,
  color : "white"
  }
  
  // create com paddle
  const com = {
  x : cvs.width - 10,
  y : cvs.height/2 - 100/2,
  width : 10,
  color: "white",
  score : 0
  }
  
  // draw rect function
  
  function drawRect(x, y, w, h, color ){
  cxt.fillStyle = color;
  cxt.fillRect(x,y,w,h,);
  }
  
  
  // create the net
  const net = {
  x : cvs.width -1,
  y : 0,
  width : 2,
  height : 10,
  color : "white"
  }
  
  // draw the net
  function drawNet(){
  for(let i = 0; i <= cvs.height; i+=15){
  drawRect(net.x, net.y + i, net.width, net.height, net.color);
  }
  }
  
  
  // draw circle function
  
  function drawCircle(x,y,r,color){
  cxt.fillStyle = color
  cxt.beginPath();
  cxt.arc(x,y,r,Math.PI*2, false);
  cxt.closePath();
  cxt.fill();
  }
  
  
  // draw Text
  function drawText(text,x,y,color){
  cxt.fillStyle = color;
  cxt.font = "45px fantasy";
  cxt.fillText(text,x,y);
  }
  
 // render the game
  
  function render(){
  // clear the canvas
  drawRect(0,0, cvs.width, cvs.height, "black");
  
  // draw the net
  drawNet();
  
  // draw score
  drawText(user.score,cvs.width/4,cvs.height/5,"white");
  drawText(com.score,3*cvs.width/4,cvs.height/5,"white");
  
  // draw the user and com paddle
  drawRect(user.x, user.y, user.width, user.height, user.color);
  drawRect(com.x, com.y, com.width, com.height,com.color);
  
  //draw the circle
  drawCircle(ball.x, ball.y, ball.radius, ball.color);
  }
  
  
  //game int
  function game(){
  render();
  }
  
  //loop
  const framePerSeccond = 50;
  setInterval(game,1000/framePerSeccond);
  </script>
</body>
</html>
