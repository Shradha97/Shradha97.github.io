---
layout: default
---

# WaveGlow: A Generative Network for Speech Synthesis
Before I move on to the work, I feel it would be good to give a brief intro about the place where I persued this work. 

## Mihup Communications Pvt. Ltd.
**Mihup**, short for **May I Help You Please** is an AI and ML-based startup built on **Automatic Speech Recognition** for both online and offline platforms in Indian languages. With an AI foundation for scale and reliability in Natural Language Processing(NLP) and Information Retrieval(IR), it offers flexibility to support customer-specified features, content domains. Media and Entertainment, consumer electronics, IoT, retail and e-commerce, automotive, BFSI are among the industry segments can be benefited from Mihup’s capabilities. 

It started as an offline platform in the year 2014, where one could ask questions (via SMS) and get an instant answer and has made its way into ‘The top 50 most promising start-ups in the world’ within a span of just 4 years. Mihup’s domain knowledge consists of Hinglish (a mix of Hindi and English) and its deep research are extending towards accents and dialects across languages, and is currently working with English, Hindi, Bengali, Hinglish, and Benglish (mix of Bengali and English) and many other Indian Languages.

## A brief of my experience
Well, since Mihup is a start-up, I entered the company with a perception that I would be directly working on a small part of their potentially big product that they would be planning to launch to the market, which would be far from doing any kind of research and more of my experience of the hard-core corporate life. 

Frankly speaking, I always see myself as a researcher, everything I do, think...all, I tend to approach like a researcher naturally. So while entering Mihup, I was a bit nervous by the thought of how would the corporate life be different, would it match match with my research thinking. But...as it is rightly said *"**Never judge a book by its cover**"*. I was part of the **research team**, headed by **Mr. Harmandeep Singh Matharu, the Vice President of Engineering**. The work assigned to me was no less than doing a research. Since they were launching a new product into the market, and to be competitive enough, they ought to add something new to their product, hence it was important to dive into the research aspect of it too. 

It was a great pleasure to be a part of the Mihup team, it not just gave me a view of how research is done in a company but equally exposed me to the corporate world, I got a view of how systems are actually deployed to the market, specially, how machine learning is done and deployed in the market. Most importantly I could witness the theory studied in my courses at IIT being put to practical uses. When you get the opportunity can turn ur knowledge into something that's gonna benefit the world is one of best moments in your life time according to me, and...believe me, that was one of those moments. I would always be thankful to the team for introducing to the world of Speech Recognition and for the new experiences. 

## A Study on WaveGlow Text-to-Speech System for Offline Deployabililty
As voice is the future, the world’s technology giants are clamoring for vital market share by placing voice-enabled devices at the core of their strategy. Since a huge amount of data is required to achieve this feat and the system tends to be heavy memory-wise, most of these voice-enabled devices are deployed for online platforms. But online platforms leave customers vulnerable to privacy issues, bcoz of which we decided to focus on the possibility of deploying these models for different low memory platforms in an offline mode. This would broaden the boundaries of use cases for the concerned problem. Through this work, our aim was to:
* try to build offline deployable TTS systems from already existing models and test their usability.
* study the important factors observed that need to be taken into account while the offline deployment of these online models.

