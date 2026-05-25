et robotX, robotY;
 let tamano = 180;
 let forma = "circulo"; // cambia: circulo, cuadrado, ovalo
 let colorCuerpo = [100, 200, 255];
 let estado = "feliz"; // Expresiones exactas que pediste
 let parpadeo = false;
 let tiempoParpadeo = 0;
 let movLado = 0;
 let movArribaAbajo = 0;
 function setup() {
   createCanvas(700, 500);
   robotX = width / 2;
   robotY = height / 2;
 }
 function draw() {
   background(20, 20, 30);
   
   // 🔄 MOVIMIENTO DEL ROBOT
   movLado = sin(frameCount * 0.03) * 30;
   movArribaAbajo = cos(frameCount * 0.04) * 15;
   
   // 👁️ LÓGICA DE PARPADEO
   tiempoParpadeo++;
   if (tiempoParpadeo > 120 && random(1) < 0.05) {
     parpadeo = true;
     tiempoParpadeo = 0;
   }
   if (parpadeo) {
     tiempoParpadeo++;
     if (tiempoParpadeo > 8) parpadeo = false;
   }
   // 🤖 DIBUJO
   push();
   translate(robotX + movLado, robotY + movArribaAbajo);
   
   dibujarCuerpo();
   dibujarOjos();
   dibujarExpresion();
   
   pop();// 🤖 ROBOT DE ESCRITORIO - EXACTO COMO LO PEDISTE 🤖
// Solo: Movimiento, parpadeo, cambia forma/color, 12 expresiones

// 🧠 VARIABLES
let robotX, robotY;
let tamano = 180;
let forma = "circulo"; // cambia: circulo, cuadrado, ovalo
let colorCuerpo = [100, 200, 255];
let estado = "feliz"; // Expresiones exactas que pediste
let parpadeo = false;
let tiempoParpadeo = 0;
let movLado = 0;
let movArribaAbajo = 0;

function setup() {
  createCanvas(700, 500);
  robotX = width / 2;
  robotY = height / 2;
}

function draw() {
  background(20, 20, 30);
  
  // 🔄 MOVIMIENTO DEL ROBOT
  movLado = sin(frameCount * ;
}

// ==========================================
// 🎨 CUERPO: CAMBIA FORMA Y COLOR
// ==========================================
function dibujarCuerpo() {
  fill(colorCuerpo);
  stroke(255);
  strokeWeight(3);
  
  // Cambia de forma automática
  if (frameCount % 180 === 0) {
    let formas = ["circulo", "cuadrado", "ovalo", "rectangulo"];
    forma = random(formas);
  }

  // DIBUJAR FORMA
  switch(forma) {
    case "circulo":
      ellipse(0, 0, tamano, tamano);
      break;
    case "cuadrado":
      rect(-tamano/2, -tamano/2, tamano, tamano);
      break;
    case "ovalo":
      ellipse(0, 0, tamano * 1.2, tamano * 0.8);
      break;
    case "rectangulo":
      rect(-tamano/2, -tamano/3, tamano, tamano * 0.7);
      break;
  }
}

// ==========================================
// 👁️ OJOS Y PARPADEO
// ==========================================
function dibujarOjos() {
  let sep = 35;
  let t1 = 20, t2 = 24;

  // Tamaño de ojos según emoción
  switch(estado) {
    case "feliz": t1=16; t2=22; break;
    case "triste": t1=22; t2=12; break;
    case "enojado": t1=12; t2=20; break;
    case "sorpendido": t1=26; t2=26; break;
    case "enamorado": t1=22; t2=22; break;
    case "cansado": t1=20; t2=10; break;
    case "riendo": t1=22; t2=10; break;
    case "dudando": t1=16; t2=20; break;
    case "asustado": t1=26; t2=26; break;
    case "orgulloso": t1=14; t2=22; break;
    case "saludando": t1=18; t2=22; break;
  }

  // DIBUJAR OJOS (PARPADEAN)
  fill(255, 255, 0);
  noStroke();
  if (!parpadeo) {
    ellipse(-sep, -10, t1, t2);
    ellipse(sep, -10, t1, t2);
    fill(0);
    ellipse(-sep, -10, t1/2, t2/2);
    ellipse(sep, -10, t1/2, t2/2);
  } else {
    // Ojos cerrados
    fill(0);
    rect(-sep-5, -10, t1+4, 4);
    rect(sep-5, -10, t1+4, 4);
  }
}

// ==========================================
// 😀 EXPRESIONES EXACTAS QUE PEDISTE
// ==========================================
function dibujarExpresion() {
  stroke(0);
  strokeWeight(4);
  noFill();

  switch(estado) {
    case "feliz":
      arc(0, 20, 50, 30, 0, PI);
      break;
    case "triste":
      arc(0, 30, 50, 30, PI, TWO_PI);
      break;
    case "enojado":
      line(-20, 20, 20, 28);
      line(-30, -20, -10, -15); // ceja
      line(30, -20, 10, -15);   // ceja
      break;
    case "sorprendido":
      ellipse(0, 20, 18, 22);
      break;
    case "enamorado":
      arc(-12, 18, 14, 14, 0, PI);
      arc(12, 18, 14, 14, 0, PI);
      break;
    case "cansado":
      arc(-10, 25, 12, 10, PI, TWO_PI);
      arc(10, 25, 12, 10, PI, TWO_PI);
      break;
    case "riendo":
      arc(0, 15, 60, 40, 0, PI);
      line(-25,15,-12,30);
      line(25,15,12,30);
      break;
    case "dudando":
      line(-15, 25, 15, 20);
      break;
    case "asustado":
      ellipse(0, 20, 16, 20);
      break;
    case "orgulloso":
      arc(0, 22, 40, 18, 0.7, PI - 0.7);
      break;
    case "saludando":
      arc(0, 20, 50, 25, 0, PI);
      strokeWeight(3);
      line(-60, -30, -40, -60); // mano saludando
      break;
  }
}

// ==========================================
// 🖱️ AL HACER CLIC: CAMBIA COLOR Y EXPRESIÓN
// ==========================================
function mousePressed() {
  // Cambiar color aleatorio
  colorCuerpo = [random(255), random(255), random(255)];
  
  // Cambiar a una de las expresiones EXACTAS que pediste
  let listaExpresiones = [
    "feliz", "triste", "enojado", "sorprendido", 
    "enamorado", "cansado", "riendo", "dudando", 
    "asustado", "orgulloso", "saludando"
  ];
  estado = random(listaExpresiones);
}
