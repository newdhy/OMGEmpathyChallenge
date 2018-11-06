# OMGEmpathyChallenge

Website: https://www2.informatik.uni-hamburg.de/wtm/omgchallenges/omg_empathy.html

**Organization**

Pablo Barros, University of Hamburg, Germany </br>
Nikhil Churamani, University of Cambridge, United Kingdom </br>
Angelica Lim, Simon Frases University, Canada </br>
Stefan Wermter, Hamburg University, Germany </br>

**OMG-Empathy Dataset**

The OMG-Empathy corpus is composed of recordings of two individuals talking to each other about a certain topic. One of the individuals is an actor who leads a semi-scripted conversation with a listener. The actors tells stories about what happened to them recently, and we recorded the reactions of the listener to these stories over time, which can contain short interactions.

We created a series of eight topics that the actor talked about, each of them related to one or more emotional state:

- Story 1 - A childhood friend.
- Story 2 - I started a band!
- Story 3 - My relation with my dog.
- Story 4 - I had a bad flight experience.
- Story 5 - I had an adventurous traveling experience.
- Story 6 - I cheated on an exam when I was younger.
- Story 7 - I won a martial arts challenge.
- Story 8 - I ate a very bad food.

The actor was free and encouraged to improvise on each of these topics, so that we recorded a natural conversation scenario, but the actor was instructed to maintain the control over the conversation. This way, we guaranteed that the recorded interaction were not one-sided, and at the same time that the listener did not overtake the direction of the conversation.

We recorded the audio and visual data of both the actor and listener for each interaction. Immediately after each session, we asked the listeners to watch the interactions on a computer screen and use a joystick to annotate how they felt in terms of valence using a continuous scale ranging from positive to negative values. The use of the joystick allowed for continuous and gradual tracking of annotations which are temporally related to the interaction scenario.

We used a total of four different actors, each one of them taking part in the conversation with two different topics. This way we collected different reaction levels from different listeners for the same actor. We had a total of 10 subjects, each one taking part in all the eight topics. This gave us 80 different interaction videos. Each video had an average of 5 minutes and 12 seconds, providing us with 415 minutes (around 7 hours) of recordings.

**Tracks**

We let available for the challenge a pre-defined set of training, validation and testing samples. We separate our samples based on each story: 4 stories for training, 1 for validation and 3 for testing. Each story sample is composed of 10 videos with interactions, one for each listener. Although using the same training, validation and testing data split, we propose two tracks which will measure different aspects of the self-assessed empathy:

The **Personalized Empathy track**, where each team must predict the empathy of a specific person. We will evaluate the ability of proposed models to learn the empathic behavior of each of the subjects over a newly perceived story. We encourage the teams to develop models which take into consideration the individual behavior of each subject in the training data.

The **Generalized Empathy track**, where the teams must predict the general behavior of all the participants over each story. We will measure the performance of the proposed models to learn a general empathic measure for each of the stories individually. We encourage the proposed models to take into consideration the aggregated behavior of all the participants for each story, and to generalize this behavior in a newly perceived story.

**Baseline**

As a baseline for both protocols, we decided to use a state-of-the-art model for emotion recognition. By providing a baseline with an emotion recognition model, we hope to encourage others to use more specific solutions for empathy tracking.

We choose to calculate the valence of each of our videos using the winner model of the recent OMG-Emotion Recognition challenge~\cite{Zheng2018}. This model makes use of a hybrid neural network for multimodal emotion recognition. It uses a temporal attention layer to improve the recognition of emotions over time. The baseline model is composed of two individual networks used for feature extraction: a video network and an audio one.

To provide a proper baseline for the dataset, and to encourage the development of computational models which are not based on perception only, we calculate the valence using the actor (by using only the actor facial expression and audio) and the listener (only the listener face expression and audio). We then calculate the CCC between the perception model and the self-assessment annotations using both protocols.

|**Personalized Track** | - |


|**Subject**| **CCC** |
| --- | --- |
|Subject 1 | 0.01|
|Subject 2 | 0.11|
|Subject 3 | 0.04|
|Subject 4 | 0.1|
|Subject 5 | 0.11|
|Subject 6 | 0.35|
|Subject 7 | -0.01|
|Subject 8 | 0.05|
|Subject 9 | 0.05|
|Subject 10 | 0.10|
|**Mean**   | 0.091|


| -  |- |
|**Generalized Track** |- |
|**Story** | **CCC**|
|Story 1 | 0.111|
|**Mean**    | 0.111|




**Dataset Structure**

The dataset is separated into .mp4 videos. Each video name contain the story and subject information. The annotations follow the same name structure. Each .csv contain a header ("valence") and each row of the file represents the valence of one frame of the video.


**Scripts**

We provide the following scripts:

- OMG_empathy_extract_audio.py: a script used to extract an audio file (in .wav format) for all the videos of the dataset.

- OMG_empathy_extract_faces.py: a script used to extract the faces (from both actors and subjects) for all the videos of the dataset.

- calculateCCC.py: a script used to calculate the CCC of the output of a model and the validation set for both tracks.

To calculate the CCC for both tracks, the script takes as arguments two folders: one with the validation .csv files and one with the model's .csv files. Be aware that the folders must contain the same amount of files and they must have he same file name - following the same structure as the annotations: Subject_X_Story_X.csv. Each file must contain a header ("valence") and each row of the file must be the valence output for each frame of the video.


**How to participate**

Important dates: 
- 25th of September 2018  - Opening of the Challenge - Team registrations begin
- 1st of October 2018 - Training/validation data and annotation available
- 3rd of December 2018 - Test data release
- 5th of December 2018 - Final submission (Results and code)
- 7th of December 2018 - Final submission (Paper)
- 10th of December 2018 - Announcement of the winners

To participate to the challenge, please send us an email to barros @ informatik.uni-hamburg.de with the title "OMG-Empathy Team Registration". This e-mail must contain the following information:
- Team Name
- Team Members
- Affiliation
- Participating tracks

We split the corpus into three subsets: training, validation and testing. The participants will receive the training and validation sets, together with the associated annotations once they subscribe to the challenge. The subscription will be done via e-mail. Each participant team must consist of 1 to 5 participants and must agree to use the data only for scientific purposes. Each team can choose to take part in one or both the tracks.

After the training period is over, the testing set will be released without the associated annotations.

Each team must submit, via e-mail, their final predictions as a .csv file for each video on the test set. The format of the .csv file must be the same as the provided annotations. Together with the final submission, each team must send a short 2-4 pages paper describing their solution published on Arxiv and the link for a github page to their solution. If a team fails to submit any of these items, their submission will be invalidated. Each team can submit 3 complete submissions for each track.

**Paper submission**

Each participating team must submit, together with their final results, a short 2-4 pages paper describing their solution. This paper must follow the IEEE specifications ( Latex and Word templates) and will be peer reviewed following the FG 2019 standards. The accepted papers will be included in the FG 2019 workshop proceedings.

**License**

This corpus is distributed under the Creative Commons CC BY-NC-SA 3.0 DE license. If you use this corpus, you have to agree with the following itens:

- To cite our reference in any of your papers that make any use of the database. 
- The references are provided at the end of this page.
- To use the corpus for research purpose only.
- To not provide the corpus to any second parties.


**More information** 

- our website: https://www2.informatik.uni-hamburg.de/wtm/omgchallenges/omg_empathy.html
- You can also find usefull scripts for processing the dataset here: https://github.com/knowledgetechnologyuhh/OMGEmpathyChallenge

For more informations: barros@informatik.uni-hamburg.de
