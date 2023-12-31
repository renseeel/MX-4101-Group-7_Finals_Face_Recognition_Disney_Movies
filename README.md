# <h1 align="center">![image](https://github.com/renseeel/MX-4101-Group-7_Finals_Face_Recognition_Disney_Movies/assets/143627650/d5613900-98b4-4f51-9b59-d4cd29b33bab)</h1>

_**Author/s**: Hannah Jocelle P. Bacong, Jancene Grace C. Generoso, and Renzell M. Mercado_

<p align="justify"> Disney movies, a treasure trove of wonder and delight, weave magical narratives that transcend generations. From the groundbreaking classics like "Snow White and the Seven Dwarfs" to the modern masterpieces such as "Frozen" and "Moana," Disney's cinematic repertoire is a kaleidoscope of imagination and emotion. These films transport audiences to enchanting worlds filled with vibrant characters, unforgettable melodies, and timeless messages. With their artistry in storytelling and animation, Disney movies serve as a universal language, evoking laughter, tears, and a sense of wonder. They embody the essence of storytelling at its finest, leaving an indelible mark on the hearts of viewers worldwide, fostering dreams and reminding us of the enduring power of imagination and the importance of believing in the extraordinary. </p>

<p align="justify"> Face recognition is a technology that involves identifying or verifying individuals by analyzing and comparing patterns based on their facial features. It is a subset of biometric technology that uses distinctive characteristics of a person's face to distinguish them from others.
    
For this tale, the group task is to develope a face recognition program that accurately identifies and acknowledges Disney Live-Action Princess characters. This activity must be aligned with the pivotal action of making an interactive Dashboard for the brand of Disney Movies.

The group used the following codes provided below: </p>


### 🎬 ℑ𝔪𝔭𝔬𝔯𝔱𝔦𝔫𝔤 ℑ𝔪𝔞𝔤𝔢𝔰 𝔣𝔯𝔬𝔪 𝔊𝔦𝔱𝔥𝔲𝔟 𝔞𝔫𝔡 ℑ𝔫𝔰𝔱𝔞𝔩𝔩𝔦𝔫𝔤 𝔉𝔞𝔠𝔢_ℜ𝔢𝔠𝔬𝔤𝔫𝔦𝔱𝔦𝔬𝔫
    !git clone https://github.com/renseeel/MX-4101-Group-7_Finals_Face_Recognition_Disney_Movies
    !pip install face_recognition
    %cd MX-4101-Group-7_Finals_Face_Recognition_Disney_Movies

### 🎬 𝔈𝔫𝔠𝔬𝔡𝔦𝔫𝔤 𝔓𝔯𝔬𝔣𝔦𝔩𝔢𝔰 𝔘𝔰𝔦𝔫𝔤 𝔎𝔫𝔬𝔴𝔫 𝔉𝔞𝔠𝔢 ℑ𝔪𝔞𝔤𝔢𝔰
<p align="justify"> 💻 This code is a Python code that performs face recognition on an image using the face_recognition library and the OpenCV. It loads an unknown image, detects faces, and compares their encodings with a set of known face encodings. It then draws rectangles around recognized faces, annotates them with corresponding names, and displays the modified image, showcasing the results of the face recognition process. </p>

👧🏻 For the face recognition of the Live Actors and Actresses of the Disney Movies Princesses utilized in this code for Known and Unknown identities intended for this activity:

    import face_recognition
    import numpy as np
    from google.colab.patches import cv2_imshow
    import cv2

    # Creating the encoding profiles
    face_1 = face_recognition.load_image_file("Ariel.jpg")
    face_1_encoding = face_recognition.face_encodings(face_1)[0]

    face_2 = face_recognition.load_image_file("Belle.jpg")
    face_2_encoding = face_recognition.face_encodings(face_2)[0]

    face_3 = face_recognition.load_image_file("Cinderella.jpg")
    face_3_encoding = face_recognition.face_encodings(face_3)[0]

    face_4 = face_recognition.load_image_file("Jasmine.jpg")
    face_4_encoding = face_recognition.face_encodings(face_4)[0]

    face_5 = face_recognition.load_image_file("Mulan.jpg")
    face_5_encoding = face_recognition.face_encodings(face_5)[0]

    known_face_encodings = [
                        face_1_encoding,
                        face_2_encoding,
                        face_3_encoding,
                        face_4_encoding,
                        face_5_encoding
    ]

    known_face_names = [
                    "Ariel",
                    "Belle",
                    "Cinderella",
                    "Jasmine",
                    "Mulan",
    ]

