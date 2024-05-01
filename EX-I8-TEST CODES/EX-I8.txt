// Blinks an LED attached to a MCP23XXX pin.

// ok to include only the one needed
// both included here to make things simple for example



#include <Adafruit_MCP23X08.h>
#include <Adafruit_MCP23X17.h>

#define SDA 16
#define SCL 17

#define INPUT1 0
#define INPUT2 1
#define INPUT3 2
#define INPUT4 3
#define INPUT5 4
#define INPUT6 5
#define INPUT7 6
#define INPUT8 7

#define Address 0x20  // Set Address According to DIP Switch Configuration

Adafruit_MCP23X08 mcp;


void setup() {
  Serial.begin(115200);
  Serial.println("Device Starting");

  Wire.begin (SDA, SCL);   
  if (!mcp.begin_I2C(Address)) {
    Serial.println("Error.");
    while (1);
  }

  // configure pin for output
  mcp.pinMode(INPUT1, INPUT); mcp.pinMode(INPUT2, INPUT); mcp.pinMode(INPUT3, INPUT);   mcp.pinMode(INPUT4, INPUT); mcp.pinMode(INPUT5, INPUT); mcp.pinMode(INPUT6, INPUT); mcp.pinMode(INPUT7, INPUT); mcp.pinMode(INPUT8, INPUT);
}

void loop() {
  Serial.print(mcp.digitalRead(INPUT1));Serial.print(mcp.digitalRead(INPUT2));Serial.print(mcp.digitalRead(INPUT3));Serial.println(mcp.digitalRead(INPUT4));
Serial.print(mcp.digitalRead(INPUT5));Serial.print(mcp.digitalRead(INPUT6));Serial.print(mcp.digitalRead(INPUT7));Serial.println(mcp.digitalRead(INPUT8));

  Serial.println(""); 
  delay(500);
}
