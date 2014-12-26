60PY02
======

A Python module for outputting assembly for 6502 processors, oriented toward making pixel art.

Up to now, all testing of output for this module has happenend on http://www.6502asm.com/ http://skilldrick.github.io/easy6502/.

Definition and use of function getAsm_Line():

getAsm_Line() is a function that returns valid 6502 assembly to color any pixel on the display.

GetAsm_Line(start, pixels, color):

   stringToReturn = ""
   
   colorDict = {
                  "black": "$00", "white": "$01", "red": "$02", "cyan": "$03",
                  "purple": "$04", "green": "$05", "blue": "$06", "yellow": "$07",
                  "orange": "$08", "brown": "$09", "light red": "$0A", "dark gray": "$0B",
                  "gray": "$0C", "light green": "$0D", "light blue": "$0E", "light gray": "$0F"
                }
                
   for i in range(0, pixels):
     stringToReturn = stringToReturn + "LDA #" + colorDict[color] + "\n" + "STA $" + getHexString(start + i) + "\n\n"
        
   return stringToReturn


Parameters:
  start as int, pixels as int, color as str.
  
  start:
  
  An int that will be converted into a valid hex number to represent either a memory address/location or a value to
  put into a memory address/location.
  
  pixels:
  
  An int that represents how many pixels will be drawn based on the string that getAsm_Line returns.
    
  color:
  
  A string that will be used as a key to acces hex codes corresponding to each color the the 6502 is
  capable of producing.

  Acceptable colors to pass in:
  black, white, red, cyan, purple, green, blue, yellow,
  orange, brown, light red, dark gray, gray, light green, light blue, light gray.

  All others strings passed in will result in a KeyError when trying to access data from colorDict.
