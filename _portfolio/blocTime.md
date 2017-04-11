---
layout: post
title: BlocJam
thumbnail-path: "img/bloctime.png"
short-description: A Pomodoro style time manager.

---

{:.center}
![]({{ site.baseurl }}/img/bloctime.png)

## Explanation

BlocTime is a Pomodoro timer that will count down from 25 minutes to zero, with 5 minute breaks (on prompts), then after four work sessions, users will have the option for a 30 minute break. Also included is a working task list to stay on top of TODO items while using the pomodoro technique.

## Problem

A challenge I came across was being able to display a break timer after 4 completed assignments. It would always display it after the 4th assignment was completed and the break after that was completed as well.


## Solution

The issue was resolved when i realized that i was putting the if statement in the wrong location in the countdown method .
{% highlight javascript %}
scope.countdown = function() {
   if(scope.workTime <= 0){
       stopTimer();
       scope.timerRunning = false;
       //if countdown reaches 0  and is on break , set time to 25m (work)
       if (scope.onBreak) {
           console.log("currently working");
           setWork();
       } else {
           scope.completedSessions += 1;
           console.log(scope.completedSessions);
           // if 4 work sessions are completed and not on break set time to long break
           if (scope.completedSessions === 4) {
               setLongBreak();
           } else {
               setBreak();
           };

       };
   }else{
    //countdown
    scope.workTime--;
    }
};
{% endhighlight  %}

## Conclusion

When used appropriately, BlocTime is an effective, useful way to sustain a work-break balance.
