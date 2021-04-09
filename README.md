# Emotion Recognition From Videos

<p>Many companies use sentiment analysis to understand their customers’ reactions to their products. Primarily, these analyses have been carried out on social media and text information.</p><p>However, recently companies have started using multimodal analyses to understand their customers’ reactions in much more details. This project is based on bimodal sentimental analysis, where we utilize textual as well as speech signals to detect emotions.</p>

<h2>Objectives</h2>
<ol><li>We want to understand which features play an important role in speech signals with regards to emotions. For this, we want to look into the theory to understand how human emotions and vocal responses are related. We also want to investigate through experimentation with feature selection.</li>
<li>We want to understand whether through textual sentiment analysis, we can detect contextual emotions associated with certain words, for example, positive words used in a negative sentence to convey sarcasm.</li>
<li>We also want to see if both textual and speech sentiment analysis result can be combined to provide better result than each used independently.</li>
</ol>

<h2>Architecture</h2>
This project identifies the emotion of users based on speech. Currently, it is limited to four emotions namely happiness, sadness, fear and anger. 

![Architecture](https://github.com/santoshd97/Emotion_Recognition_From_Videos/blob/main/Architecture.png)

The project is divided into three parts: The first part involves converting the speech signals to text. The emotion in the text is then identified using a Support Vector Machine (SVM) classifier. The second part involves extracting features from signals. The emotions are then extracted from the dataset of features using Support Vector Machines (SVM) and Random Forest as base models. The data is then trained using Convolution Neural Network. Each speech signal is broken into frames. Each frame will produce a particular emotion from part 1 and part 2. A voting algorithm will pick the highest occurring sentiment and the sentiment is analyzed.

<h2>Training Data Sources</h2>
The training dataset which will be used for emotion detection of audio is taken from multiple sources. The datasets are as follows:
<ul>
  <li>The Ryerson Audio-Visual Database of Emotional Speech and Song (RAVDESS)</li>
  <li>Toronto Emotional Speech Set (TESS)</li>
  <li>Berlin Database of Emotional Speech</li>
  <li>Crowd-sourced Emotional Multimodal Actors Dataset (CREMA-D)</li>
  </ul>

On the other hand, the training dataset which will be used for emotion detection of text is given below:
<ul>
  <li>International Survey on Emotion Antecedents and Reactions (ISEAR)</li>
  </ul>
  
<h2>Methodolgy</h2>
<ul>
<li>Given an audio file we first break it into 30 second frames using ffmpeg package. Each frame is then converted to text using IBM Watson speech to text API.</li>
<li>For detecting emotions through text, we first cleaned the data (removing uppercase, stop words, punctuation, etc.) and tokenized the sentences into words. After this, we performed stemming using Porter Stemmer and vectorized the words which is required for SVM model. Finally, these vectorized words are fed to the SVM classifier for classifying the corresponding emotions.</li>
<li>For emotion recognition from speech data, we are using Librosa library in python to extract audio features which are basically categorized into spectral (related to spectrum of audio), prosodic (stress and intonation patterns of speech) and qualitative (representing characteristics of voice). Based on theory referred from various papers, we have found that spectral features such as Mel-frequency cepstral coefficient (MFCCs), Pitch Chroma, Spectral Centroid and Spectral Skewness/Contrast, prosodic features such as Zero Crossing Rate and Root Mean Square and Energy (RMSE), and qualitative feature Mel-frequency play an important role in recognition of emotions. Using these and through experimentations, we reduced the features to hundred to be used in final training.</li>
<li>For feature selection, we have analyzed correlation between the features and removed highly correlated features. We have also used Recursive Feature Elimination (RFE) to select top 100 most relevant features. This reduced the time to train the model and provided slightly better results in some models.</li>
<li>For training the model, we have used Support Vector Classifier (SVC) and Random Forest to give us an idea of the accuracy. Finally, the model was trained using Convolution Neural Network with four hidden layers. The test dataset was used as validation set in the neural network. We have used Keras library for the same.</li>
<li>The results from both text and speech models are then combined using a priority algorithm. Longer audio files are broken into bits of 5-10 seconds and for each bit, we predict emotion using text and speech. The frequencies of emotions present in both the arrays are calculated and priorities are assigned to each of them. For the final result, for each bit, emotions predicted through text and speech are weighed and if found conflicting, the emotion with higher priority is selected, otherwise, it is taken as the final emotion for that bit.</li>
</ul>

<h2>Result</h2>
<ul>
<li><b>Achieved 69% accuracy</b> using SVM multiclass classifier while extracting emotions from text.</li>
<li>For the model, which was used to extract emotions from speech, the base model accuracy for SVM multiclass classifier was 44% for unscaled data and 61% for scaled data using all the features except highly correlated. For Random Forest, the highest accuracy was achieved at 71% for data with reduced features. The final training model gave us the highest accuracy of 72% using Convolution Neural Network.</li>
  </ul>
<p>For the final results, we used longer videos and divided into 10 seconds bits. The result from both these were combined using the priority algorithm, which produced satisfactory results.
<p>We believe that a real time emotion detection system, using this method which we attempted can be very useful for lot of companies to analyze the responses of their customers over calls or other feedbacks.
