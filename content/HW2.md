# Homework 2 - Intro to ml5 and Image Classification

You probably came here thinking that I was going to say that AI doesn't work. Well unfortunately that was clickbait and I came up with it after I made this post. In reality, AI works but under very specific circumstances. In the realm of image classification, AI needs certain conditions to be able to recognize things successfully. Unfortunately for me, my apartment is the perfect example of what can cause image classification to fail.

### ImageNet

Although I had trouble accessing imagenet's explore page, I did find a working version of it on internet archive so I was able to get a bit of a look into what is available and what it covers. I was very surprised at how comprehensive it felt at first glance. For instance I opened up the "artifact" tab and found a large number of nested synsets relating to this topic. It is surprising how well they organized this information.

I do wonder why there exist certain things that don't necessarily make sense within the artifact category such as "lemon, stinker". What is that? What is a "lemon, stinker"? I wish there was an easy way to find out.

![weird synsets](/images/hw2-weird-synsets.png)

I think that it is possible that a majority of these images were collected ethically, but I do believe that issues surrounding copyright ownership and royalty could've played a part in the curation of these images which may lead to bias.

### Image Classification testing

I tried running the ml5 image classifier on some items in my room. Unfortunately since I have a dark background I think I may have affected my results for darker items. But on the other hand, my black headphones weren't identified at all even when I gave a white background (my pillow). When I used my pillow as a background it chose to recognize the pillow instead of the headphones.

| Item                | Result                                                                                                                                 |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Headphones          | Didn't recognize. Said it was a mailbag                                                                                                |
| Pen                 | Recognized! Though the accuracy was low due to the background, it correctly said ballpoint pen                                         |
| Scissors            | Didn't recognize. Said it was a "hook, claw"                                                                                           |
| Book                | Didn't recognize. For some reason it was convinced that this was a harp with nearly 90% accuracy.                                      |
| Tissue box          | Didn't recognize. Thought that it was a hammer head shark when I held it close to the camera and a candle when I held it further away. |
| Water bottle        | Kinda got it? Said that it was a "cocktail shaker" which i guess is better than nothing...                                             |
| Keys                | Didn't recognize. Thought that it was an electric guitar.                                                                              |
| AA Battery          | Didn't recognize. Thought that it was a joystick.                                                                                      |
| Tape measure        | Didn't recognize. Thought that it was a "syringe" or a "lighter".                                                                      |
| Graphing Calculator | Kinda recognized. It said that it was either a hand held phone or a hand held computer which is close enough for me.                   |

![correct result!](/images/hw2-semiworking-code-1.png)

![weird result](/images/hw2-harp-1.png)

I feel that the fact that my background was not white really affected my results with this. MobileNet only recognized about 3/10 of the objects I presented and was wildly off for the rest with varying degrees of confidence. Different backgrounds affect results in different ways and that is an issue if we want to be able to use image classification in many scenarios in the future. People who don't have access to light colored backgrounds bay be at a disadvantage compared to those with light colored backgrounds at hand. Scale also is very important. For instance when I used the tissue box, it registered different things when close up and far away.

I believe we are still a ways to go with this technology, but if we provide useful data containing images of different scales/colors/backgrounds then we will be a bit closer to being able to have this work for everyone.
