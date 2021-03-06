I made a pitch detection device that sorts pitches by range. I'm a trombone player and I want to eventually track my tendencies by partial (a partial is an overtone, the trombone follows the overtone series so ranges of pitches fall into a "partial" which for a player generally translates to the tightness of the lips).
I used a previous potRead code and substituted the pot with the ACG mic amp and renamed it pitchRead. I added an LED and at this point adjusted the frequency ranges to the room so that everything would be off until I sing or play. At the moment, all the lights come on when a high range note is played, low is on with mid, the only stand alone light is the low range. I'd like to eliminate engaging lower ranges if I'm in the high range and I'd like to assign specific pitches to each LED.

MIDTERM CODE:

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
  }

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

I had two issues to troubleshoot - because of my ranges, the low range wouldn't engage and the mid range (yellow) LED would not turn off. I fixed that by expanded and redefining my pitch ranges. My other issue was then that I'd sing in any range and no matter which light came on, the low range (red) would stay on and never turn off. I implemented an off switch in the code in the same format as the other "if" statements.

One of the things I liked about my second problem was that when a pitch was certainly mid-range, as long as it was held, no other lights would come on. It seems when I extended my ranges I also gave my project a more fluid response.
