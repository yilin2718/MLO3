{
 "cells": [
  {
   "cell_type": "markdown",
   "id": "4409b2e8",
   "metadata": {},
   "source": [
    "<p align = \"center\" draggable=”false” ><img src=\"https://user-images.githubusercontent.com/37101144/161836199-fdb0219d-0361-4988-bf26-48b0fad160a3.png\" \n",
    "     width=\"200px\"\n",
    "     height=\"auto\"/>\n",
    "</p>\n",
    "\n",
    "# Reddit and HuggingFace Stater Kit"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "8241138f",
   "metadata": {},
   "source": [
    "## ============= PART 1 =============\n",
    "The first part of this excercise is to figure out how to instantiate a Reddit API object using the [PRAW library](https://praw.readthedocs.io/en/stable/). This is a Python library that gives easy to understand interfaces to interact with the Reddit API.\n",
    "\n",
    "Your first task is to look through the [documentation here](https://praw.readthedocs.io/en/stable/code_overview/reddit_instance.html) and figure out how to instanstiate a Reddit instance. (hint: you only need to use `client_id`, `client_secret`, and `user_agent`)\n",
    "\n",
    "Make sure everyone in the group does this part! Follow the guide below on how to get your `client_id` and `client_secret`.\n",
    "\n",
    "### Steps for part 1:\n",
    "1. Pull the `FourthBrain/ML03` repo locally so you can start development.\n",
    "2. Open `reddit_and_huggingface.ipynb` and install the necessary packages for this lesson by running:\n",
    "\n",
    "    ```\n",
    "    cd code_student/Week_2\n",
    "    conda activate {your_virtual_environment_name}\n",
    "    pip install transformers praw torch torchvision torchaudio\n",
    "    ```\n",
    "\n",
    "3. Get your `client_id` and `client_secret` from Reddit by doing:\n",
    "\n",
    "* Make a Reddit account\n",
    "* Follow the steps in this screenshot which are the first steps from this [guide](https://towardsdatascience.com/how-to-use-the-reddit-api-in-python-5e05ddfd1e5c).\n",
    "\n",
    "![instructions to set up reddit api](../../images/reddit_get_access.JPG)\n",
    "\n",
    "* Create a `secrets.py` file and include the following:\n",
    "\n",
    "    ```\n",
    "    REDDIT_API_CLIENT_ID = \"\"\n",
    "    REDDIT_API_CLIENT_SECRET = \"\"\n",
    "    REDDIT_API_USER_AGENT = {can_be_any_string...for ex: \"marksbot\"}\n",
    "    ```\n",
    "\n",
    "* Put `secrets.py` in `Week_2` so you can easily import it\n",
    "\n",
    "4. Read the [documentation here](https://praw.readthedocs.io/en/stable/code_overview/reddit_instance.html) and try to figure out how to instanstiate a Reddit instance object. \n",
    "5. Lastly, once you have your Reddit instance object, figure out how to make a `subreddit` object for your favorite subreddit. (hint: look for `subreddit` in the documentation)\n",
    "6. If time permits, continue to browse the documentation to prep for the next part of this excercise which will be to get submissions from the subreddit of your choosing."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "24b10417",
   "metadata": {},
   "outputs": [],
   "source": [
    "import praw\n",
    "from transformers import pipeline\n",
    "import secrets\n",
    "\n",
    "reddit = praw.Reddit(\n",
    "    # YOUR CODE\n",
    ")\n",
    "\n",
    "subreddit = reddit.subreddit(#Your Subreddit)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "b13fd85d",
   "metadata": {},
   "source": [
    "## ============= PART 2 =============\n",
    "\n",
    "This next part you are going to figure out how to parse comments by using your `subreddit` instance object.\n",
    "\n",
    "### Todos for part 2:\n",
    "1. How do I find the top 10 posts of all time from your favorite subreddit(s)? (hint: look at [\"Obtain Submission Instances from a Subreddit\"](https://praw.readthedocs.io/en/stable/getting_started/quick_start.html))\n",
    "2. How do I parse comments from the post? (hint: look at [\"Obtain Submission Instances from a Subreddit\"](https://praw.readthedocs.io/en/stable/getting_started/quick_start.html))\n",
    "\n",
    "Put your scraped data into a list so you can use it in the next part. A good structure would be a list of lists where the inner list is one comment. (hint: you might need a DOUBLE nested FOR loop). This could take a minute or two once running."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "18aae563",
   "metadata": {},
   "outputs": [],
   "source": [
    "from praw.models import MoreComments\n",
    "\n",
    "# Get top 100 posts of all time and iterate over them putting all comments and replies into a flat list\n",
    "\n",
    "top_comments = []\n",
    "\n",
    "for submission in subreddit.top(limit=10):\n",
    "    for top_level_comment in submission.comments:\n",
    "        if isinstance(top_level_comment, MoreComments):\n",
    "                    continue\n",
    "        top_comments.append(top_level_comment.body)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "71e99ef6",
   "metadata": {},
   "source": [
    "## ============= PART 3 =============\n",
    "\n",
    "The last part is to somehow use the data you have scraped from Reddit to run a HuggingFace model inference. \n",
    "\n",
    "### Todos for part 3:\n",
    "\n",
    "Implement the [Sentiment Analysis](https://huggingface.co/docs/transformers/quicktour) Model. Do you see any potential downside to using the top level comment strategy in part 2?"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "7d9b0acb",
   "metadata": {},
   "outputs": [],
   "source": [
    "from transformers import pipeline\n",
    "\n",
    "# Your Code\n",
    "\n",
    "\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "56a07cfc",
   "metadata": {},
   "outputs": [],
   "source": [
    "def get_random_comment(conversations):\n",
    "    convo = random.choice(conversations)\n",
    "    comment = random.choice(convo)\n",
    "    return comment\n",
    "\n",
    "# Run sentiment analysis\n",
    "sentiment_query_sentence = get_random_comment(top_comments) # grabs a random comment from the comment and replies list\n",
    "sentiment = sentiment_model(sentiment_query_sentence) # \n",
    "print(f\"Sentiment test: {sentiment_query_sentence} === {sentiment}\")"
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3 (ipykernel)",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.9.7"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}
