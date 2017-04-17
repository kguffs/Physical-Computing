This is the documentation for my first draft, which I submitted as my midterm. At that point, the project could only recognize range and would turn on all LEDs if the high range was activated. This is the code for that stage:

#define ledred 11
#define ledyellow 12
#define ledgreen 13

void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  pinMode(ledred, OUTPUT);
  pinMode(ledyellow, OUTPUT);
  pinMode(ledgreen, OUTPUT);

}

void loop() {
  // put your main code here, to run repeatedly:
  int pitchRead = analogRead(A0);
  Serial.print("pitchRead: ");
  Serial.println(pitchRead);

  
  if (pitchRead < 275) {
    digitalWrite(ledred, LOW);
    digitalWrite(ledyellow, LOW);
    digitalWrite(ledgreen, LOW);
  

  if (pitchRead > 255 && pitchRead < 325) {
    digitalWrite(ledred, HIGH);
    digitalWrite(ledyellow, LOW);
    digitalWrite(ledgreen, LOW);
    
   
  }

  if (pitchRead > 325 && pitchRead < 375) {
    digitalWrite(ledred, LOW);
    digitalWrite(ledyellow, HIGH);
    digitalWrite(ledgreen, LOW);

  }

  if (pitchRead > 375) {
    digitalWrite(ledred, LOW);
    digitalWrite(ledyellow, LOW);
    digitalWrite(ledgreen, HIGH);
  }
}
