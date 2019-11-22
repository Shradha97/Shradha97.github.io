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

Text to speech, abbreviated as TTS, is a form of speech synthesis that converts text into spoken voice output. It consists of two units: Natural Language Processing Unit(NLP) and Digital Signal Processing(DSP) or Synthesizer unit. The DSP unit is also called the **vocoder** which converts speech features into audio. Our focus would be mainly on the vocoder component of the TTS.

## WaveGlow
![waveglow](https://user-images.githubusercontent.com/35024433/69430979-be5ade80-0d5c-11ea-8867-78cafb7261cf.png)
WaveGlow is essentially a vocoder developed by NVIDIA, which is a combination of the well known WaveNet and Glow systems.

![image7](https://user-images.githubusercontent.com/35024433/69431142-24dffc80-0d5d-11ea-856a-89f6962f7956.png)
