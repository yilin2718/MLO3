# Week 2 - Reddit API EDA and Modeling
Welcome to your first assignment! This one is going to be a bit open ended and allow you to explore the Reddit API and a model zoo of your choice. In class we went over how to set up your Reddit API connection and do basic traversal of threads in subreddits of your choosing. We also took a look at HuggingFace (feel free to use HuggingFace again for this assignment). 

The next step is to put everything you did in class together and create a data pipeline for collecting Reddit data via the Reddit API, run basic analysis on the data, use or fine tune a two models, and then answer the questions at the end of this doc. 

So specifically, here is what we would like to see:
1. Create a Github repo for this project.
2. Make a notebook or Python program that scrapes data from your favorite subreddit(s).
3. Collect said data in whatever form you think necessary for utilizing or fine tuning a model from a model zoo. If fine tuning is not available or is too intensive to do right now, just use the out of the box model. 
4. Choose a model zoo and two models to test on.
5. Showcase in your notebook running inferences to show off an interesting/useful tie in with your scraped data.
6. For now, this data collection and model tuning/inferencing can all be static. Throughout the course we will be able to add layers to this to make our pipeline and service more complex.
7. Upon completion of this, answer the following questions:
  * Why did you choose this particular subreddit and model zoo combo?
  * How is this pipeline useful? (even if it is more "fun" than "business useful", explain why someone using this would care)
  * What are your ideas of how you could serve this publically as a service from a technical perspective?
  * With unlimited time and budget, what are some ways you could improve this pipeline and make it into a service?
8. Commit this to your repo and turn in your Github link through Canvas.

## Things to consider:
* Use `hugging_reddit.ipynb` from class to get you started. Updated complete version is in the code directory of this repo.
* If you want to explore other model zoo's (particularly any that you'll use for your capstone) you can do so and apply them here. Otherwise, just use HuggingFace!