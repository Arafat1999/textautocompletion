# textautocompletion

# Introduction: -
Implemented android app that automatically gives suggestions to
the user as he/she is typing. The distances between the input text and an
English dictionary of 20,000 words are calculated. The words with the
lowest distances are suggested to the user to automatically complete the
text.

Text Auto-completion app uses the Levenshtein distance to create an
android app that generates suggestions to the user while typing that helps
in automatically completing or correcting a single word. The user text
input is compared to a dictionary of words. The words with the least
distance are suggested to the user. The user can then select a suggested
word rather than typing it.

Text Auto-completion can reduce the human efforts of typing and reduces
the chances of spelling errors. It saves time by suggesting the text rather
than typing the whole word. The app could also suggest corrections for
spelling mistakes. It also Improves user experience.

# Working: -
An editable text view where the user will type the text and the buttons
will show the text suggestions automatically while user is typing. The
suggestions is displayed in the three buttons from which the user can
choose/click on the text/button to replace the content of the edit box with.

Here we are using Levenshtein Distance, The primary method name
is levenshtein(), and it accepts 2 arguments token1 and token2,
representing the 2 words to be compared. It returns an integer representing
the distance between these 2 words.

For our application, the distance is to be calculated between the user text
input and all words in the dictionary. The closest words to the input are
suggested to the user for autocompletion. The next section reads the
dictionary and calculates the distance between all words within it, as well
as the user input.

Comparing the Dictionary to the User Input and Making Suggestions:
The dictionary used in this application is available as a text file.

This section creates a method named returnSuggestions(), which accepts 2
arguments:
word: The text entered by the user.
numWords: Number of suggestions to return.

The method returns a String array representing the closest words to the
user input.
String [] returnSuggestions(String word, int numWords){
}

Because the dictionary has 20,000 words, the method creates a String
array of length 20,000 to hold all words in the dictionary alongside their
distance to the user input.
String[] dictWordDist = new String[20000];

After that, the text file is read. The text file, in, is named 20k.txt, which is
available in the assets directory of the Android project. The text file holds
only 1 word per line, and thus the readLine() method is used to return each
word in the line variable.

After the word is returned, the levenshtein() method is called to calculate
the distance between the user input and the current word in the dictionary.
The distance is saved into the integer variable named wordDistance. The
distance, separated by - from the dictionary word, is inserted into the
previously created array dictWordDist. For example, if the word is age
and the distance is 5, then 5-age is inserted into the array. By doing this,
we’ll be able to sort the words according to their distances.

After calculating the distances between all 20,000 dictionary words and
the user input, the distances separated by - from the words will be
available in the dictWordDist array. The next step is to sort the array in
ascending order so that the closest words are available at the beginning of
the array.
Arrays.sort(dictWordDist);

The next step to create a String array that holds the closest words.
String[] closestWords = new String[numWords];

Here’s how the closest words are fetched. Using a for loop that loops
through the first numWords words in the array dictWordDist, each
element is returned into the variable currWordDist. To separate the textual
word from its numerical distance, the split() method is used to return an
array named wordDetails holding 2 elements. The first one is the distance,
and the other one is the dictionary word. Only the word is inserted in the
closestWords array.
String currWordDist;
for (int i = 0; i < numWords; i++) {
currWordDist = dictWordDist[i];
String[] wordDetails = currWordDist.split("-");
closestWords[i] = wordDetails[1];
}

We successfully created a String array named closestWords that holds the
closest words to the user input. These words will be used as suggestions
from which the user can select to automatically complete the word being
entered.
