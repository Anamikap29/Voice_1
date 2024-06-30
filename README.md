import speech_recognition as sr
import pyttsx3

# Initialize recognizer
recognizer = sr.Recognizer()

# Function to convert text to speech
def speak(text):
    engine = pyttsx3.init()
    engine.say(text)
    engine.runAndWait()

# Function to recognize speech
def recognize_speech():
    with sr.Microphone() as source:
        print("Listening...")
        audio = recognizer.listen(source)

        try:
            # Using Google Speech Recognition
            query = recognizer.recognize_google(audio)
            print(f"User said: {query}\n")
            return query.lower()

        except sr.UnknownValueError:
            speak("Sorry, I didn't get that.")
            return ""
        except sr.RequestError:
            speak("Sorry, my speech service is down.")
            return ""

# Main program loop
if __name__ == "__main__":
    speak("Hello, I am your virtual assistant. How can I help you today?")

    while True:
        query = re
