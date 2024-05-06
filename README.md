# Ex.No: 13 Machine Learning – Mini Project
# DATE: 22/4/2024
# REGISTER NUMBER : 212221220034
# AIM:
To write a program to train the classifier for Diabetes.
# ALGORITHM:
```
Step 1: Import packages. 
Step 2: Get the data. 
Step 3: Split the data. 
Step 4: Scale the data. 
Step 5: Instantiate model. 
Step 6: Create Gradio Function. 
Step 7: Print Result.
```
# PROGRAM:
```
import numpy as np
import pandas as pd
pip install gradio
pip install typing-extensions --upgrade
pip install --upgrade typing
pip install typing-extensions --upgrade
import gradio as gr
data = pd.read_csv('/content/diabetes.csv')
data.head()
print(data.columns)
x = data.drop(['Outcome'], axis=1)
y = data['Outcome']
print(x[:5])
#split data
from sklearn.model_selection import train_test_split

x_train, x_test, y_train, y_test= train_test_split(x,y)

from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
x_train_scaled = scaler.fit_transform(x_train)
x_test_scaled = scaler.fit_transform(x_test)

from sklearn.neural_network import MLPClassifier
model = MLPClassifier(max_iter=1000, alpha=1)
model.fit(x_train, y_train)
print("Model Accuracy on training set:", model.score(x_train, y_train))
print("Model Accuracy on Test Set:", model.score(x_test, y_test))

def diabetes(Pregnancies, Glucose, Blood_Pressure, SkinThickness, Insulin, BMI,Diabetes_Pedigree, Age):
    x = np.array([Pregnancies,Glucose,Blood_Pressure,SkinThickness,Insulin,BMI,Diabetes_Pedigree,Age])
    prediction = model.predict(x.reshape(1, -1))
    if(prediction==0):
      return "NO"
    else:
      return "YES"

outputs = gr.Textbox()
app = gr.Interface(fn=diabetes, inputs=['number','number','number','number','number','number','number','number'], outputs=outputs,description="Detection of Diabeties")
app.launch(share=True)

# OUTPUT:
![image](https://github.com/Naadira/Ex.No13_AI_miniproject/assets/128135126/7a7e5650-caa2-4d7c-833c-378295214ffa)
![image](https://github.com/Naadira/Ex.No13_AI_miniproject/assets/128135126/1057e1da-3a7f-4531-9bb6-84d9eee0072e)
![image](https://github.com/Naadira/Ex.No13_AI_miniproject/assets/128135126/96a82277-a4ce-46f6-a609-0405bd5b4183)
```
# RESULT:
Thus the system was trained successfully and the prediction was carried out.





