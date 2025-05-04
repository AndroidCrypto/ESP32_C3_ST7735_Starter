# ESP32 C3 Supermini with ST7735 TFT display Starter
Getting started with an **ESP32-C3 Supermini** device and a TFT display **ST7735**.

This is the accompanying repository for my article "**Getting Started with an ESP32-C3 Supermini device connected to an ST7735 TFT display**: https://medium.com/@androidcrypto/getting-started-with-an-esp32-c3-supermini-device-connected-to-an-st7735-tft-display-6ba1a1027a88

My display is a 1.8 inch large TFT display with 128 x 160 pixels.

## Settings for the display specific setup file

I'm using a display specific setup file for the combination ESP32-C3 Supermini with TFT display driver ST7735. This file contains e.g. the display driver, size and pins for the ESP32-device. If your display has a different size please change the height and width accordingly. 

### Copy a file to the User_Setups folder

Please copy the file

    Setup702_C3_SM_ST7735_128x160.h

to the **User_Setups** folder.

### Edit the User_Setup_Select.h file

You need to place the following line in the root folder's "**User_Setup_Select.h**" file

    #include <User_Setups/Setup702_C3_SM_ST7735_128x160.h> // ESP32-C3 Supermini, 27 MHz

Second: please comment all other "#include..." entries like this, especially the "//#include <User_Setup.h>" entry.

````
// Example User_Setup files are stored in the "User_Setups" folder. These can be used
// unmodified or adapted for a particular hardware configuration.
#ifndef USER_SETUP_LOADED //  Lets PlatformIO users define settings in
                          //  platformio.ini, see notes in "Tools" folder.
///////////////////////////////////////////////////////
//   User configuration selection lines are below    //
///////////////////////////////////////////////////////
// Only ONE line below should be uncommented to define your setup.  Add extra lines and files as needed.
//#include <User_Setup.h>                       // Default setup is root library folder
// Setup file in folder Arduino/libraries (updates will not overwrite your setups)
#include <User_Setups/Setup702_C3_SM_ST7735_128x160.h> // ESP32-C3 Super Mini, 27 MHz
````

## GPIO pins setup in the display specific setup file

The **regular setup file** has these pin settings:

```` plaintext
// file Setup702_C3_SM_ST7735_128x160.h
//#define TFT_BL 4  // LED back-light
#define TFT_MISO 20 //  not used/connected
#define TFT_MOSI 6  // = SDA
#define TFT_SCLK 7
#define TFT_CS   21 
#define TFT_DC   10
#define TFT_RST  9  // Set TFT_RST to -1 if display RESET is connected to ESP32 board EN
````

## Important note

You need to modify the display library TFT_eSPI to get the code to work. Please find instructions on how to do this in my forked TFT_eSPI repository here on GitHub: [https://github.com/AndroidCrypto/TFT_eSPI](https://github.com/AndroidCrypto/TFT_eSPI).

