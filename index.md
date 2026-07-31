# Gesture Controlled Robot
Replace this text with a brief description (2-3 sentences) of your project. This description should draw the reader in and make them interested in what you've built. You can include what the biggest challenges, takeaways, and triumphs from completing the project were. As you complete your portfolio, remember your audience is less familiar than you are with all that your project entails!

My project, the Gesture Controlled Robot, is a robot car that can be moved simply by waving one's hand while wearing a custom-made component. Through constant coding and debugging, shifting the wiring of different components, and even changing the overall design multiple times, I was able to combine a motion sensing chip that detects the amount of tilt through sensing its acceleration when it rotates with 4-wheeled robot by sending information from one computer to another using Bluetooth. This endeavor was filled with frustration from challenges ranging from the robot moving incorrectly to the short circuit of several components but also triumph as I eventually arrived a working product and even went beyond with additional features for varying speed and anti-obstacle collision.

You should comment out all portions of your portfolio that you have not completed yet, as well as any instructions:
```HTML 
<!--- This is an HTML comment in Markdown -->
<!--- Anything between these symbols will not render on the published site -->
```

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Xiaohan Z | Dougherty Valley High School | Mechanical Engineering | Incoming Junior

**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](logo.svg)
  
# Final Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE

Following my prior milestone, I was able to finalize the project through ensuring all my initial plans were implemented. I was able find a suitable glove for my Xiao chip to rest flat in neutral position so natural tilt from a rough surface wouldn't cause unintentional movement in the robot. In addition I was able to implement two modifications that I brainstormed at the beginning during my build plan: a feature that allows the speed to be adjusted depending on level of tilt as well as an ultrasonic sensor to detect obstacle and stop the robot should the human directions fail to avoid collisions. For my first modification, I was able to achieve customizable speed by adding three different levels of speed (slow, normal, and fast) via adding additional thresholds that I determined through testing. I have only added adjustable speed for forward and backward directions because I found that slow turns tend to be incredibly inefficient as it overwhelms to robot when it receives orders faster than it can carry them out. Each speed level is sent as a different information through Bluetooth to the Arduino ESP 32, which is coded so that when it receives an order to act in a certain direction at a certain speed to call the function of that direction at a speed I have already defined earlier in the code. My second modification was an ultrasonic sensor to will override manual control should it cause the robot to crash (inspired by advanced cars such as ones from Tesla or Waymo). The Sensor was set at the front middle part of the car to ensure that it is in the most optimal position to detect things in front of it. How it works is that it sends out a soundwaves at a frequency inaudible to humans every 50 millisecond, once it bounces off an object it returns to the receiver of the sensor. The distance between the sensor and the object is calculated by multiplying the time between the soundwave being sent and received with the speed of sound (about 343 m/s, depending on surrounding factors) and divided by 2 (because we only want the distance between the two not the total distance traveled by the soundwave), and I have coded the Arduino to stop the motors should the distance be within 7cm. Some of my biggest challenges here at BSE involved learning topics I have had basically no prior knowledge about such as how electric circuits work as well as coding in the new world of Arduino IDE. I had many setbacks because of this dearth in experience (as well as lack of care sometimes), having to disassemble the robot due to incorrect wiring from bad soldering and replacing components like my previous Bluetooth modules due to accidental short circuiting. Despite those problems, I kept on progressing even when I was encountering trouble constantly. When I was connecting my glove component and robot didn't work together through Bluetooth, I changed different factors like running a test code to only turn the motors to check if it s a code problem, changed the wiring to see if is a physical problem with the setup. Eventually I was able to overcome this and many other problems using a similar strategy of changing factors to isolate the root cause of the problem. I learned many topics through my time here at Bluestamp Engineering ranging from technical skills like how electricity needs to flow into a component and back out through GND for it to be powered and melting solder to attach wiring to an efficient way to approach problems and to persevere when faced with challenges. In the future I hope to learn more about how other components can be used for different projects that I would like to take on, such as the robotic arm that I hope mount on top for more uses.





# Second Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/iUUz3c4Hcvg?si=-KV3AcNENHIhCIRa" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

