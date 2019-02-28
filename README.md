# ECE387MidtermProject

Inspiration for this project was taken from http://www.jo3ri.be/arduino/projects/lcd-16x2-demo. 

To create any animation on a LCD, there are several steps:

1) Create the animation using https://www.piskelapp.com
    - This allows you to create a canvas of pixels to fit the size of LCD. I used the top portion of the LCD so pixel width and 
    height used was 10px x 8px. This uses two side-by-side blocks on the LCD.
    
2) Define each frame in the Arduino IDE
    - Example:
    
byte smiley[8] = {
       {
                0b00000,
                0b00000,
                0b01010,
                0b00000,
                0b10001,
                0b01110,
                0b00000,
                0b00000
              };

    - The code above will display a smiley face on the LCD. The 1's represent black squares on the LCD. While, the 0's represent an
    empty square on the LCD.
    
    - I recommend using this site: https://mikeyancey.com/hamcalc/lcd_characters.php, it easily translates the pixel drawing to code
    
3) Begin drawing frames on the Arduino IDE

    - For my project, I had the animation move at 250 ms and had several variables increment by 1 to move the animation across the
    screen
    
    - Example:
    
    void catDrawSpace() {
  for (int a = 0; a < 13; a += 2)
  {
    int b = a + 1;
    int c = a + 2;
    int d = a + 3;
    int e = a + 4;
    lcd.clear();
    lcd.setCursor(1, 1);
    lcd.print("KEEP ON WALKING");

    lcd.createChar(1, empty);

    //--FRAME 1--
    lcd.createChar(2, catButtStanding);
    lcd.createChar(3, catFaceStanding);

    - The code above shows the incrementing variables to move the animation across the screen. The lcd.clear() method clears the screen.
    The lcd.setCursor(top lcd bar column, bottom lcd bar column) method is used to move to on of the 16 squares on either the top or bottom
    row of the lcd. Note that this can vary based on the LCD you are using. I have a 16 x 2 LCD screen.
    
4) Create the circuitry for the LCD and test your animation
    - Again I will suggest: http://www.jo3ri.be/arduino/projects/lcd-16x2-demo. There is a wonderful picture showing the basic setup 
    for the Arduino to the LCD and the switch to turn the LCD on and off.
    
    
