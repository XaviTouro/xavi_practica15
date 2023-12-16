# xavi_practica15
/*************************************************************************************************************************
* Reaproveita partes da montaxe das prácticas anteriores para realizar esta. 
* Vas reproducir a penúltima práctica das 'portas lóxicas' para realizar a programación
* por software en lugar de hardware. Para iso vas simular a saída (1 ou 0) pola activación 
* ou desactivación dun LED, as entradas A, B e C van ser simuladas por pulsadores que forcen
* un 0 cando non están activos e un 1 cando se premen (configuración PULL_DOWN). 
* As entradas irán aos pins dixitais 10, 9 e 8 respectivamente.

* Recorda que a función lóxica que vas simular é: Cando se dean as condicións correspondentes, 
* débese acender o LED de saída. Ponlle uns 3 ou 4 s de tempo, para que se vexa que está aceso. 
* Cando NON se dan esas condicións, o LED debe apagar, pero só cando NON se dean as condicións.

* Para realizar esta práctica terás que empregar o bloque 'IF-ELSE' (SI-ENTÓN condicional) 
* e engadir unha condición relativa aos pins 10, 9 e 8, correspondentes ás entradas A, B e C respectivamente.

* Recomendacións: (a) prepara en primeiro lugar a parte do código que vai estar no bloque do IF e comproba que funciona, 
* (b) prepara en segundo lugar a parte do código que vai estar no bloque do ELSE e comproba que funciona
* (p.ex. cunha condición simple cun só pulsador), (c) elabora as condicións por separado paraparae para, 
* podes comprobar cada unha das condicións por separado, (d) finalmente integra todas as condicións parciais nunha global
* de () OR () OR () [no texto debería aparecer como if(() || (() || ()))].

* AUTOR: Xavi Figueiro

* DATA: 16/12/2023

**************************************************************************************************************************/




// Identificar entradas e saídas.
// Declarar entradas e saídas
// Declarar variables globais ou sentenzas do preprocesador.
// Intentar descompoñer o problema en tarefas máis simples.
//  Secuenciar ou ordear as tarefas.

#define pinA 10  // Entrada A
#define pinB 9   // Entrada B
#define pinC 8   // Entrada C
#define pinS 11  // Saída a Relay 


int tempo = 4000;         // tempo espera aceso ou apagado.
bool condicion = -1;      // condición para o acendido  ou apagado bombeo.

bool a, b, c = -1;        // variables que gardan o valor de cada interruptor.

void setup(){
  pinMode(pinA, INPUT);
  pinMode(pinB, INPUT);
  pinMode(pinC, INPUT);
  pinMode(pinS, OUTPUT);
  //serial.begin(9600);
  
 }

void loop(){
  a = digitalRead(pinA);
  b = digitalRead(pinB);
  c = digitalRead(pinC);
  
  condicion = ( !a && b && !c); // || (a && b && !c) || (a && b && c);
  //serial.printín(condicion);
  
  if(condicion){
    digitalWrite(pinS, HIGH);
    delay(tempo);
  }
  else{
    digitalWrite(pinS, LOW);
    delay(tempo);
  }
}
