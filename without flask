import pyttsx3
import datetime
import speech_recognition as sr
import wikipedia
import webbrowser as wb 
import random
import os 
from googletrans import Translator


   
   
   
      
   
   
engine =pyttsx3.init('sapi5')
voices= engine.getProperty('voices')
#print(voices[1].id) 
engine.setProperty('voice',voices[0].id)
def speak(audio):
 engine.say(audio)
 engine.runAndWait()
def wishme():
   hour=int(datetime.datetime.now().hour)
   if hour>=0 and hour<12:
     speak("good morning baby")
   elif hour >=12 and hour <18:
      speak("good afternoon baby")
   else:
      speak("good evening baby") 

   speak("ready to work sir ") 


def takecommand():
   #it takes microphone input from user and return string
   r=sr.Recognizer()
   with sr.Microphone() as source:
      print("listening sir ")
      r.pause_threshold =2
      r.energy_threshold=300
      audio=r.listen(source)


   try:
      print("recognizing")
      query=r.recognize_google(audio,language="en-in")
      print(f"user said :{query}\n")  


   except Exception as e :
      #print(e)

   
      print("say that again please")

      return "none"
   return query   

if __name__== "__main__":
    wishme()
    while True:
      query=takecommand().lower()
      #logic to execute task
      if 'wikipedia' in query:
         speak("searching in wikipedia")
         query=query.replace("wikipedia","")
         results=wikipedia.summary(query,sentences=10)
         speak("according to wikipedia")
         print(results)
         speak(results)
      elif 'play music ' in query:

         music_dir='C:\\Users\\harsh\\Downloads\\music folder'
         songs =os.listdir(music_dir)
         print(songs)
         r=random.randint(1,8)
         os.startfile(os.path.join(music_dir,songs[r]))

      elif 'open youtube ' in query:
         wb.open("youtube.com")



      elif ' open LinkedIn 'in query:
         wb.open("linkedIn.com")
      
      
      elif 'open google ' in query:
         wb.open("google.com")
      
      
      
      elif 'open news' in query:
         wb.open("news.com")
      
      
      elif 'open games' in query:
         wb.open("zapak.com")
      
      
      
      
      elif 'joke' in query:
         speak("your college campus bitch ")

       













      elif 'time' in query:
         strTime=datetime.datetime.now().strftime("%H:%M:%S")
         speak("sir the time is {strTime}")

      elif 'translate' in query:
         translator = Translator()
         translation = translator.translate(input("enter string to convert to hindi"), dest='hi')
         print(translation.text)


      elif 'quit ' in query:
         exit   



      
         