### 𝔘𝔰𝔦𝔫𝔤 𝔉𝔞𝔠𝔦𝔞𝔩 ℜ𝔢𝔠𝔬𝔤𝔫𝔦𝔱𝔦𝔬𝔫 𝔬𝔫 𝔏𝔦𝔳𝔢-𝔄𝔠𝔱𝔦𝔬𝔫 𝔇𝔦𝔰𝔫𝔢𝔶 𝔄𝔠𝔱𝔬𝔯𝔰 𝔞𝔫𝔡 𝔄𝔠𝔱𝔯𝔢𝔰𝔰𝔢𝔰
    file_name = " "
    unknown_image = face_recognition.load_image_file(file_name)
    unknown_image_to_draw = cv2.imread(file_name)

    face_locations = face_recognition.face_locations(unknown_image)
    face_encodings = face_recognition.face_encodings(unknown_image, face_locations)

    for (top,right, bottom, left), face_encoding in zip(face_locations, face_encodings):
        matches = face_recognition.compare_faces(known_face_encodings, face_encoding)

        name = "Unknown"

        face_distances = face_recognition.face_distance(known_face_encodings, face_encoding)
        best_match_index = np.argmin(face_distances)
        if matches[best_match_index]:
            name = known_face_names[best_match_index]
        cv2.rectangle(unknown_image_to_draw, (left, top), (right, bottom),(0,255,0),3)
        cv2.putText(unknown_image_to_draw,name, (left, top-20), cv2.FONT_HERSHEY_SIMPLEX,1,(0,0,255),2, cv2.LINE_AA)

    cv2_imshow(unknown_image_to_draw)

<h1 align="center"> 👸🏻 𝔇𝔦𝔰𝔫𝔢𝔶 𝔓𝔯𝔦𝔫𝔠𝔢𝔰𝔰𝔢𝔰 👸🏻 </h1>

