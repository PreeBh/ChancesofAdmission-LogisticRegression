Logistic Regression 

Problem statement - to predict the chances of admission on the basis of score of GRE, GPA and Rank.


# -*- coding: utf-8 -*-
"""
Created on Mon Mar 23 20:18:26 2020

@author: hp
"""

import os 
import pandas as pd 
print(os.getcwd())
os.chdir("C:\\Users\\hp\\Downloads\\")
print(os.getcwd())
dataset=pd.read_excel("2 Logistic Regression.xlsx",header=0)
print(dataset.head())

# Divide variables in 2 parts DV(Target) and IV( Feature Variable)

feature=['GRE','GPA','Rank']
x=dataset[feature]
y=dataset.Admit

## Take Care of Underfitting and Overfitting(Split data)
from sklearn.model_selection import train_test_split
x_train,x_test,y_train,y_test=train_test_split(x,y,test_size=0.25,random_state=0)
''' We need to pass 3 parameters in train_test_split
1.Features (IV)
2.Target (DV)
3.Test_size

Optional: random_state - To split data randomly in 2 parts
'''
from sklearn.linear_model import LogisticRegression
logreg=LogisticRegression()
logreg.fit(x_train,y_train) # fit data with model
y_predict=(logreg.predict(x_test))

print(y_predict)

