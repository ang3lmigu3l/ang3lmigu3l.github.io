---
layout: post
title: Blocitoff
thumbnail-path: "img/blocitoff.png"
short-description: A self-disruptive To-do list.

---

{:.center}
![]({{ site.baseurl }}/img/blocitoff.png)

## Explanation

Blocitoff Is a simple To-do list app using Ruby on Rails. It allows users to create lists of things they need to complete, with a self-disruptive that functions as way to help you complete your goals in 7 days or less.

## Problem

To-do lists are easily to make but harder to get them done when it comes to it. The "Ill just do it later" attitude always seems to arise when it comes to finishing off something we have put asside but Blocitoff hopes to help by implementing its self-disruptive feature.

## Solution

The self-disruptive feature in Blocitoff is implemented  to  automatically delete to-do item that weren't completed within 7 days of it being created. It is implemented by creating a rake task like so :


{% highlight ruby %}
desc "Delete Expired Items (7 days)"
  task delete_items: :environment do
    Item.where("created_at <= ?", Time.now - 7.days).destroy_all
end
{% endhighlight  %}



## Results

As a result Blocitoff allows the user to create and manage their to-do items as well as encouraging the user to complete them before they expire. Blocitoff was my first project going solo and it allowed me to follow a User Story tool to complete the tasks that was ask for.

## Conclusion

Bloccitoff was a good introduction to rake tasks that could be run manually or automatically. I also playing around with some Ajax to implement a more smooth experience when marking to-do items as complete.
