---
layout: post
title: Blocitoff
thumbnail-path: "img/blocflix.png"
short-description: A self-disruptive To-do list.

---

{:.center}
![]({{ site.baseurl }}/img/blocflix.png)

## Explanation

Kele Gem allows Bloc students to access Bloc's API with ease by eliminating the need to use cURL.

## Problem
making GET and POST requests with cURL can be long and repetitive. How can a user be able to retrieve current user information, get a list of their mentors availability ,see Bloc roadmaps and checkpoints? All in a time consuming way.

## Solution
With the use of gems like HTTParty and JSON a user is able to make GET and POST requests to access the API .
<br><br>
After successfully initialized a user with email and password. The user is able to retrieve the authentication token to access the Bloc API .

Kele methods like `get me ` allows the user to retrieve current user data.

{% highlight ruby %}
def get_me
    response = self.class.get('/users/me', headers: { "authorization" => @auth_token })
    @current_user = JSON.parse(response.body)
end
{% endhighlight  %}

* JSON gem was added as a run type dependency to allow the user of the json.parse method to convert the user data to a Ruby rash .


`get_mentor_availability` retrieves the current users mentors availability by providing mentors_id to the method .
{% highlight ruby %}
def get_mentor_availability(mentor_id)
  response = self.class.get("/mentors/#{mentor_id}/student_availability" , headers: {"authorization" => @auth_token})
  body = JSON.parse(response.body)
end

{% endhighlight  %}

`create_submission` which allows current user to submit a completed checkpoint by passing the required arguments.
{% highlight ruby %}
  def create_submission(assignment_branch, assignment_commit_link, checkpoint_id, comment, user_id)
    response = self.class.post('/checkpoint_submissions', body: {assignment_branch: assignment_branch, assignment_commit_link: assignment_commit_link, checkpoint_id: checkpoint_id, comment: comment, enrollment_id: user_id}, headers: {"authorization" => @auth_token})

    puts response
  end
{% endhighlight  %}
## Results

Kele easily call GET and POST requests to the Bloc API at a more efficient way and by converting its JSON responce into a Ruby hash.


## Conclusion

This project have me a greater understanding of how to build an API based gem. Used for the first time HTTParty to  make GET and POST requests with correct headers and body.