![Disney Movies Princess](https://github.com/renseeel/MX-4101-Group-7_Finals_Face_Recognition_Disney_Movies/assets/92082602/24459688-3e89-48e1-99d1-074e68fb9650)


# <h1 align="center"> 𝔇𝔦𝔰𝔫𝔢𝔶 𝔓𝔯𝔦𝔫𝔠𝔢𝔰𝔰 | 𝔎𝔫𝔬𝔴𝔫 </h1>


### 🧜🏻‍♀️ 𝔄𝔯𝔦𝔢𝔩 

<p align="justify"> Ariel is a beloved fictional character and the protagonist of Disney's animated film "The Little Mermaid," released in 1989. She is a spirited and curious mermaid princess who dreams of exploring the world beyond the ocean and living among humans. Ariel's fascination with the human world leads her to make a deal with the sea witch Ursula to exchange her voice for legs, hoping to experience life on land and win the heart of Prince Eric. With her distinctive red hair and an adventurous spirit, Ariel captivated audiences with her determination, courage, and love for adventure. She remains one of Disney's most iconic and cherished princesses, known for her memorable songs and endearing personality.

💡 The outcome derived from employing the "Ar.jpg" image with the code for facial recognition is: 
</p>

<p align="center">
  <img src="https://github.com/renseeel/MX-4101-Group-7_Finals_Face_Recognition_Disney_Movies/assets/143622288/e66545dc-f757-4ba9-b917-19bf8d3d7151" alt="Ar with name">
</p>

### 🥀 𝔅𝔢𝔩𝔩𝔢 

<p align="justify"> Belle is another iconic Disney princess, known for her intelligence, kindness, and love of books. She is the central character in Disney's animated film "Beauty and the Beast," released in 1991. Belle is depicted as a smart, independent, and free-spirited young woman living in a small French village. Her love for reading and yearning for adventure set her apart from the conventional expectations of her provincial life.

Belle becomes entangled in a unique and heartwarming tale when she sacrifices herself to save her father, Maurice, from a terrifying Beast's castle. There, she discovers that the Beast is, in reality, a cursed prince trapped in a monstrous form due to his selfishness. Over time, Belle learns to see beyond the Beast's exterior and discovers the kindness and goodness within him.

💡 The outcome derived from employing the "Be.jpg" image with the code for facial recognition is: 
</p>

<p align="center">
  <img src="https://github.com/renseeel/MX-4101-Group-7_Finals_Face_Recognition_Disney_Movies/assets/143622288/7ae047c6-cb78-40b6-aef0-6afa0d72da2f" alt="Be with name">
</p>

### 🥿 ℭ𝔦𝔫𝔡𝔢𝔯𝔢𝔩𝔩𝔞

<p align="justify"> Cinderella is a classic Disney princess and the protagonist of Disney's animated film "Cinderella," released in 1950. Her story is one of enduring hope, resilience, and the transformative power of kindness. Cinderella, whose birth name is Ella, is portrayed as a gentle and kind-hearted young woman living with her wicked stepmother and stepsisters after her father's passing.

Living with her cruel stepfamily, she finds hope when her Fairy Godmother helps her attend a royal ball. There, she captures the heart of the Prince but must leave at midnight, leaving behind a glass slipper. The Prince searches for her, and when the slipper fits, Cinderella's life changes as she marries the Prince, embodying the belief that kindness triumphs over adversity in Disney's timeless tale.

💡 The outcome derived from employing the "Ci.jpg" image with the code for facial recognition is: 
</p>
    
<p align="center">
  <img src="https://github.com/renseeel/MX-4101-Group-7_Finals_Face_Recognition_Disney_Movies/assets/143622288/e415ae99-13df-4441-87a3-2509142cca66" alt="Ci with name">
</p>

### 🪔 𝔍𝔞𝔰𝔪𝔦𝔫𝔢

<p align="justify"> Jasmine is a Disney princess featured in the animated film "Aladdin," released in 1992. She is a headstrong and independent young woman, the daughter of the Sultan of Agrabah. Jasmine longs for freedom from the constraints of palace life and seeks to experience the world beyond its walls.

Jasmine is known for her courage, intelligence, and determination to shape her destiny, making her a beloved and empowering figure among Disney princesses. Her character challenges societal norms and stands for the idea that one should be free to pursue their dreams and find true love on their terms.

💡 The outcome derived from employing the "Ja.jpg" image with the code for facial recognition is: 
</p>

<p align="center">
  <img src="https://github.com/renseeel/MX-4101-Group-7_Finals_Face_Recognition_Disney_Movies/assets/143622288/57c48bd9-cd76-448e-9243-38e1f179da4d" alt="Ja with name">
</p>

### ⚔️ 𝔐𝔲𝔩𝔞𝔫

<p align="justify"> Mulan is a courageous and resourceful Disney character who stars in the animated film "Mulan," released in 1998. She is a brave young woman who defies tradition and societal expectations in order to protect her family and serve her country.

Throughout her journey, Mulan shows incredible bravery and loyalty, ultimately playing a pivotal role in saving China. Her story is one of self-discovery, empowerment, and the importance of being true to oneself, making her an inspiring and beloved Disney character admired for her resilience and courage.

💡 The outcome derived from employing the "Mu.jpg" image with the code for facial recognition is: 
</p>

<p align="center">
  <img src="https://github.com/renseeel/MX-4101-Group-7_Finals_Face_Recognition_Disney_Movies/assets/143622288/ab5e85e7-6743-47d9-874d-e3730093b343" alt="Mu with name">
</p>

# <h1 align="center"> 𝔇𝔦𝔰𝔫𝔢𝔶 𝔓𝔯𝔦𝔫𝔠𝔢𝔰𝔰 | 𝔘𝔫𝔨𝔫𝔬𝔴𝔫 </h1>


### ❓𝔘𝔫𝔨𝔫𝔬𝔴𝔫 𝔓𝔯𝔦𝔫𝔠𝔢𝔰𝔰 𝟏

💡 The outcome derived from employing the "An.jpg" image with the code for facial recognition is: 

<p align="center">
  <img src="https://github.com/renseeel/MX-4101-Group-7_Finals_Face_Recognition_Disney_Movies/assets/143622288/e52fa5fa-be83-416d-8962-43ee54ed8e9d" alt="U1">
</p>

### ❓𝔘𝔫𝔨𝔫𝔬𝔴𝔫 𝔓𝔯𝔦𝔫𝔠𝔢𝔰𝔰 𝟐

💡 The outcome derived from employing the "Me.jpg" image with the code for facial recognition is: 

<p align="center">
  <img src="https://github.com/renseeel/MX-4101-Group-7_Finals_Face_Recognition_Disney_Movies/assets/143622288/62f775d7-73a7-47df-ac6f-7ecbc7065d1f" alt="U2">
</p>

### ❓𝔘𝔫𝔨𝔫𝔬𝔴𝔫 𝔓𝔯𝔦𝔫𝔠𝔢𝔰𝔰 𝟑

💡 The outcome derived from employing the "Po.jpg" image with the code for facial recognition is: 

<p align="center">
  <img src="https://github.com/renseeel/MX-4101-Group-7_Finals_Face_Recognition_Disney_Movies/assets/143622288/68f6e667-742c-4b03-abc5-210d85155388" alt="U3">
</p>

### ❓𝔘𝔫𝔨𝔫𝔬𝔴𝔫 𝔓𝔯𝔦𝔫𝔠𝔢𝔰𝔰 𝟒

💡 The outcome derived from employing the "Mo.jpg" image with the code for facial recognition is: 

<p align="center">
  <img src="https://github.com/renseeel/MX-4101-Group-7_Finals_Face_Recognition_Disney_Movies/assets/143622288/56f89d12-8cb2-4d14-92cf-d6fdb2f193e6" alt="U4">
</p>

### ❓𝔘𝔫𝔨𝔫𝔬𝔴𝔫 𝔓𝔯𝔦𝔫𝔠𝔢𝔰𝔰 𝟓

💡 The outcome derived from employing the "Ki.jpg" image with the code for facial recognition is: 

<p align="center">
  <img src="https://github.com/renseeel/MX-4101-Group-7_Finals_Face_Recognition_Disney_Movies/assets/143622288/d3177af0-7cac-44f6-8409-6250b8e0b821" alt="U5">
</p>

### ❓𝔘𝔫𝔨𝔫𝔬𝔴𝔫 𝔓𝔯𝔦𝔫𝔠𝔢𝔰𝔰 𝟔

💡 The outcome derived from employing the "Sw.jpg" image with the code for facial recognition is: 

<p align="center">
  <img src="https://github.com/renseeel/MX-4101-Group-7_Finals_Face_Recognition_Disney_Movies/assets/143622288/9179b852-1951-4555-a2c5-18bbae5b2079" alt="U6">
</p>

### ❓𝔘𝔫𝔨𝔫𝔬𝔴𝔫 𝔓𝔯𝔦𝔫𝔠𝔢𝔰𝔰 𝟕 

💡 The outcome derived from employing the "Mi.jpg" image with the code for facial recognition is: 

<p align="center">
  <img src="https://github.com/renseeel/MX-4101-Group-7_Finals_Face_Recognition_Disney_Movies/assets/143622288/9ac026e7-3906-4693-b148-581b3a63da95" alt="U7">
</p>

### ❓𝔘𝔫𝔨𝔫𝔬𝔴𝔫 𝔓𝔯𝔦𝔫𝔠𝔢𝔰𝔰 𝟖 

💡 The outcome derived from employing the "Al.jpg" image with the code for facial recognition is: 

<p align="center">
  <img src="https://github.com/renseeel/MX-4101-Group-7_Finals_Face_Recognition_Disney_Movies/assets/143622288/92a73f82-8524-4ab9-a4d4-5c523817ba80" alt="U8">
</p>

### ❓𝔘𝔫𝔨𝔫𝔬𝔴𝔫 𝔓𝔯𝔦𝔫𝔠𝔢𝔰𝔰 𝟗 

💡 The outcome derived from employing the "Mk.jpg" image with the code for facial recognition is: 

<p align="center">
  <img src="https://github.com/renseeel/MX-4101-Group-7_Finals_Face_Recognition_Disney_Movies/assets/143622288/846150c0-9812-400b-8357-d50644e98ba1" alt="U9">
</p>

### ❓𝔘𝔫𝔨𝔫𝔬𝔴𝔫 𝔓𝔯𝔦𝔫𝔠𝔢𝔰𝔰 𝟏𝟎

💡 The outcome derived from employing the "Ri.jpg" image with the code for facial recognition is: 

<p align="center">
  <img src="https://github.com/renseeel/MX-4101-Group-7_Finals_Face_Recognition_Disney_Movies/assets/143622288/c9150224-e833-4e33-81d8-42564190178d" alt="U10">
</p>

## 🅢🅞🅤🅡🅒🅔
_https://disneyprincess.fandom.com/wiki/Live-Action_Disney_Princesses_
_https://www.cinemablend.com/movies/aladdins-mena-massoud-offers-update-on-the-live-action-sequel_
_https://www.imdb.com/news/ni64089839/_
_https://theadamscorner.wordpress.com/2015/08/17/beautyandthebeast-first-look-emma-watson-makes-gorgeous-debut-as-belle/comment-page-1/_
_https://www.wickedlocal.com/story/bulletin-tab/2015/03/13/movie-review-x2018-cinderella-x2019/35017558007/_
_https://www.pinterest.ph/pin/757167756088806791/visual-search/?x=16&y=16&w=532&h=1437_
_https://www.imdb.com/news/ni62170055/_
_https://www.pinterest.ph/pin/disney--508625351664238640/_