For your second milestone, explain what you've worked on since your previous milestone. You can highlight:
- Technical details of what you've accomplished and how they contribute to the final goal
- What has been surprising about the project so far
- Previous challenges you faced that you overcame
- What needs to be completed before your final milestone

Since my previous milestone, I have shifted my focus mainly on the glove component of my project. This involved an abundance of wiring the Arduino Nano to the the IMU mpu6050, which is a sensor that can detect and track acceleration (accelerometer), angular velocity (gyroscope), and even temperature). This sensor plays a key role in the project because it will track the rotation of my glove component by tracking the acceleration using the accelerometer. When the IMU is flat, it only feels the gravity of the earth (which is 9.8 m/s^2) and it sets that as a "base value" of 1 (The acceleration in the z-axis is 0 here). When the glove and IMU is tilted, the acceleration it feels changes. Using this, the IMU creates vectors in different axes and is then able to calculate the degree/extent of rotation using the inverse tangent function. Subsequently, I have edited the code so that it only identifies a certain direction is initialized once the change in the axis goes over a certain, reasonable amount so as to not make the the robot too sensitive when connected. After that I decided to setup the HC-05 Bluetooth Module, but I was unable to establish connections between the modules because (as I later found out after debugging the problem by changing setup to see the source of the problem) one of the modules was short circuited. While I was waiting for a new module to arrive, I was instead able to find another component that worked better than my original setup: a XIAO-NRF52840 Seeed Studio chip. Essentially it has an Arduino, IMU, and a Bluetooth built in, making the overall setup for my glove extremely simple. I also switched the Bluetooth module and Arduino Uno on my robot for an Arduino Nano ESP32 (has built in Bluetooth) for similar reasons. I thought this switch in setup would change the code I have already written for both Arduinos, but I was surprised to find that the general code for the robot (AKA the 4 functions for each direction and their calling) is essentially similar. I was even more surprised by how complicated the Bluetooth setup between the XIAO and the Arduino Nano ESP32 is as it required commands that took up a significant portion of the overall code. This was where I overcame the problem of the Bluetooth connection I faced before and the reason why I wasn't able to include the setup of the receiver Bluetooth module in my milestone 1. Before my final milestone, I still need to actually find something resembling a glove or can allow the Xiao to rest on top of my hand as well as tape everything down so it doesn't move during travel. In addition I would like to implement some modifications which include making the speed at which the robot goes at vary depending on the level of tilt, as well as add an ultrasonic sensor so that the robot doesn't crash into objects in front of it.

# First Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/KC9W6fl12bc?si=12MsDaF2m3Opu-4w" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

For your first milestone, describe what your project is and how you plan to build it. You can include:
- An explanation about the different components of your project and how they will all integrate together
- Technical progress you've made so far
- Challenges you're facing and solving in your future milestones
- What your plan is to complete your project

My project is a gesture controlled robot, which is where a glove on one hand will be able to control a robot car using sensors that detect certain motions and sent accordingly to the robot via Bluetooth. My plan to build this project is to first split into 3 different parts: the robot, the glove, and the last part will be any assembly of the parts together or final code. First, the robot is a car with 4 motors to turn the wheels accordingly and the amount of power that cause the car to change directions will be determined by a motordriver that they are wired to. The motordriver determines the amount of power (which comes from an installed battery pack) goes to which motor. This information about direction and power output comes from an Arduino UNO, a computer that acts as the decision processor that has code that will be able to determine 4 different directions (forward, backward, left, and right). The information of which direction the Arduino UNO should make the robot actually turn comes from a Bluetooth module that receives information from another one on the glove. Since this robot is controlled through the motion of my hand, a sensor on the glove detects an intended motion on my hand and is then processed by the code on an Arduino Nano that sends the information to the robot. So far I have been able to build the robot by soldering the wiring between the motors and the motordriver and connecting it to an Arduino. I was also able to write basic code that allows the robot to move in the four directions, meaning the robot is able to function and move. I have faced several challenges with most of them summing up to the wheels turning in ways that I don't intend it to. This showed in the forms of either soldering wires on the motors incorrectly, connecting the wires incorrectly to the motordriver, and even my code with wrong instructions for each direction. Challenges I am facing and solving in future milestones include actually writing the code to connect the glove component to the robot component via Bluetooth as I have had almost negligible experience coding with python and C++ and none at all in Arduino IDE, requiring me to learn how this new coding environment works. My plan to complete the project is to next work on the glove, installing an Arduino Nano, Inertial measurement unit, and Bluetooth module to send information and connecting it all together. I also plan to code the glove to recognize motion for intended direction of the robot and send it as such. Later I plan to connect the 2 code and add finishing touches as well as modifications to complete my project.

