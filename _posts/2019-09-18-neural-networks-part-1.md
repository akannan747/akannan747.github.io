---
layout: page
title:  "Neural Networks (part 1)"
date:   2019-09-18 12:00:00 -0400
categories: blog
mathjax: true
comments: true
---




<span class="image center"><img src="/assets/galaxy_brain.jpg" alt="" /></span>
<!--more-->
<h2 class="align-center">An Introduction to Neural Networks</h2>
<p>
  Oftentimes I marvel at how truly amazing the human brain is. You can hear a snippet of a song you used to like when you were a child and almost instantly recognize it and begin humming the rest of the song. Easy enough, but if you ask a computer to do the same thing, you begin to realize the complexity of the task. Let's write some pseudocode that might allow a computer to achieve that level of recognition:
</p>
  
    def find_song(song_snippet)
      for each song that you have ever heard
        if song contains song_snippet
          play song
      if you made it here you can't find it 
    
<p>
  In fact, the above might be overly simplifying the problem at hand, since comparing two songs is itself not an easy task. But our brain can do this sort of thing in a fraction of a second. That all being said, lookup is a relatively easy task in which computers usually outperform humans. Where the human brain really shines over computers is our ability to make decisions.
</p>
<p>
  Let's say that there's a yacht party happening this coming Friday night. To go, or not to go, that is the question. To make this decision, there's a number of factors that we're going to need to know. First; this yacht party is our big chance at a promotion. If our boss shows, we're definitely going to be able to show him all the hard work we put in during the last year and bring home the big bucks. We hate the rain. So we should probably check the weather forecast and make sure that our yacht party isn't going to rain on us. The last thing we have to worry about is Tanner. He wears the freshest clothes, eats at the chillest restaurants, and hangs out with the hottest dudes. And he bullied us in high school. If Tanner shows up, he might make us look bad in front of our boss. 
</p>
<p>
  Now that we have all of this information, we can make a decision. This promotion is pretty important to us, so our boss being at this yacht party plays a bigger role in our choice than either Tanner or the weather. We're willing to tolerate Tanner if it means a promotion, and we're willing to get drenched in the rain for it too. But Tanner AND the rain would be too much of a dampener on our day; that's the one situation in which we'd skip the yacht. So we know how we would make our choice. How can we get a computer to replicate that? 
</p>
<p>
  We could start by assigning a value to each factor showing how much weight they have in our final decision. Let's give Tanner a weight of -3, the weather a weight of -3, and our boss a weight of 5.

  $$
      W_{Tanner} = -3 \\
      W_{weather} = -3 \\
      W_{boss} = 5 \\
  $$

  This makes sense, because the presence of our boss has a bigger positive weight on our decision than the negative weights of Tanner's presence or bad weather. Then let's define three binary variables; x, y, and z for Tanner, the weather, and our boss respectively. 
</p>
<p>
$$\begin{array}{cc}
  \{ & 
    \begin{array}{cc}
      x = 0 & \text{if Tanner doesn't show up} \\
      x = 1 & \text{if Tanner does show up} \\
    \end{array}
\end{array}$$

$$\begin{array}{cc}
  \{ & 
    \begin{array}{cc}
      y = 0 & \text{if it doesn't rain} \\
      y = 1 & \text{if it rains} \\
    \end{array}
\end{array}$$

$$\begin{array}{cc}
  \{ & 
    \begin{array}{cc}
      z = 0 & \text{if your boss doesn't come} \\
      z = 1 & \text{if your boss does come} \\
    \end{array}
\end{array}$$
</p>
<p>
  Now to make our decision we multiply the inputs x, y, z with their relative weights. If the result is less than 0, we stay home and skip the party. If the result is greater than 0, it's party time! You should be able to prove to yourself pretty quickly that if our boss shows up, it would require both Tanner and the rain to stop you from your promotion. 
</p>
<p>
  $$\text{decision} = X * W_{Tanner} + Y * W_{weather} + Z * W_{boss}$$
  $$\text{decision} = 1 * -3 + 1 * -3 + 1 * 5 = -1$$
</p>
<p>
  That's just what we wanted! What's even more cool is that we just created an artificial neuron called a perceptron. More about those in a future blog post. The important thing is that we just created a function that does exactly what we wanted it to do; make decisions based on relevant factors, in a way similar to how a human might make them. This neuron is our first step towards neural networks.
</p>