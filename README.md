# Recognizing Composers Using High-Level Features

Automatic classification of classical music scores according to their composer, by applying methods common in text classification. Event durations and sequences of approximated chords are extracted from the dataset. Tf-idf values are computed for durations and chord n-grams, then used to build five composer classifier models: support vector machine, logistic regression, k-nearest neighbors, Naive Bayes and multilayer perceptron. The support vector machine is shown to work best in both two-class and multiclass settings.

Identifying the composer by listening to a piece of music is a task often associated with human knowledge of music. An entrance exam for the composition program of a conservatory will typically require the candidate to listen to a piece of music without knowing its composer or title, then to identify the stylistic elements as well as historical context pertinent to the composer of that piece. In other words, recognizing composers usually requires the combined knowledge of music theory and history.

This experiment tackles the previously mentioned task using machine learning methods. Without heavily relying on expert knowledge, this data-driven approach seeks to build accurate predictive classification models using features collected from labeled data given in the form of MIDI files. Specifically, it focuses on the usage of chords by each composer and applies methods common in information retrieval and text mining, such as n-grams and tf-idf values, to the classification of musical scores. In addition, the durations of notes, chords and rests are also considered as features.

![Squish all notes within length of one quarter note to a chord id number](notes-to-chordnumbers.png)

Course project for Machine Learning ([Professor Robert M. Haralick](http://www.haralick.org), Graduate Center, CUNY, Spring 2017)

Keywords: music classification, high-level musical feature, chord n-grams, duration, machine learning, music21, scikit-learn.

Project settings:
- Python 3.5.2
- scikit-learn 0.18.1
- music21 3.1.0
- (optional, for midi-mxl conversion) MuseScore 2.0

### Converting MIDI files to MusicXML

The original dataset consists of MIDI files. I've noticed that some scores take a long time to parse using music21, and also that part of the data like rhythm information is a bit messed up in the imported object. Converting the files into MusicXML before importing seemed to help. In Mac OS with MuseScore 2.0 installed, I used the following shell command:

``` 
> cd {TARGETDIR}  
> find {MIDIFILEDIR} \( -name "bach*.mid" -o -name "beethoven*.mid" -o -name "debussy*.mid" -o -name "scarlatti*.mid" -o -name "victoria*.mid" \) -type f -exec cp {} . \;  
> find . -type f -name "*.mid" -exec /Applications/MuseScore\ 2.app/Contents/MacOS/mscore {} --export-to {}.mxl \;  
> for f in *.mxl; do mv "$f" "${f%.mid.mxl}.mxl"; done  
> ls *.mxl > mxl_list.txt 
```

TODO

- [x] Upload (processed) dataset
- [ ] Make code cleaner, add comments, etc
- [x] Add pdf write-up
- [x] Add instructions for MIDI conversion
- [ ] Translate to lang:ko?
