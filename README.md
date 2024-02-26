# Bangalore_House_Price_Prediction

This project series provides a comprehensive guide on creating a real estate price prediction website. It starts by utilizing the Bangalore home prices dataset from Kaggle.com to develop a predictive model using Scikit-learn and linear regression. The subsequent steps involve building a Python Flask server to deploy the model for handling HTTP requests. The final component is crafting a website using HTML, CSS, and JavaScript, allowing users to input home square footage, number of bedrooms, etc., which triggers a call to the Python Flask server for retrieving the predicted price.

Throughout the project, various data science concepts are explored, including data loading and cleaning, outlier detection and removal, feature engineering, dimensionality reduction, hyperparameter tuning using techniques like GridSearchCV, and k-fold cross-validation. The project utilizes a range of tools and technologies:

1. Python
2. Numpy and Pandas for data manipulation and cleaning
3. Matplotlib for data visualization
4. Scikit-learn for model development
4. IDEs such as Jupyter Notebook, Visual Studio Code, and PyCharm
5. Python Flask for creating the HTTP server
6. HTML/CSS/JavaScript for building the user interface.

# Deploy this app to cloud (AWS EC2)
1. Create EC2 instance using amazon console, also in security group add a rule to allow HTTP incoming traffic
2. Now connect to your instance using a command like this,
   'ssh -i "C:\Users\prans\.ssh" ubuntu@ec2-3-71-51-28.eu-central-1.compute.amazonaws.com'

Amazon ec2 instance link 
http://ec2-54-93-37-199.eu-central-1.compute.amazonaws.com/ ubuntu@
