# RSU-E
Realtime self updating encryption method.

This encryption method is directly connected with the server's date and time, and the random alphabet sequences which stored on the server side.

Three different parameters are the most important:

*Date & Time*

*Randomly generated alphabets*

*Hidden Number*

The encryption starts when the user input received by server. Current time when the input arrives to server will be saved.
That date and time will be used for selecting the Hidden Number, and encryption of the day-month-year.
While this happening, server is automatically generating random sequenced alphabets in X time.
Or just for an idea, server can regenerate the alphabets while user input received.

# Simple flowchart of the method

![e1](https://i.imgur.com/l0Lwbzs.jpg)

The key point here is the Hidden Number, which can be calculated by;

Hidden Number = Current Server Time(ms) (mod10)

Later we will use the Hidden Number for 'space character' in encrypted text.

# Server side alphabet generation

![e2](https://i.imgur.com/9G3lkjd.jpg)

As we can see from the flowchart of the server-side alphabet generation process, for every X time, server will generate another random alphabet sequences. For each message sent from user to server, it will be selected randomly.

For example, when user sent the message 'this is a very very bad encryption method', server-side will randomly select the 4th alphabet generated. If the user will send another message after X hours called 'wow, it's still too bad.', server will randomly select the 7th alphabet from the right table.

This will be the alphabet selection section.


# Using the Hidden Number to encrypt the text

Let's assume user sent the message at 2020/02/22 14:22:53.427

From the Hidden Number calculation, 427(mod10)= 7

Our Hidden Number will be = 7.

And again let's use the 4th alphabet generated in the server-side alphabet generation flowchart.

Let's assume the users message is: Hello All.

We are going to skip the Hidden Number while counting the each letter on the 4th alphabet.

![e3](https://i.imgur.com/Ec74hhr.jpg)

Now we are starting to find all of the letters position on the alphabet the 4th.

Users message was: Hello All.

For each letter in the words or sentences, we will count and find the position.

Let's start with the letter 'H' from Hello.

We are starting with zero, and skip the hidden number and the Hidden Number + 10. Like; 0,1,2,3,4,5,6,7(this normally is the Y letter, but we count one more time again so the Y letter is 8th character, E normally will be 17th but we skip hidden+10, so it's 18th). 

And with the counting of the alphabet, 'H' letter will be the 21th character.

'E' letter would be the 18th.

'L' letter would be the 6th.

'O' letter would be the 5th.

'A' letter would be the 10th.

'L' letter is still 6th.

So our 'Hello' word is 21,18,6,6,5 according to our 4th alphabet.

And 'All' word is 10,6,6.

Now we should tell our program to recognize the letters correctly.

If we didn't show these are seperated numbers, it will give false results.

So here is the Hidden Number part.

Our program adds Hidden Numbers in the middle of the letters and words.

For usage in words letters, we use hidden character for 2 or 3 times.

For space characters, Hidden Number's usage will be random.

Let's continue on our example;

We already have the each letters results above.

Our final encrypted text will be like this;

21771877767767757777771077767776

![e3](https://i.imgur.com/v7sYqwb.jpg)

As you can see from the upper image, Red Lined parts are letter spaces and green line is word space which can have 0 to infinite amount of Hidden Numbers except 2 and 3(Those are using for letter spacing).
