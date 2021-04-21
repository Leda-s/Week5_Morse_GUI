######## MORSE CODE ########

from tkinter import *
import tkinter.font
from gpiozero import LED
import RPi.GPIO
RPi.GPIO.setmode(RPi.GPIO.BCM)
import time

#Hardware
ledRed = LED(10)
ledGreen = LED(9)
ledBlue = LED(11)


#GUI DEFINITIONS#
win = Tk()
win.title("Morse Code LED")
myFont = tkinter.font.Font(family = 'Helvetica', size = 12, weight = 'bold')



#Event functions#

#Turn off all LED's
def turnOffLeds():
    ledRed.off()
 

#Red
def ledToggleRed():
    turnOffLeds()
    if ledRed.is_lit:
        ledRed.off()
        ledButtonRed["text"] = "Red LED on"
        
    else:
        ledRed.on()
        ledButtonRed["text"] = "Red LED off"


#Dot function
def dot():
    ledRed.on()
    time.sleep(0.5)
    ledRed.off()
    time.sleep(0.5)


#Dash function
def dash():
    ledRed.on()
    time.sleep(1.5)
    ledRed.off()
    time.sleep(0.5)


#Translate the letter to morse code and then flash the letter in morse code through the LED
def toMorse(letter):
    
    if letter == "a":
        dot()
        dash()
        
    if letter == "b":
        dash()
        dot()
        dot()
        dot()
        
    if letter == "c":
        dash()
        dot()
        dash()
        dot()
        
    if letter == "d":
        dash()
        dot()
        dot()
        
    if letter == "e":
        dot()
        
    if letter == "f":
        dot()
        dot()
        dash()
        dot()

    if letter == "g":
        dash()
        dash()
        dot()
        
    if letter == "h":
        dot()
        dot()
        dot()
        dot()
        
    if letter == "i":
        dot()
        dot()
        
    if letter == "j":
        dot()
        dash()
        dash()
        dash()
        
    if letter == "k":
        dash()
        dot()
        dash()
        
    if letter == "l":
        dot()
        dash()
        dot()
        dot()
        
    if letter == "m":
        dash()
        dash()
        
    if letter == "n":
        dash()
        dot()
        
    if letter == "o":
        dash()
        dash()
        dash()
        
    if letter == "p":
        dot()
        dash()
        dash()
        dot()
        
    if letter == "q":
        dash()
        dash()
        dot()
        dash()
        
    if letter == "r":
        dot()
        dash()
        dot()
        
    if letter == "s":
        dot()
        dot()
        dot()
        
    if letter == "t":
        dash()
        
    if letter == "u":
        dot()
        dot()
        dash()
        
    if letter == "v":
        dot()
        dot()
        dot()
        dash()
        
    if letter == "w":
        dot()
        dash()
        dash()
        
    if letter == "x":
        dash()
        dot()
        dot()
        dash()
        
    if letter == "y":
        dash()
        dot()
        dash()
        dash()
        
    if letter == "z":
        dash()
        dash()
        dot()
        dot()
    
   
#String to Letters function
def toLetters(userString):
    
    for i in userString:
        toMorse(i)
        time.sleep(1)
    
        
#Enter Text
def enter():
    
    displayArea.delete(1.0, END) #Clear display box
    
    textString = textArea.get("1.0", "end-1c")
    textStringLen = len(textString)

        
    if textStringLen <= 12 and textString.isalpha() : 
    
        #Print text to the console
        print(textString)
        
        #Print to display box
        displayArea.insert(END, 'Success! Printed in Morse code')

        #Translate to morse code using the toLetters function, first change letters into lower case.
        textLowerCase = textString.lower()
        toLetters(textLowerCase) 

    #Message if the text entered is too long or is not letters
    else:
        displayArea.insert(END, 'Failed! Text must be letters and less than 12 characters')

#Close
def close():
    RPi.GPIO.cleanup()
    win.destroy()


#Text Box
textArea = Text(win, height = 2, width = 30)
textArea.grid(row = 1, column = 1)

#Label
label = Label(win, text = "Enter a word")
label.grid(row = 2, column = 1)

#Display area
displayArea = Text(win, height = 2, width = 30, bg = 'light cyan')
displayArea.grid(row = 4, column = 1)

#Enter button
enterButton = Button(win, text = 'Enter', font = myFont, command = enter, bg = 'bisque2', height = 1, width = 6)
enterButton.grid(row = 3, column = 1)

#Exit
exitButton = Button(win, text = 'Exit', font = myFont, command = close, bg = 'bisque2', height = 1, width = 6)
exitButton.grid(row = 5, column = 1)


win.protocol("WM_DELETE_WINDOW", close) #Exit cleanly

