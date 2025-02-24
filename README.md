# 📊 Analysis of Community Notes Data from X

This project uses community notes [data](https://x.com/i/communitynotes/download-data) published by X to analyze its effectiveness in curbing potentially harmful/misleading information online.  
🔗 **Link to project page:** [Community Notes Analysis](https://hazel-gandhi.github.io/community-notes-analysis/)



## 📂 Repo Guide
- **`cn_analysis.ipynb`:** Contains all my analysis for the charts used in the piece.  
- **`data` folder:** This folder has all the `.csv` files that power the charts.  



## 🎯 Aim
- As a former fact-checker, I was interested in analyzing how the Community Notes model was working in tackling disinformation on X, especially now that other platforms like Meta aim to incorporate a similar model for their platforms.  
- Learn how to query a database and ask targeted questions.  
- I also wanted to try my hand at analyzing large files in pandas (Each file has 1.6 million rows representing each community note ever written).  



## 🔍 Findings
- Most community notes (about 1 million) are stuck in the "Needs More Ratings" status, meaning that potentially misleading posts go unchecked by the community.  
- Even in cases where a note does appear under a misleading post, its views are negligible compared to the views of the misleading post.  
- About 850,000 notes were stuck in "Needs More Ratings" for more than a month, some even exceeding the 1 and 2-year mark.  
- A contributor I spoke to revealed that they do not have much confidence in the Community Notes model, especially since X has let go of its Trust and Safety teams.  

## 🧪 Data Collection and Analysis Process
- I downloaded the Community Notes data made publicly available by X on February 11, 2025.  
- Started by looking at all notes ever written since this project began in 2021 and categorized all misleading posts into sub-categories like factual errors, out of context, satire, manipulated media, and so on.  

### ⏲️ To calculate how long a note remained in the "Needs More Ratings" status:
- Converted the creation time of notes in milliseconds to datetime format in pandas.  
- Filtered notes tagged as "Needs More Ratings" from `currentStatus` column.  
- Set current time as February 11, 2025.  
- Calculated difference of days between creation date of note and current date.  
- Cleaned the column to remove exact hours and minutes and keep only days.  
- Filtered for notes stuck in the status for 30+ days.  
- Set up bins of 1 month, 1-6 months, 6 months-1 year, 1-2 years, and 2+ years to `groupby`.  
- Joined `notesHistory.tsv` with `notes.tsv` since that had the `tweetIds` I wanted to count.  
- Counted all notes that appeared in each bin.  

## 🚀 New Skills Acquired/Improved Approaches
-Using Adobe Illustrator to make Tree Maps
- Complex data analysis of large data files in pandas.  
- Merging two large data files and ensuring the accuracy of the analysis by double-checking methodology, columns selected, and formulae applied.  
- Doing complex `groupby`s and slicing and dicing data according to my queries.  

## 🔮 Things I Would Change/Scope for Further Research
- I would have liked to analyze how long it took for an average community note to be displayed under a misleading post, but X's algorithm ensures that as more contributors rate a note, its status keeps changing and hence it was tough to determine which column to consider for this question.  
- Speaking to an expert who has already analyzed the data and conducting a more politically-focused analysis (e.g., How well Community Notes combats misinformation post-Trump).  
- One of the files includes details about `userEnrollment.tsv`, which will be interesting to look at and understand how contributors behave in this space.  
