# Kidnapping at Yrgo

This is an SQLite game where you have to find whoever kidnapped a student at Yrgo.

## HOW TO PLAY

- Clone the repository.
- Open the ```database.db``` file with SQLite.
- ENJOY!

<img src="https://i.imgur.com/OBNFYkI.png" width="50%">


## SOLUTION

<details>
    <summary>Click here to see the step-by-step solution</summary>

## Step 1:

SELECT * FROM police_reports where date = "13/12/2019" AND location = "Lärdomsgatan" AND type = "kidnapping";

Info: The security footage shows that there are two witnesses. One of the witnesses had brown hair and she was about 190cm tall. The other witness had red hair and was about 165-170cm tall. He was between 28-32 years old.

## Step 2.1 (Witness 1):

SELECT * FROM people WHERE hair_color = "Brown" AND height = 190;

Info: 
ID: 670	
Name: Betsy Alva Soplin	
Yrgo-ID: 37-0256627	
Gender: Female	
Age: 25	
Height: 190	
Hair color: Brown

SELECT * FROM people
INNER JOIN interviews
ON people.id = interviews.person_id
WHERE id = 670;

I saw a masked man walk into the school and grab a person and then leaving the school. 

## Step 2.2 (Witness 2):

SELECT * FROM people WHERE hair_color = "Red" AND height > 160 AND height < 170 AND age > 27 AND age < 33;

Info:
(Dominic Kersch)

SELECT * FROM people
INNER JOIN interviews
ON people.id = interviews.person_id
WHERE hair_color = "Red" AND height > 160 AND height < 170 AND age > 27 AND age < 33;

The man who grabbed the person had brown hair and was about 25-30 years old. I saw that he checked into the school at 2:36 PM.

## Step 3:

SELECT * FROM people
INNER JOIN yrgo_check_in
ON people.yrgo_id = yrgo_check_in.yrgo_id;

Info:
ID: 615
Name: Viktor Puke
Yrgo-ID: 57-8982240

## Step 4:

SELECT * FROM interviews WHERE person_id = 615;

Info: 
It wasn't me! I was sick that day. I lent my key tag the day before to my classmate. I'm not gonna snitch him out but he's a very short man. Just above 100cm short. He's 26 years old. That's it! I've said enough!

## Step 5.1:

SELECT * FROM people
INNER JOIN interviews
ON people.id = interviews.person_id
WHERE height > 100 AND height < 110 AND age = 26;

Info:
Thomas Sönnerstam, Marcus Augustsson, Janela Brayfield

## Step 5.2:

Case Thomas:

SELECT * FROM facebook_events WHERE event_date = "13/12/2019";

Thomas was in fact at a Foo Fighters concert.

Case Marcus Augustsson:

Vincent Kaliber took the key tag.

Case Janela Brayfield:

She was out of town.

## Step 6:

SELECT * FROM people
INNER JOIN interviews
ON people.id = interviews.person_id
WHERE name = "Vincent Klaiber";

Info:
Alright, alright, fine! It was me. I thought that by taking a student's key tag that I would never be the suspect. I can't believe my own student ratted me out! 


</details>


## CREATED BY

- Thomas Sönnerstam
- Andreas Lindberg