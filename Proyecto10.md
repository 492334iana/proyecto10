# PROC10var life = 0;
var car1, car2, car3,car4;
var boundary1, boundary2;
var sam;

  boundary1 = createSprite(190,120,420,3);
  boundary2 = createSprite(190,260,420,3);
  
  sam = createSprite(20,190,3,3);
  sam.shapeColor = "green";
  
  car1 = createSprite(100,130,10,10);
  car1.shapeColor = "red";
  car2 = createSprite(215,130,10,10);
  car2.shapeColor = "red";
  car3 = createSprite(165,250,10,10);
  car3.shapeColor = "red";
  car4 = createSprite(270,250,10,10);
  car4.shapeColor = "red";
  
 sam.setAnimation("sam");
sam.scale=0.15
car1.setAnimation("car1");
car1.scale=0.05
car2.setAnimation("car2");
car2.scale=0.05
car3.setAnimation("car3");
car3.scale=0.05
car4.setAnimation("car4");
car4.scale=0.05
 //Agrega velocidad para hacer que el auto se mueva.

 car1.velocityY =2;
  car2.velocityY =8;
  car3.velocityY =-7;
  car4.velocityY =-7;
 
function draw() {
   background("white");
  text("kill: " + life,200,100);
  strokeWeight(0);
  fill("lightblue");
  rect(0,120,52,140);
  fill("yellow");
  rect(345,120,52,140);
  
  if(sam.isTouching(car1) || sam.isTouching(car2)){
 playSound("app_button_5.mp3");
    }
 if(boundary1.isTouching(car3)|| boundary2.isTouching(car4)){
  playSound("app_button_5.mp3");
  }
  
  
  
  // Crea la función bounceoff para hacer que el auto rebote en los límites.
//Agregar la condición para hacer que Sam se mueva de izquiera a derecha.
//Agregar la condición de reducir la vida de Sam si toca el carro.
  
    car1.bounceOff(boundary1);
  car1.bounceOff(boundary2);
  car2.bounceOff(boundary1);
  car2.bounceOff(boundary2);
  car3.bounceOff(boundary1);
  car3.bounceOff(boundary2);
  car4.bounceOff(boundary1);
  car4.bounceOff(boundary2);
  
  if(keyDown(UP_ARROW)){
  sam.y=sam.y-3
}

if(keyDown(DOWN_ARROW)){
  sam.y=sam.y+3
}

if(keyDown(LEFT_ARROW)){
  sam.x=sam.x-3
}

if(keyDown(RIGHT_ARROW)){
  sam.x=sam.x+3
}
  if(
     sam.isTouching(car1)||
     sam.isTouching(car2)||
     sam.isTouching(car3)||
     sam.isTouching(car4))
  
  {
     sam.x = 20;
     sam.y = 190;
     life = life + 1;
  }
  
  

 drawSprites();
}
