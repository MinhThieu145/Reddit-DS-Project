# Reddit-DS-Project
**Scraping, illustrating and predicting data from reddit for a school assignment.**   
So, I have a writing assignment for my class that asks me to analyze and write an analysis about a virtual community of my choice, so I did this analysis to gain a little more insights for my assignment.

#Links:
- Notebook: (kaggle notebook with dataset already included): https://www.kaggle.com/code/th1402/reddit-notebook
- Dataset: https://www.kaggle.com/datasets/th1402/data-science-reddit-community

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
Trivia is the one with the highest mean score, so I first see its distribution:  

![image](https://user-images.githubusercontent.com/88282475/196007286-f97ecd1a-1c79-4cc1-b419-f4e583cfda35.png)

The majority of posts still have score below 500, although the distribution varied more compare to education flair  
  
Next, I move on to plot the distribution of upvote ratio:
![image](https://user-images.githubusercontent.com/88282475/196007647-56b0e6ca-ee66-460a-88c9-e6300ee976aa.png)  
  
It's overwhelmly positive, with 40% of posts have only upvote. 

I move on to graph the relationship between score and the number of comments
![image](https://user-images.githubusercontent.com/88282475/196009562-2dda59b7-65b9-4e8e-ad0e-8b430e4190e6.png)
  
It's can be seen that they follow a certain pattern, eventhough the comment is lower than the score (for sure, since it's much easier to click upvote, compare to actually comment. Here is a table to confirm their relation:
  
  ![image](https://user-images.githubusercontent.com/88282475/196009617-5e2eae14-b868-4670-86b1-57fd0ab6ba09.png)
  
## Authors and their impact
After playing with the top 1000 posts, I wonder whether the number of comments and score in general have anything to do with the author. So I scrap another dataset, this time with authors and some of their information, it looks like this:
![image](https://user-images.githubusercontent.com/88282475/196009691-1bacce1b-d92d-43fb-95da-5ea686d7134e.png)  
  
The number of karma: represent how liked the authors are within the community
  
First I try the relation between columns in general:
![image](https://user-images.githubusercontent.com/88282475/196009718-b5c3e730-d081-4c31-8423-e5098fbccb6a.png)
  
It seems like the score and number of comments and upvote_ratio have little relation with the author, whether he's a mod or gold member, or the number of karma.
Eventhough the number of people who are gold membership or mod is quite small:
![image](https://user-images.githubusercontent.com/88282475/196009827-dbddbc5c-90d5-48d4-9b4c-e968716be2aa.png)

### Models
Finally, I implemented a XGBoost model to see whether it can predict the score, base on the give information or not. It seems like XGBoost model has overfit, since I have an extremely high accuracy score. 
![image](https://user-images.githubusercontent.com/88282475/196009889-999afe99-2382-4043-8997-d7293d174f03.png)
  
Here are the results:
![image](https://user-images.githubusercontent.com/88282475/196010638-78a1dd0f-837c-4a0a-addd-692366ba4da6.png)

Eventhough it seems like there is little connection between the gold member status and score, it seems to be the most importance feature to determine score:
![image](https://user-images.githubusercontent.com/88282475/196010806-28c68797-3d44-4ea4-8ddc-ec1fe07a5686.png)
