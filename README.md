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
1. Create EC2 instance using amazon console, also in security group add a rule to allow HTTP incoming traffic.
2. Now connect to your instance using a command like the below
   ```
   ssh -i "C:\Users\prans\.ssh" ubuntu@ec2-3-71-51-28.eu-central-1.compute.amazonaws.com
   ```
3. nginx setup
   1. Install nginx on EC2 instance using these commands
      ```
      sudo apt-get update
      sudo apt-get install nginx
      ```

   2. Above will install nginx as well as run it Check status of nginx using
      ```
      sudo service nginx status
      ```

   3. Here are the commands to start/stop/restart nginx
      ```
      sudo service nginx start
      sudon  service nginx stop
      sudo service nginx restart
      ```
   4. Now when you load cloud url in browser you will see a message saying "welcome to nginx" This means your nginx is setup and running.

4. Now you need to copy all your code to EC2 instance. You can do this either using git or copy files using winscp. We will use winscp. You can download winscp from here: https://winscp.net/eng/download.php

5. Once you connect to EC2 instance from winscp (instruction in a youtube video), you can now copy all code files into /home/ubuntu/ folder. The full path of your root folder is now: /home/ubuntu/BangloreHomePrices


6. After copying code on EC2 server now we can point nginx to load our property website by default. For below steps,
Create this file /etc/nginx/sites-available/bhp.conf. The file content looks like this,

   1. Create this file /etc/nginx/sites-available/bhp.conf. The file content looks like this,
      ```
      server {
         listen 80;
            server_name bhp;
            root /home/ubuntu/BangloreHomePrices/client;
            index app.html;
            location /api/ {
                  rewrite ^/api(.*) $1 break;
                  proxy_pass http://127.0.0.1:5000;
               }
         }
      ```
   2. Create symlink for this file in /etc/nginx/sites-enabled by running this command,
      ```
      sudo ln -v -s /etc/nginx/sites-available/bhp.conf
      ```

   3. Remove symlink for default file in /etc/nginx/sites-enabled directory,
      ```
      sudo unlink default
      ```
   4. Restart nginx,
      ```
      sudo service nginx restart
      ```

7. Now install python packages and start flask server
```
sudo apt-get install python3-pip
sudo pip3 install -r /home/ubuntu/BangloreHomePrices/server/requirements.txt
python3 /home/ubuntu/BangloreHomePrices/client/server.py
```

After executing the previous command, you'll receive a prompt indicating that the server is operational on port 5000. Next, simply open your cloud URL in a web browser. In my case, it was http://ec2-54-93-37-199.eu-central-1.compute.amazonaws.com/. This will lead you to a fully functional website running in a production cloud environment.