# Schematics 
<img width="350" height="350" alt="circuit_image" src="https://github.com/user-attachments/assets/40bcaca4-e4ac-48b0-bb8d-ac8ec36b9f38" />

# Code
Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. 

```c++
#include <ArduinoBLE.h>
#include <Wire.h>
#include <LSM6DS3.h>


// ---------------- IMU ----------------

LSM6DS3 myIMU(I2C_MODE, 0x6A);


// ---------------- BLE ----------------

BLEService robotService("19B10000-E8F2-537E-4F6C-D104768A1214");

BLECharacteristic commandCharacteristic(
  "19B10001-E8F2-537E-4F6C-D104768A1214",
  BLERead | BLENotify,
  1
);


// ---------------- Settings ----------------

// Forward / backward speed levels
const float level1Threshold = 0.50;   // Slow
const float level2Threshold = 0.75;   // Medium
const float level3Threshold = 1.00;   // Fast

// Turning threshold (higher because turns are full speed)
const float turnThreshold = 0.65;


// Last command sent

char lastCommand = 'S';


// ---------------- Error blink ----------------

void errorBlink(int blinkDelay) {

  while (1) {

    digitalWrite(LED_BUILTIN, !digitalRead(LED_BUILTIN));

    delay(blinkDelay);

  }

}

// ---------------- Speed level helper ----------------

char getSpeedLevel(float magnitude) {

  if (magnitude >= level3Threshold) return '3';
  if (magnitude >= level2Threshold) return '2';
  if (magnitude >= level1Threshold) return '1';

  return 0;

}


// ---------------- Send BLE Command ----------------

void sendCommand(char command) {


  if(command == lastCommand)
    return;


  lastCommand = command;


  commandCharacteristic.writeValue(
    (const uint8_t*)&command,
    1
  );


  if(Serial) {

    Serial.print("Sent: ");
    Serial.println(command);

  }

}



// ---------------- Setup ----------------

void setup() {


  pinMode(LED_BUILTIN, OUTPUT);


  Serial.begin(115200);


  // Start IMU

  if(myIMU.begin() != 0) {


    if(Serial)
      Serial.println("IMU failed!");


    errorBlink(150);

  }


  if(Serial)
    Serial.println("LSM6DS3 Ready");



  // Start BLE

  if(!BLE.begin()) {


    if(Serial)
      Serial.println("BLE failed!");


    errorBlink(500);

  }



  BLE.setLocalName("XIAO_Robot_Controller");

  BLE.setAdvertisedService(robotService);



  robotService.addCharacteristic(
    commandCharacteristic
  );


  BLE.addService(robotService);



  commandCharacteristic.writeValue(
    (const uint8_t*)"S",
    1
  );



  BLE.advertise();



  if(Serial)
    Serial.println("BLE Advertising");


}



// ---------------- Loop ----------------

void loop() {


  BLE.poll();



  float x = myIMU.readFloatAccelX();

  float y = myIMU.readFloatAccelY();



  char command = 'S';



  // -------- Forward / Backward --------

  // -------- Forward / Backward (3 speeds) --------

if (x < 0) {

  char level = getSpeedLevel(-x);

  if (level != 0)
    command = level;          // '1','2','3'

}
else if (x > 0) {

  char level = getSpeedLevel(x);

  if (level != 0)
    command = 'a' + (level - '1');   // 'a','b','c'

}

// -------- Left / Right (single speed) --------


  //Serial.println(y);
  if (y < -turnThreshold) {
    command = 'L';
  
  }
  else if (y > turnThreshold) {
    command = 'R';
  }


  sendCommand(command);



  delay(50);

}
```