## Text-to-Speech system (TTS)
![TTS](https://user-images.githubusercontent.com/35024433/69430873-89e72280-0d5c-11ea-8ebe-682edf0568ff.png)

**Text to speech**, abbreviated as **TTS**, is a form of speech synthesis that converts text into spoken voice output. It consists of two units: **Natural Language Processing Unit (NLP)** and **Digital Signal Processing (DSP)** or **Synthesizer unit**. The DSP unit has a subunit called the **vocoder** which converts speech features into audio. Our focus was be mainly on the vocoder component of the TTS.

## WaveGlow
![waveglow](https://user-images.githubusercontent.com/35024433/69430979-be5ade80-0d5c-11ea-8867-78cafb7261cf.png)

WaveGlow is essentially a vocoder which was recently developed by **NVIDIA Corporation**, which is a combination of the well known [WaveNet](https://deepmind.com/blog/article/wavenet-generative-model-raw-audio) and [Glow](https://openai.com/blog/glow/) systems.
We used this WaveGlow model for the purpose of our research. For more detailed understanding of WaveGlow, please refer to [this](https://arxiv.org/abs/1811.00002). 

## Approach Flow
![approach](https://user-images.githubusercontent.com/35024433/69433463-a6398e00-0d61-11ea-8d1d-62da9b75e2c4.png)

### Choosing the TTS Model
As I mentioned above, for this project, we chose to work with the WaveGlow model. We chose this over other models like WaveNet and Glow because of its comparitively more promising results in the online TTS system, moreover it combines the most important components of both WaveNet and Glow into a single model thus making it more preferable.

### Choosing the Framework and Datasets
The original WaveGlow model was built in PyTorch. We decided to rebuild the model in **Tensorflow** and **Chainer** respectively because these frameworks are supported by wider variety of platforms. Our first aim was to build a model that could be deployed to **Raspberry Pi3**. We chose [Libri-Speech](https://keithito.com/LJ-Speech-Dataset/) dataset for the training purpose.

* **WaveGlow-Tensorflow**

    For deployment purposes of Machine Learning models, Tensorflow is one of the most widely used frameworks. So, the first       choice for a different framework was Tensorflow.  Moreover, for deploying the model offline, TensorFlow Lite                   was the considered framework, hence, going for Tensorflow was the best choice.
    The WaveGlow model was redesigned for the latest version of Tensorflow, Tensorflow Nightly-2.0. 
    
    But, after training this Tensorflow model, we found out that it was failing to converge for the GPU version. Hence, the       results obtained were inconsistent.
    
* **WaveGlow-Chainer**

    In order to deal with the problem faced with the Tensorflow model, we had to switch to a new framework which would             be more stable and consistent. So, we moved on to the Chainer framework. One more reason for choosing Chainer was because of its excellent GPU data center performance. According to the reports, recently, Chainer became the world champion for GPU data center performance, beating even Tensorflow and can be run on multiple GPUs with very little effort.
    
   This Chainer model was consistent as compared to the previous Tensorflow model, but with a disadvantage, where TensorFlow takes just 3 - 4 days for training the model, Chainer takes almost 3 weeks to train the same model. 

### Redesigning the Model for the Chosen Framework and Platform  
Now, it was important to redesign the model so that it could be deployed to low level devices like Raspberry Pi3. The most important factor to be taken into account to make a model suitable for such devices is the size factor. The original model was of the order of 300 GB, whereas the required memory limit was of 80-90 MB. The following algorithm was devised and followed in order to achieve the goal.

![image7](https://user-images.githubusercontent.com/35024433/69431142-24dffc80-0d5d-11ea-856a-89f6962f7956.png)

For a detailed understanding of the approach, please refer to the full [report](WaveGlow_report.pdf).

## Necessary Factors for Offline Deployability

| Factor | Explanation |
| :----: | :----: |
| Size of model | Application to be run must be of the size of MBs, max 80-90 MBs is preferable |
| Number of layers in model vs Accuracy | The number of layers should be chosen such that the loss value converges for the trained model and the accuracy doesn't go very low respectively |
| Accuracy vs Clarity of speech heard | Accuracy is an important factor in deciding whether the model can be released for user experience or not, but the quality of the audio output plays a more important role in deciding the usability of the model.|

## Output and Results

The following table contains the models obtained after training the WaveGlow Chainer model. Inference of these models will yield the required audio.

 | Training Epochs | Model |
 | :---: | :---:|
 | 39000 | |
 | 40000 | |
 | 125000 | |
 | 350000 | |
 | 500000 | |

The **source code for this project** can be found [here](https://github.com/Shradha97/chainer-WaveGlow). To obtain the audio files, first download these models. Then follow the instructions in the repository to install the prerequisites and run the command for generation.

## References
1. [WaveGlow: A Flow-based Generative Network for Speech Synthesis by Ryan Prenger, Rafael Valle, Bryan Catanzaro](https://arxiv.org/pdf/1811.00002.pdf). 
2. [ Glow: Generative Flow with Invertible 1x1 Convolutions by Diederik P. Kingma, Prafulla Dhariwal](https://arxiv.org/pdf/1807.03039.pdf).
3. [WaveNet: A Generative Model for Raw Audio by Aaron van den Oord, Sander Dieleman, Heiga Zen, Karen Simonyan, Oriol Vinyals, Alex Graves, Nal Kalchbrenner, Andrew Senior, Koray Kavukcuoglu](https://arxiv.org/abs/1609.03499).
4. [Towards Understanding the Invertibility of Convolutional Neural Networks by Anna C. Gilbert, Yi Zhang, Kibok Lee, Yuting Zhang, Honglak Lee](https://arxiv.org/abs/1705.08664).
5. [Introduction to Chainer: A Flexible Framework for Deep Learning, a seminar by Seiya Tokui](https://www.slideshare.net/beam2d/introduction-to-chainer-a-flexible-framework-for-deep-learning).
6. [Glow: Generative Flow with Invertible 1x1 Convolutions lecture by D. Kingma and P.Dhariwal, OpenAI](https://www.youtube.com/watch?v=6OVH1i2BVAE).


