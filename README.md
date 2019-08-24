int numBolas = 500;
int radioI;
int r=100;
int r2=20;
Bola [] bolas = new Bola[numBolas];

void setup() {
  size(500, 700);
  background(0);
  frameRate(30);
  smooth();
  noStroke();
  //radioI= int(random(2,5));
  //b1 = new Bola(random(1,4), random(1,4), random(width-radioI),random(height-radioI), 1, 1, radioI, int(random(50, 255)));
  for (int i = 0; i < bolas.length; i++) {
    radioI= int(random(2, 8));
    //crea cada objeto
    //Bola(float velx,float vely, float xInicio, float yInicio, int dirx, int diry, int rad, int trans)
    bolas[i] = new Bola(random(1, 3), random(1, 3), random(width-radioI*2)+radioI, random(height-radioI*2)+radioI, 1, 1, radioI, int(random(50, 255)));
  }
}
void draw() {
  // b1.mover();
  //b1.dibujar();
  background(0);
  /////////////////////////////////////////////////////


  // fill(0, 30);
  // rect(0,0,width, height);
  for (int i = 0; i < bolas.length; i++) {
    bolas[i].mover();
    bolas[i].dibujar();
  }

  fill(180);
  // NAVE  1
  ellipse (265, 200, r, r); //capsula
  fill(13, 147, 23);
  ellipse(275, 275, 200, 75); //cuerpo

  fill(0);
  line(75, 275, 475, 275);
  fill(255, 255, 0);
  ellipse(130, 250, r2, r2);
  ellipse(180, 250, r2, r2);
  ellipse(230, 250, r2, r2);
  ellipse(280, 250, r2, r2);
  ellipse(330, 250, r2, r2);
  ellipse(380, 250, r2, r2);
  ellipse(425, 250, r2, r2);
  // PRIMER HAZ
  fill(154, 250, 23);
  ellipse(275, 460, 175, 70);
  fill(0);
  ellipse(275, 460, 150, 60);
  // SEGUNDO HAZ
  fill(154, 250, 23);
  ellipse(275, 620, 140, 50);
  fill(0);
  ellipse(275, 620, 115, 40);
}

class Bola {
  float velocidadX;
  float velocidadY;
  float x, y;
  int direccionX;
  int direccionY;
  int radio;
  int transparencia;
  /////////// constructor////////////////
  Bola(float velx, float vely, float xInicio, float yInicio, int dirx, int diry, int rad, int trans) {
    this.velocidadX = velx;
    this.velocidadY = vely;
    this.x = xInicio;
    this.y = yInicio;
    this.direccionX = dirx;
    this.direccionY = diry;
    this.radio = rad;
    this.transparencia = trans;
  }
  ///////////////////////////sistema de movimiento/////////////////
  void mover() {
    x += velocidadX * direccionX;
    if ((x > width-radio) || (x < radio)) {
      direccionX = -direccionX;
    }
    y += velocidadY * direccionY;
    if ((y > height-radio) || (y < radio)) {
      direccionY = -direccionY;
    }
  }
  ///////////////////////dibuja en la pantalla/////////////////
  void dibujar() {
    noStroke();
    ellipseMode(RADIUS);
    fill(255, transparencia);
    ellipse(x, y, radio, radio);
    strokeWeight(2);
    stroke(0, 100);
    point(x+radio, y+radio);
  }
}
