# addslider_curves_homework
import controlP5.*;

float r = 20;
float petalLen;
int resolution = 100;
float theta;
float x;
float y;
float k;
float n = 20;
float d = 20;

int index = 0;
float animationVal1;


ControlP5 cp5;

void setup() {
 size(600, 600);
 k = n / d;
  
cp5 = new ControlP5(this);


cp5.addSlider("resolution")
   .setLabel("Number of Points")
   .setPosition(20, 20)
    .setRange(20, 360*2);
    
cp5.addSlider("r")
    .setLabel("Radius")
   .setPosition(20, 32)
    .setRange(20, 300);

  cp5.addSlider("n")
    .setLabel("n Value")
    .setPosition(20, 44)
    .setRange(0, 50)
    .setNumberOfTickMarks(51);

 cp5.addSlider("d")
    .setLabel("d Value")
   .setPosition(20, 56)
   .setRange(0, 100)
    .setNumberOfTickMarks(51);
}

void draw() {
  
animationVal1 = d;
 
  background(0);
  
  pushMatrix();
  translate(width*0.5, height*0.5);
  noFill();
  stroke(255);

  beginShape();
  for (int i = 0; i < resolution; i++) {

    theta = map(i*ceil(animationVal1), 0, resolution, 0, TWO_PI);
   
    petalLen = sin(n*theta);

   x = r * petalLen * sin(theta);
   y = r * petalLen * cos(theta);
 point(x,y);
 vertex(x, y);
}
  endShape(CLOSE);
  popMatrix();

}
