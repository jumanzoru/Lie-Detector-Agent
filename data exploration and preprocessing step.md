#  data exploration and preprocessing step

## We are using the dataset politifact_clean_binarized.csv

---

There are 11188 number of observations in this training set. We are going to assume words appear at most once every observation. There are exceptions but due to the set being so large, this error can be neglected. The fist 11087 observations are going to be the training data of this project and the last 100 be the validation set.
The truthfulness of each data, as the owner of this data set states, are evaluated by the Politifact.com team, hence it is realiable.

---

There are 4 columns in politifact.csv: statement, source, link, veracity.

* statement - statement made by celebrity or politician.
* source - can be a person, but not necessarily.
* link - URL of affirmation.
* veracity - degree of truthfulness given by the Politifact.com team.

There are 6305 lies and 4783 truth in total in the training set, which is the first 11087 data in this dataset.

For this dataset specifically,veracity is binarized (into just truths and lies), with 1 being truth and 0 being lie.
For this project, only the first colum and fourth column are needed.