```c++
#include <BLEDevice.h>
#include <BLEUtils.h>
#include <BLEClient.h>


#define SERVICE_UUID        "19B10000-E8F2-537E-4F6C-D104768A1214"
#define CHARACTERISTIC_UUID "19B10001-E8F2-537E-4F6C-D104768A1214"


// -------- L298N MOTOR PINS --------

int IN1 = 9;
int IN2 = 8;
int IN3 = 7;
int IN4 = 6;

int ENA = 12;
int ENB = 10;


// -------- SPEED SETTINGS --------

const int FAST_SPEED = 255; // used for turns now, and as level 5

// 5 forward/backward speed levels — index 0 = gentlest tilt, index 4 = strongest
const int SPEED_LEVELS[3] = {80, 160, 255};


// -------- ULTRASONIC (HC-SR04) --------
// Echo is 5V logic — run it through a voltage divider before this pin!

const int TRIG_PIN = 2;
const int ECHO_PIN = 3;

const int OBSTACLE_DISTANCE_CM = 7; // stop threshold — small buffer, tune as needed
const unsigned long OBSTACLE_CHECK_INTERVAL = 50; // ms between re-checks while driving forward

unsigned long lastObstacleCheck = 0;


// -------- BLE VARIABLES --------

BLEClient* client = nullptr;
BLERemoteCharacteristic* characteristic;

bool connected = false;

char lastCommand = 'S';


// -------- CLIENT CONNECTION CALLBACKS --------

class MyClientCallback : public BLEClientCallbacks {

  void onConnect(BLEClient* pclient) {
  }

  void onDisconnect(BLEClient* pclient) {
    connected = false;
    Serial.println("Disconnected from XIAO - will rescan");
  }

};


// -------- ULTRASONIC FUNCTIONS --------

long getDistanceCm() {

  digitalWrite(TRIG_PIN, LOW);
  delayMicroseconds(2);
  digitalWrite(TRIG_PIN, HIGH);
  delayMicroseconds(10);
  digitalWrite(TRIG_PIN, LOW);

  long duration = pulseIn(ECHO_PIN, HIGH, 30000); // 30ms timeout

  if (duration == 0) return 999; // no echo = nothing in range, treat as clear

  return duration * 0.0343 / 2;

}


// -------- MOTOR FUNCTIONS --------

void forward(int speed) {
  analogWrite(ENA, speed);
  analogWrite(ENB, speed);
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, HIGH);
}

void backward(int speed) {
  analogWrite(ENA, speed);
  analogWrite(ENB, speed);
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, HIGH);
  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);
}

// Turns — full pivot, both wheels equal and opposite, always full speed
void left(int speed) {
  analogWrite(ENA, speed);
  analogWrite(ENB, speed);
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, HIGH);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, HIGH);
}

void right(int speed) {
  analogWrite(ENA, speed);
  analogWrite(ENB, speed);
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);
}

void stopMotors() {
  analogWrite(ENA, 0);
  analogWrite(ENB, 0);
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, LOW);
}


// -------- CENTRAL MOTOR DISPATCH (obstacle-aware) --------

void updateMotors() {

  // Forward — 5 speed levels ('1'-'5'), obstacle-checked
  if (lastCommand >= '1' && lastCommand <= '3') {

    int speed = SPEED_LEVELS[lastCommand - '1'];

    if (getDistanceCm() <= OBSTACLE_DISTANCE_CM) {
      stopMotors();
    } else {
      forward(speed);
    }

    return;

  }

  // Backward — 5 speed levels ('a'-'e'), never blocked by the front sensor
  if (lastCommand >= 'a' && lastCommand <= 'c') {

    int speed = SPEED_LEVELS[lastCommand - 'a'];
    backward(speed);
    return;

  }

  switch (lastCommand) {

    case 'L':
      left(FAST_SPEED);
      break;

    case 'R':
      right(FAST_SPEED);
      break;

    case 'S':
      stopMotors();
      break;

  }

}


// -------- BLE RECEIVE --------

void notifyCallback(
  BLERemoteCharacteristic* characteristic,
  uint8_t* data,
  size_t length,
  bool isNotify
) {

  if (length > 0) {

    char command = (char)data[0];

    if (command != lastCommand) {

      lastCommand = command;

      Serial.print("Command received: ");
      Serial.println(command);

      updateMotors();

    }

  }

}


// -------- SETUP --------

void setup() {

  Serial.begin(115200);

  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(IN3, OUTPUT);
  pinMode(IN4, OUTPUT);

  pinMode(ENA, OUTPUT);
  pinMode(ENB, OUTPUT);

  pinMode(TRIG_PIN, OUTPUT);
  pinMode(ECHO_PIN, INPUT);

  stopMotors();

  Serial.println("Starting BLE");

  BLEDevice::init("Nano Robot");

}


// -------- LOOP --------

void loop() {

  if (!connected) {

    Serial.println("Scanning...");

    BLEScan* scan = BLEDevice::getScan();
    scan->setActiveScan(true);

    BLEScanResults results = scan->start(5);

    for (int i = 0; i < results.getCount(); i++) {

      BLEAdvertisedDevice device = results.getDevice(i);

      if (device.haveServiceUUID() &&
          device.isAdvertisingService(BLEUUID(SERVICE_UUID))) {

        Serial.println("Found XIAO");

        if (client == nullptr) {
          client = BLEDevice::createClient();
          client->setClientCallbacks(new MyClientCallback());
        }

        if (client->connect(&device)) {

          Serial.println("Connected to XIAO");

          BLERemoteService* service = client->getService(BLEUUID(SERVICE_UUID));
          characteristic = service->getCharacteristic(BLEUUID(CHARACTERISTIC_UUID));

          if (characteristic->canNotify()) {
            characteristic->registerForNotify(notifyCallback);
            Serial.println("Notifications enabled");
          }

          connected = true;

        }

      }

    }

    delay(1000);

  } else {

    unsigned long now = millis();

    if (now - lastObstacleCheck >= OBSTACLE_CHECK_INTERVAL) {
      lastObstacleCheck = now;

      if (lastCommand >= '1' && lastCommand <= '3') {
        updateMotors();
      }
    }

    delay(10);

  }

}
```




# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Arduino Nano ESP32-S3| The main computer component of the robot that receives information and  | $19.3 | <a href="https://www.amazon.com/Arduino-ABX00083-Bluetooth-MicroPython-Compatible/dp/B0C947BHK5/"> Link </a> |
| XIAO nRF52840 | To detect correct motion on the glove and send direction information to the robot | $16.99 | <a href="https://www.amazon.com/Seeed-Studio-XIAO-nRF52840-Microcontroller/dp/B09T9VVQG7/"> Link </a> |
| L298n Motor Drive controller | Able to control current so to move the motors | $6.99 | <a href="https://www.amazon.com/Qunqi-Controller-Module-Stepper-Arduino/dp/B014KMHSW6/"> Link </a> |
| Ultrasonic Sensor HC - SRO4 | Sends out soundwaves to detect obstacles in it's way | $5.25 | <a href="https://www.amazon.com/HC-SR04-Ranging-Detector-Ultrasonic-Distance/dp/B01GNEHJNC/"> Link </a> |
|4WD Robot Car Chassis Kit  | Includes a base plate as well as the motors and wheels used for the basis of the project | $20.99 | <a href="https://www.amazon.com/4WD-Robot-Chassis-Robotics-Raspberry/dp/B0G5N8P9YF/"> Link </a> |
| Sparthos Glove | The base for the glove component so that the chip has a place to rest | $9.99 | <a href="https://www.amazon.com/Sparthos-Wrist-Support-Sleeves-Pair/dp/B074CXHF4T/"> Link </a> |
| Miady 2-Pack Portable Charger | Powers the glove component | $17.99 | <a href="https://www.amazon.com/Miady-Portable-Charger-10000mAh-Battery/dp/B0GQH1QHDH/"> Link </a> |
| AA 9V battery holder | Holds batteries on the robot, only 1 is needed| $7.99 | <a href="https://www.amazon.com/LAMPVPATH-Pack-Battery-Holder-Leads/dp/B07KVJ9FPN/"> Link </a> |
| AA 9V batteries | Powers the robot, 6 are needed| $6.49 | <a href="https://www.amazon.com/AmazonBasics-Performance-Alkaline-Batteries-8-Pack/dp/B00O869KJE/"> Link </a> |


# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
