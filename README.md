# Reddit-DS-Project
**Scraping, illustrating and predicting data from reddit for a school assignment.**   
So, I have a writing assignment for my class that asks me to analyze and write an analysis about a virtual community of my choice, so I did this analysis to gain a little more insights for my assignment.

# A few guiding questions


# The Analysis
So first I scraped the top 1000 hot post of the r/datascience with some feature like:
  - day_created: the day the post was posted, it in UNIX time so I'll convert it latter
  - title: the title of the post
  - score: the number of upvotes
  - upvote_ratio: the ratio of upvotes/votes
  - num_comments: number of comments
  - author: the author name
  - flair: like the tag of the post, ex: education, fun, meme,etc
  
![image](https://user-images.githubusercontent.com/88282475/196001973-ed81e88e-6a69-4417-9d1f-e73d34f86274.png)

### Problem 1: I want to see which flair has the highest mean score (or recieve the most positive feedback from the community)
So, I clean the data and visualize the mean high score of different flairs:
![image](https://user-images.githubusercontent.com/88282475/196002138-3d8069a2-fbc2-488a-af50-401bdd34f267.png)
> It seems like most community members really like **Fun/Trivia** (I do, too). The next favorite things is **Meta**. Since I'll don't really get what Meta is about, I'll
> choose education to analyze deeper instead  

Before I go, I decided to graph all three mean just to see if there any correlation:
![image](https://user-images.githubusercontent.com/88282475/196003611-61f6959a-90aa-4be1-a5fe-15c05c381db7.png)  

And print out a dataframe just for sure:   

![image](https://user-images.githubusercontent.com/88282475/196003815-744aef88-d7ca-4918-b27c-ab103f3d188b.png)

And so now I'll move a little deeper into education
## Education:
### Problem 1: 
Before I dig into education flair, I actually took a look at the median score, upvote ratio and number of comments of all the flair:  

![image](https://user-images.githubusercontent.com/88282475/196004454-cc3d95e5-d6eb-4d9d-b1bf-41979c67b85e.png)     

And I realize that education was not doing that great, that mean most of the score was really low, with some exception, or outliners  

![image](https://user-images.githubusercontent.com/88282475/196004503-7fc34574-f68a-4c95-aa24-963e4a4ee0c0.png)    
  
So I try to find some of those outliners:    

![image](https://user-images.githubusercontent.com/88282475/196004527-0469f3be-6f26-4779-84f1-f5d059c56414.png)    

It seems like most of the education posts have score below 40, with an exception of 1077. So of course, I search for it:
  
![image](https://user-images.githubusercontent.com/88282475/196004709-935d970e-5910-41ae-8dfa-68f626123a5f.png)  

It seems like there is some error with the url, but I manage to find it base on title and author.  
Can't believe such simple post can be that exceptional, and now I'm on my way to become hot redditor (and I'll put this post to my writing assignment, I guess):  

![image](https://user-images.githubusercontent.com/88282475/196004780-3dd6619e-394d-4576-a1bf-8196972a90f8.png)   

I decided to look at the trend of the score overtime, just to see if there anything interesting, but other than the peek, the line of score of education flair is pretty much flat:
![image](https://user-images.githubusercontent.com/88282475/196006100-5df6ce6e-3f8d-4fa8-8055-f51a2d532dcb.png)

## Fun/Trivia:
















.
