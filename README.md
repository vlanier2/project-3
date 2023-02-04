# UOCIS322 - Project 3 #

NAME: Vincent Lanier

CONTACT: vlanier@uoregon.edu

## Project Description

The program is a simple anagram game designed for English-learning students in elementary and middle school. It presents a list of words to students and an anagram. The anagram is a jumble of some of the words, which are randomly chosen. Students attempt to type words that can be created from the jumble. When a matching word is typed, it is added to a list of solved words.

The vocabulary word list is fixed for one invocation of the server, so multiple students connected to the same server will see the same vocabulary list but may have different anagrams.

The frontend is built with AJAX and JQuery with a Flask backend.

## Setup

### Supplying a Credentials File

credentials-skel.ini should be replaced by a credentials.ini file specifying the port and debug mode. If no credentials file is provided, it defaults to port 5000 and debug=True. *Note: The credentials.ini file should be placed in the /vocab directory so it can be accessed within the container.

credentials.ini should also provide three additional variables related to the anagram game.

"secret_key" - should be replaced by a random string

"success_at_count" - decides how many words must be guessed to win the game

"vocab" - path to the vocab list used in the game. Three vocab lists are provided in /data and any custom vocab list can be used in this format

### Building a Container

Move to /vocab and build the simple flask app image using

```
docker build -t <some-image-name> .
```

Run the container using

```
docker run -d -p desired-port:5000 some-image-name
```

## Anagram Game

Use the letters provided in bold to determine which of the words shown make up the anagram. When you have a guess, type in the field labeled word. 
The page will dynamically update and let you know one of three cases: 

1) The typed characters are not in the list of words

2) The typed word can't be made from the letters in the anagram

3) You already found the word

Once a word is correctly guessed, it will appear on screen under "You found". Once the required number of words are guessed you are redirected to a success page and given the option to return and start again.

## Shutting Down

Simply shut down the flask app with ctrl-c in your terminal, and/or stop the docker container.