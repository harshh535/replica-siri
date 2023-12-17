from flask import Flask, render_template,url_for
import pyttsx3
import datetime
import speech_recognition as sr
import wikipedia
import webbrowser as wb 
import random
import os 
from googletrans import Translator
app = Flask(__name__)

@app.route("/")
def hello():
         return render_template("index.html")
          

engine = None
voices = None

def initialize_engine():
    global engine, voices
    engine = pyttsx3.init('sapi5')
    voices = engine.getProperty('voices')
    engine.setProperty('voice', voices[0].id)

def speak(audio):
 if not engine:
    initialize_engine()
 engine.say(audio)
 engine.runAndWait()
def wishme():
   if not engine:
    initialize_engine() 

   hour=int(datetime.datetime.now().hour)
   if hour>=0 and hour<12:
     speak("good morning baby")
   elif hour >=12 and hour <18:
      speak("good afternoon baby")
   else:
      speak("good evening baby") 

   speak("ready to work sir ") 

r = sr.Recognizer()

# Flask route for handling voice commands
@app.route('/voice-command')
def voice_command():
    with sr.Microphone() as source:
        print("Listening...")
        audio = r.listen(source)

    try:
        print("Recognizing...")
        query = r.recognize_google(audio)
        print(f"User said: {query}")
        query=query.lower()
        execute_command(query)
    except Exception as e:
        print("Sorry, I couldn't understand. Please try again.")
        print(str(e))

    return ''   
@app.route('/')
def home():
    wishme()
    return render_template('index.html')

@app.route('/command/<string:query>')
def execute_command(query):
    if 'wikipedia' in query:
        # your wikipedia code here
        speak("searching in wikipedia")
        query=query.replace("wikipedia","")
        results=wikipedia.summary(query,sentences=10)
        speak("according to wikipedia")
        print(results)
        speak(results)
    elif 'play music' in query:
        # your play music code here
        music_dir='C:\\Users\\harsh\\Downloads\\music folder'
        songs =os.listdir(music_dir)
        print(songs)
        r=random.randint(1,8)
        os.startfile(os.path.join(music_dir,songs[r]))
    elif 'open youtube ' in query:
        wb.open("youtube.com")
    elif ' open linkedin 'in query:
        wb.open("linkedIn.com")
    elif 'open google ' in query:
        wb.open("google.com")
    elif 'open news' in query:
        wb.open("news.com")
    elif 'open games' in query:
        wb.open("zapak.com")
    elif 'tell joke' in query:
        speak("your college campus bitch ")
    elif 'time' in query:
        strTime=datetime.datetime.now().strftime("%H:%M:%S")
        speak(f"sir the time is {strTime}")
    elif 'translate' in query:
        translator = Translator()
        translation = translator.translate(input("enter string to convert to hindi"), dest='hi')
        print(translation.text)    
    # other elif blocks for your commands
    elif 'quit' in query:
        exit()
    return ''


if __name__ == '__main__':
    app.run(debug=True)
    
