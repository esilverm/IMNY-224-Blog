# Homework 3 - Transfer Learning

### The Treachery of Images

In image classification researchers pair images and labels to give computers the ability to recognize things within images. From the computers perspective, it knows nothing about what an image is or what an objects are. These are all merely representations of bits that the computer has been told is an image or a string of text. Because of this, the job of preparing datasets is a very important one. Providing a dataset with poor representation of the objects or even with poor labeling can lead to issues of mislabeling and can be potentially very harmful.

A while back I watched a youtube video of somebody [training face recognition AI to recognize K-Pop stars](https://www.youtube.com/watch?v=7W6uSF98b6s). About halfway through the video she tries running the model on a fan cam of BTS member Jungkook and despite having trained the model on a ton of well labeled input (thanks to fan cams), the BTS member's name didn't pop up in any of the results. In fact, it wasn't even a top result (the top result being "unidentified"). Upon further inspection the youtuber finds out that the library that she used has a hard time recognizing non-european individuals.

I kinda went on a tangent and now I am realizing that the example I gave only marginally relates to the main topic of this since it deals moreso with model creation than transfer learning. However the message is the same. If we don't properly label the input data we provide to our machine learning models or provide our data in such a way that it creates bias, it is harmful and unethical.

### My own Transfer Learning Application

When looking for a topic to make my model on, I found a couple datasets on Kaggle pertaining to face mask detection. I had planned to use one of these to train as samples, but many of them were not sorted properly or were poorly made. So of course the next best thing was to make a model using only images of myself!

To do this I made three different labels:

| Wearing Mask                        | Not Wearing Mask                      | Incorrectly Wearing Mask                          |
| ----------------------------------- | ------------------------------------- | ------------------------------------------------- |
| ![mask on](/images/hw3-mask-on.png) | ![mask off](/images/hw3-mask-off.png) | ![mask incorrect](/images/hw3-incorrect-mask.png) |

Thinking about it now, I probably could've done a couple incorrect mask ones where I used my shirt.

After doing this I created a [new p5.js project](https://editor.p5js.org/esilverm/sketches/QwZloMg_v) using the teachable machine starter code. After introducing the newly trained model, things worked out pretty well but I knew I could take things further.

As a student who needs to wear his mask inside during class, I feel that I could use this for good. Basically if I am not wearing my mask or happen to be wearing it incorrectly, I would appreciate knowing if that is the case so I can correct it.

To make this alert, I found a free mp3 file with an alarm sound effect and added a few lines of code to play a sound if I am not wearing a mask (i.e. if the label is not "wearing mask").

```js
if (label.toLowerCase() !== "wearing mask") {
  if (label !== prevLabel && !sound.isPlaying()) {
    sound.play();
  }
} else {
  if (prevLabel.toLowerCase() !== "wearing mask" && sound.isPlaying()) {
    sound.stop();
  }
}
```

Because I didn't want this to play over and over again since this code runs frequently (I don't typically use p5.js so this was more so a safety thing), I added a check to make sure that it doesn't play the sound multiple times if we have the same label many times in a row.

Of course since this is a long audio, I don't want to have an issue where I hear is after I put my mask on, so I added a check to stop the sound when I am wearing my mask properly.

Jokes aside, I feel this was a fun way to play with transfer learning with a real like use case.

Let's hope the alarm won't go off next time I'm in class!
