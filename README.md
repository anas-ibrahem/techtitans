# Techtitans 💻🕹
Let Us introduce the Tech Titans Projects 💙🤖

*Both Projects Are Based on Arduino Uno

First We Have The Smart Parking Garage 🅿️ :

Components we used: 2 LCDs with i2c, buzzer, Flame sensor,6 IR sensors, Servo motor, Push button, LEDs, LDR Sensor,
Description :
.One LCD display is mounted facing the exterior of the garage, providing information to vehicles entering the garage.

.The other LCD display is positioned inside the garage, conveying information to the user within the garage.

.Two IR sensors are  placed at the garage entrance and exit, one before and one after the gate, to accurately determine the direction of vehicles. These sensors facilitate gate control, allowing the system to differentiate between incoming and outgoing vehicles.

.A servo motor is responsible for controlling the garage gate. It opens and closes in response to vehicle entry and exit.

.Four IR sensors are strategically placed within the garage parking slots to determine the availability of parking spaces. These sensors communicate with the LCD facing the car entering the garage.

.A buzzer is integrated into the system to provide audible alerts and warnings, such as fire detection or security breaches.

.The flame sensor continuously monitors for the presence of fires within the garage. If a fire is detected, it triggers an alarm displays a warning message on the interior LCD, And Keeps The gate Open.

.An emergency button is included in the system. If pressed, it signals a security threat (thief) and activates the buzzer and gate closure.

.LED lights are installed within the garage for illumination and an LDR continuously monitors ambient light conditions, If it is dark, the LDR signals the LED lights to turn on, ensuring adequate lighting within the garage, and In daylight or well-lit conditions, the LDR signals the LEDs to turn off, saving energy and electricity.




Second We have Maze-Solver & Bluetooth Car AKA "AZZA" 🚗:
* The car has 3 modes (Bluetooth Controller mode - Voice control Mode - Maze solver Mode ) Which you can choose between via your smartphone.

Our car “azza”, which we made with all effort and passion using components like 4 ir sensors, H-Bridge, Bluetooth module, LCD 16x2 with i2c .

the four sensors at the front of the car act as its eyes as They're really good at spotting black lines and Their job is to help the car follow this black line correctly If the 4 sensors detect a black area on the ground, the car stops. so, these sensors work together to make sure the car can follow the line accurately, even when there's a sharp turn ahead. 

.The H-bridge motor driver manages the car's four robust DC motors independently, granting it exceptional maneuverability and control.
.Bluetooth module is seamlessly integrated, allowing users to control the car via a mobile app or by issuing voice commands, enhancing its versatility and user-friendliness.
.Equipped with an LCD display using I2C, the car presents essential information such as the time taken to follow a line or solve a maze. It also indicates the car's operational mode, providing real-time feedback on its activities and status.
.power switch When you turn it on, the car's magic starts. It makes the car's sensors, motors, and all the fancy stuff work. When you turn it off, everything stops, making sure the car doesn't do anything unexpected.
Now let us explain the mechanism of solving the maze, which is that
The car gives priority to the path from left to right, so it tries all the paths until it reaches the end, and if it encounters an open path, it turns around and returns to the path again. 


* There was a challenge which if the car encounters 3 ways at the same time (Forward, Left and Right)
  In that case, the 4 sensors Read black and it's the same situation as the ending point so we solved this by doing a trick instead of using an extra IR sensor
  We made the car takes a small left rotation when encounters 4 black readings after that if the 4 reading were still black that meant its an actual ending point so the car stops.
  if they don't then it turns left and continues solving the maze.!!!!


Hope You enjoy Reading The Code for Our projects ! ✅
* Video of Car "Azza" Enjoy Watching it https://drive.google.com/drive/folders/1-qO5skBQvclPyShT_PV0-vdkKg4PJZZT

