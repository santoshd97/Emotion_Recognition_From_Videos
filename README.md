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
  
<h2>Model</h2>


<h2>Result</h2>
