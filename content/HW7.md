# Homework 7 - Recurrent Neural Networks

A lot of the issues with working with text data come from the diversity and sources of the content used as training data. It is up to the developer of the model to train the model with data that uses a diverse array of sources. However how can we make sure that these sources don't end up marginalizing people in some way? I don't know if there is an exact solution yet, but limiting sources that have harmful language could be a good start when it comes to this.

### My Sketch

For my sketch I wanted to experiment with something similar to a project I did in high school. When I took AP Computer Science Principles, I made a "poetry generator" that was fed a text document or a url and it made "poetry" from the text of that site. It didn't really do much poetry generation however, since it was all random, but it did structure things similar to poems so it looked nice.

One of the texts I used for testing was Finnegan's Wake by James Joyce. This book, if you have no clue what it is, is essentially full or gibberish (or if you are fan it is full of the most genius text ever). I mean the first sentence is:

> riverrun, past Eve and Adam’s, from swerve of shore to bend
> of bay, brings us by a commodius vicus of recirculation back to
> Howth Castle and Environs.

I thought it would be interesting to experiment with markov chains for this text for that reason. I mean, if the text I generate is going to end up being gibberish, I might as well go all in.

To get the source text I found a pdf online and copied and pasted it all in a text file. After that I did a very rudimentary find and replace with regex (I'm no regex expert, but this did the trick for selecting all the text I wanted `/^\d+$/g`. I probably could've added `\n` after `\d+` to get the whole line but it is too late for that) to get rid of the page numbers that were copied over.

Because the find and replace left some extra lines I figured that I should do some more cleanup in the text to get rid of all those empty newlines. For that reason I ran `.filter(Boolean)` on the `lines` array on line 18. This essentially says, is the text truthy or falsy? Typically if a text has any characters in it, it is truthy so all the empty lines get removed for that reason.

### My results

Interestingly, my results all started with "river" or something similar. Here are a few examples

Example 1:

> rivering from than businessy an oldup with to
>
> make it we week of Man’s show brace to rounder Zigzag tumbleth suck up peepestretched shes by Ghostyle of a matchin Toot might ever countainstreepetter die. Soon in pressing to don’t gluepan kennyatime — a sliderivates. Vote windown jonq

Example 2:

> rives off foot givinger Erie.
>
> Tiern Aposter the wooins fi vestill be gave and milabioling mickinarpot becausine tried of blish pads on they holth. Connaur-Jaggaggles, this whuler’s verith bespoof old you can short of Missroad was a nigh. And her their has from their turpite arian

Example 3:

> rivereams with a teethster piourishers, Mr Connie, sings and him), upon the Frieze
>
> where’s nefeel to line your bank of Ivaun sod to knowledge of all quick with lible for a jettyplumes, a cowship a lashed, the softly. If shem blieve it is crying longs are the swample free! — Hun! —

as I said it is pretty much just formatted gibberish, but it is still interesting to read some of these since they do have at least a little bit of structure to their chaos.
