30.01.2026

17:03

It was quite a log and, tiring as well, so I am out of power but learning is still fun anyways. Today I'll be learning each component byofficial Elegoo manual I've got from their website. Also I suppose that yesterdays issue with RC522 module was due to me using library from online source and not one beight provided in the manual. It's gonna be sad if it's true but let's test it out anyways.

17:16

A result was achieved!
After removing GitHub library and installing one from documentation, even though getting same serial firmware = 0x18 (unknown) error, the RC522 eventually managed to read a card!!!
<img src="CardDataProof.png" width="70%">
After that I've rebooted Uno to try once more, but unfortunately module didn't respond anymore. Well at least I know that RC522 is not malfunctional, it's either that module is poorly developed and has some issues with code or... The code is just terrible :|. Gotta research further.

18:02

One hour later, big amout of ChatGPT prompts and I managed to make this thing work. The reading cycle breaks easily if you hold card down for too long or do any other fast actions, but if to put card/tag steadily and retract it and wait before putting again, Arduino effectively manages to read data without breaking!!!

<details close>
  <summary>Click here to view full code</summary>

```C++
#include <SPI.h>
#include <MFRC522.h>

#define RST_PIN         9
#define SS_PIN          10

MFRC522 mfrc522(SS_PIN, RST_PIN);

void setup() {
  Serial.begin(9600);

  pinMode(RST_PIN, OUTPUT);
  digitalWrite(RST_PIN, HIGH);

  SPI.begin();
  mfrc522.PCD_Init();

  mfrc522.PCD_DumpVersionToSerial();
  Serial.println(F("Scan PICC to see UID..."));
}


void loop() {
  if (!mfrc522.PICC_IsNewCardPresent()) {
    return;
  }

  if (!mfrc522.PICC_ReadCardSerial()) {
    return;
  }

  Serial.print("UID:");
  for (byte i = 0; i < mfrc522.uid.size; i++) {
    Serial.print(" ");
    Serial.print(mfrc522.uid.uidByte[i], HEX);
  }
  Serial.println();

  mfrc522.PICC_HaltA();
  mfrc522.PCD_StopCrypto1();

  delay(500);
}
```

</details>
<br>
I don't really understand what most of the code does so... lol, I'll start with going through Elegoo manual as they intended I guess. But that's a task for tomorrow. I feel completely drained now.

