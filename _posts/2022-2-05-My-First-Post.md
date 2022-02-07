---
layout: post
title:  "2 servo 4 legged walking robot"
date:   2022-02-05 22:20:09 -0500
categories: Projects
image: /assets/robot1.png
---
![Image of the robot]({{ page.image }})

Link to video: [YouTube](https://youtu.be/Es3T07xIOaM
## What is it?

  I built this robot in September 2019, the idea was to build a very simple robot used as a prop for my highschool engineering club trailer. I did some searching and found out using only two servos and making the legs tilted so that the legs can act as pivots can make a robot move in all 3 directions except backing up. 

  Coming up with a method for the robot to turn was the most challenging part and the final solution was to adjust the timing and angle of the servo's movements. After designing the frame of the robot in Fusion 360 and printed it out and
  connecting all the electronics(consists of an Arduino UNO, a Bluetooth receiver and two servos).
  
  I programmed the robot in Arduino IDE and used an Android APP to send commands through Bluetooth.

  These are some of the codes to make it work

  ```
#include <Servo.h> Servo frontservo,backservo; //Built in servo library
char forward[] = {80,110,110,110,110,80,80,80};
char left[] = {60,100,100,60,60,80,80,80};     //different angles for turning char right[] = {120,100,100,120,120,80,80,80}; char t; 

void setup() 
{ 
  frontservo.attach(9); 
  backservo.attach(10);
  Serial.begin(9600);
}
void loop() 
{ 
  if(Serial.available())
{   
  t = Serial.read();   Serial.println(t);
}
if(t == 'F') 
{           //check for bluetooth inputs move forward   
  for(int n=0;n<4;n++)
  {
   frontservo.write(forward[2*n]);   
   backservo.write(forward[(2*n)+1]);   
   delay(40);
  }
}
else if(t == 'B') 
{      //reverse 
  for(int n=0;n<4;n++)
  {   
    frontservo.write(180-forward[2*n]);  
    backservo.write(180-forward[(2*n)+1]);   
    delay(60);
  }
}  
else if(t == 'L')
{      //turn right   
  for(int n=0;n<4;n++) 
    {   
      frontservo.write(left[2*n]);   
      backservo.write(left[(2*n)+1]);   
      delay(100);
    }
}   
  else if(t == 'R')
{      //turn left 
  for(int n=0;n<4;n++) 
  {
    frontservo.write(right[2*n]);   
    backservo.write(right[(2*n)+1]);   
    delay(100);
  }
}
else if(t == 'S') 
{      //stop   f
  rontservo.write(90);   
  backservo.write(90);
} 
  delay(100);
}
```