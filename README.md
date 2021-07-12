# Federated learning using Genetic Algorithm
This is a demo project for applying the concepts of federated learning (FL) in Python using socket programming.
## Project Overview
In this project I tried to train the machine learning (ML) models using Federated Learning. The ML model is created using PyGAD, which is trained using the genetic algorithm (GA). 
## Motivation
Most of the data in the world are contained not publicly on servers, but on client-side devices and sources (i.e. mobile phones, edge devices). Typically, users don’t end up directly sharing their data anywhere outside their devices. And if they do, there’s no guarantee of privacy. <br>
Federated Learning (FL) is a new paradigm for building machine learning (ML) models that keeps user data private. In this way, ML models are typically trained on data that’s not been collected and stored in a centralized server. In fact, the data is decentralized and scattered across clients. Through this project, I'll apply the concepts of FL in Python to build a demonstration of how a system like this might work.
## Data Collection
The data is taken from UCI Machine Learning Repository https://archive.ics.uci.edu/ml/datasets/bank+marketing (bank-additional-full.csv).<br>
**Features**
1 - age (numeric)
2 - job : type of job (categorical: 'admin.','blue-collar','entrepreneur','housemaid','management','retired','self-employed','services','student','technician','unemployed','unknown')
3 - marital : marital status (categorical: 'divorced','married','single','unknown'; note: 'divorced' means divorced or widowed)
4 - education (categorical: 'basic.4y','basic.6y','basic.9y','high.school','illiterate','professional.course','university.degree','unknown')
5 - default: has credit in default? (categorical: 'no','yes','unknown')
6 - housing: has housing loan? (categorical: 'no','yes','unknown')
7 - loan: has personal loan? (categorical: 'no','yes','unknown')
_italics_ related with the last contact of the current campaign: _italics_
8 - contact: contact communication type (categorical: 'cellular','telephone')
9 - month: last contact month of year (categorical: 'jan', 'feb', 'mar', ..., 'nov', 'dec')
10 - day_of_week: last contact day of the week (categorical: 'mon','tue','wed','thu','fri')
11 - duration: last contact duration, in seconds (numeric). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no'). Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model. 
_italics_ other attributes: _italics_
12 - campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)
13 - pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted)
14 - previous: number of contacts performed before this campaign and for this client (numeric)
15 - poutcome: outcome of the previous marketing campaign (categorical: 'failure','nonexistent','success')
_italics_ social and economic context attributes: _italics_
16 - emp.var.rate: employment variation rate - quarterly indicator (numeric)
17 - cons.price.idx: consumer price index - monthly indicator (numeric)
18 - cons.conf.idx: consumer confidence index - monthly indicator (numeric)
19 - euribor3m: euribor 3 month rate - daily indicator (numeric)
20 - nr.employed: number of employees - quarterly indicator (numeric)

**Output variable (desired target)**
21 - y - has the client subscribed a term deposit? (binary: 'yes','no')
## Data Preperation
To train a model using FL, the training data is distributed across the clients. The server itself does not have any training data, just test data to assess the model received from the clients. <br>
For the execution purpose of this project the bank data was horizontally splitted into three equal parts ( rows each). Out of these three dataset parts, one was kept at server side (as test data) and the remaining two parts were kept at two different client locations to which server has not access at all.
## How it works
The interaction between client and server is implemented by using programming sockets with the socket Python library. The client-server architecture will handle multiple clients simultaneously. Using PyGAD, I’ll also create a feed-forward neural network (FFNN), also using a genetic algorithm (GA).
 Using FL, a model can be created directly out of such private data. 
