# Lie-Detector-Agent
## Project Abstract Milestone1

## Introduction
This project aims to classify input statements as either truthful or deceptive based on the words presented. Using a dataset from Kaggle [Truth Detection/Deception Detection/Lie Detection.*Dataset* (2022, January 12). Kaggle.] (https://www.kaggle.com/datasets/thesergiu/truth-detectiondeception-detectionlie-detection) that contains labeled political statements (for now, we might change the data set as we later on), we develop a probabilistic agent to determine the likelihood of a statement being a lie. The agent calculates conditional probabilities for words given the truthfulness of statements and applies Bayes' Theorem to determine *P(L|W*)*, the probability of a statement being a lie given its words. Statements with all words unseen from training are flagged as unknown, and returned a failure statement requesting for another input.

---

* **P**erformance measure: what words are in the input statement and what words are in the training data
* **E**nvironment: Only able to see the input statement and the training data.
* **A**ctuators: the input cell and output cell.
* **S**ensors: the input cell.
This is a goal based model, with the only goal to find the probability of lie, and return a output based on that value. This is a memory based model. It needs to look at the training data everytime it makes a decision.


## Method
The variable *L∈*{0,1} denotes whether a statement is a lie or not. True and mostly true are projected to *L*=1, while all others (Half-True, Mostly False, False, Pants on Fire!) are all projected as *L*=0.
The variable *𝑊𝑖∈*{0,1} represents the presence of a specific word in the statement.
For this model, the conditional probability for a word *𝑊𝑖* given *L*=*l* is defined as:
*𝑃(𝑊𝑖=1∣L=l)* = # of statements of type containing word *𝑊𝑖* / # of statements of type *l*
Also, suppose that *𝑃(L=1)* = # of lie statements / # of total statements
Also, suppose that *𝑃(Wi=1)* = # of statements that contained *Wi* / # of total statements
Let *𝑊** be the input statement, and let *𝑊i* be the word of the input statement at location *i*.
For example, if the words *𝑊2* and *𝑊4* are given, then *W\**={*𝑊2*=1,*𝑊4*=1}.


## Objective
Given *𝑊\**, determine whether the statement is more likely to be a lie or the truth, that is: find *P(L|W*)* and compare against threshold 0.5
For each word within the input statement *𝑊\**, check *P(Wi)*. If any *Wi* has a probability of 0, remove that word from our input string. We will not consider the ones that our agent has never seen before. 
If all *Wi* are never trained on, then return an exception statement “Huh, I don’t know about that. Maybe try something more political?”
Calculate *P(Wi|L)* for all words within *W**, 
Calculate *P(L)*
Calculate *P(W\*|L)*
Calculate *P(W\*|notL)*
Calculate *P_L_given_W** with the above information
If *P_L_given_W\** less than 0.5, return “Truth”. Else return “Lie!”


## Future Feature Expansions
For future improvements, the agent will have an additional feature that checks with the user whether the current guess is correct or not. If the user replies no, then the agent will adjust the probabilities by lowering or raising the probabilities of the valid words from the input. That is, change *P(Wi|L)* for all valid words *Wi*. If yes, then the agent will do nothing because this means that the current probabilities are good.


# WARNING!
To run the agent, you will need to download the LieDetector.ipynb file and the politifact_clean_binarized.csv file in the SAME directory. Use google collab or VScode to open LieDetector.ipynb and run the cells. Don't use jupyter notebook because for some reason jupyter notebook takes ages to load the csv file. If you are using google collab, you will need to drag the csv file to the "file" location in google collab and overwrite the file location when reading it.


## Contributors
* Tom Tang
* Guan Huang-Chen
* Xueheng Zhou
* Jefferson Umanzor-Urrutia
* [TheSergiu (dataset owner)](https://www.kaggle.com/thesergiu)
