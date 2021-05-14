import PySimpleGUI as sg
from utils import *
from nltk.corpus import wordnet as wn
def get_meaning(word):
    synset = wn.synsets(word)
    if synset:
        return synset[0].definition()
    else:
        return None

def get_synonyms(word):
    synonyms =[]
    for synset in wn.synsets(word):
        for lemma in synset.lemmas():
            synonyms.append(lemma.name())
    return set(synonyms)

def get_antonyms(word):
    antonyms = []
    for synset in wn.synsets(word):
        for lemma in synset.lemmas():
            if lemma.antonyms():
                antonyms.append(lemma.antonyms()[0].name())
    return set(antonyms)
def get_example(word):
    example =[]
    for synset in wn.synset(word):
        for lemma in synset.lemmas():
            if lemma.example():
                example.append(lemma.exampe()[0].name())
    return set(example)
word = 'good'
#print(get_meaning(word))
#print(get_synonyms(word))
print(get_antonyms(word))

sg.theme('DarkAmber')
greeting = "Hi.This ia a programmed Robot by " \
           "Jothi Mangai\n"
layout = [
    [sg.Multiline(greeting, font=("Verdena", 14), size=(70, 15), key='output')],
    [sg.InputText("", font=("Verdena", 14), size=(50, 1), key='input', enable_events=True)],
    [sg.Button("Meaning", font=("Verdena", 14), bind_return_key=True, key="meaning"),
     sg.Button("Synonyms", font=("Verdena", 14), key='synonyms'),
     sg.Button("Antonyms", font=("Verdena", 14), key='antonyms'),
     sg.Button("Clear", font=("Verdena", 14), key='clear')
    ]
]
def display_meaning(word):
    meaning=get_meaning(word)
    window['output'].print("Word: " + word)
    if meaning:
        window['output'].print("Meaning: ", meaning)
    else:
        display_error("Meaning Not Found")
def display_synonyms(word):
    synonyms=get_synonyms(word)
    window['output'].print("Word : " + word)
    if synonyms:
        window['output'].print("Synonyms: ", synonyms)
    else:
        display_error("No Synonyms Found")
def display_antonyms(word):
    antonyms=get_antonyms(word)
    window['output'].print("Word : " + word)
    if antonyms:
        window['output'].print("Antonyms: ", antonyms)
    else:
        display_error("No Antonyms Found")
def display_error(message):
    window['output'].print("Error : " +message, text_color='white')
if __name__=='__main__':
    window = sg.Window('File Explorer', layout)
    while True:
        event,values=window.Read()
        if event=='meaning':
            display_meaning(values['input'])
        elif event=='synonyms':
            display_synonyms(values['input'])

        elif event=='antonyms':
            display_antonyms(values['input'])
        elif event=='clear':
            window.FindElement('output').Update(greeting)
        elif event == sg.WINDOW_CLOSED:
            break
    window.close()
