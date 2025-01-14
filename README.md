# UEFA EURO 2020 (Mid Project BDMLPT0922) 
Bootcamp Mid-Project bdmlpt0922 by Jaime Vaquero

The repo has 3 main parts:

- Data cleaning
- API
- Streamlit app

## Overview
The data is from Kaggle and it has been cleaned before uploading it to Mongodb Atlas. An API has been created to connect with Mongodb Atlas and retreive data with GET requests. Last, I have used Streamlit to create an app to display interactive data.

To summarise: The data is stored on the cloud in Mongodb Atlas, we access the data via an API making GET requests to the API from the streamlit app. The streamlit app is the final interface that displays the data.

You can copy the repo and launch it locally.

Finally, however the project has been presented and have passed whith success the bootcamp requirements, there is more ahead to be done in order to achieve my own goals   You can find all the details below in the ***roadmap*** section.



## Launch the project locally

If you go to streamlit/data/get_data.py you will find the functions that are used to call the API and get the data for the streamlit app. If you look closely, all functions have an URL as the URL of the localhost created for the API. You can launch the project locally in order to make changes, the default port is ***localhost:8000*** but you must crete your own database and stablish the connections by changing the Database/mongodb.py file. Rememer to add and env.(and a .gitignore) file with the URL database-connection. 


To run the project locally, in your terminal use:

For the api(you must be in the right folder to execute it):
```
uvicorn main:app --reload

The command uvicorn main:app refers to:
      main: the file main.py (the Python "module").
      app: the object created inside of main.py with the line app = FastAPI().
      --reload: make the server restart after code changes. Only use for development.
```

Then, in a new terminal tab, laucnh the streamlit app(you must be in the right folder to execute it):

```
streamlit run main_st.py
```

## Data cleaning

The data used can be found in [Kaggle](https://www.kaggle.com/datasets/mcarujo/euro-cup-2020) on a dataset with data about the UEFA Euro Cup 2020. 

During the cleaning, the goal was create a new DataFrame with the data that will be use to deploy dashborads. In order to achive it, I had to homogenize the data and then throught pyhton create new columns with the metrics already calculated, so that later on the querys be easier to code. 

To access the data through the API, the data was stored in Mongodb Atlas due to for me it is better to work with mongo than with a relational database. After the data was cleaned, it was uploaded to MongoDB in a csv format.

Inside the data folder you can find the euro_csv.csv file we used to get the data. You can find all the cleaning process [here](https://github.com/Crypto-topo/mid_project/blob/mp1/data/Data_cleaning.ipynb)


## API

The API is used as the connection between Mongodb Atlas and the streamlit app. There are several endpoints to access the data. All the endpoints can be found at api/Routers/acceso.py [here](https://github.com/Crypto-topo/mid_project/blob/mp1/api/Routers/acceso.py). 

### API Reference

Addition with routers, there’s fastapi swagger provided by Fastapi🤯. You can get it by just adding “docs” after your “localhost” in url i.e. “http://localhost/docs”. You will get the below interface. You can play with it, this interface is divided with tags. Above we have given tags as parameter in routers, these fields has “get”, “post”, etc. request/responses. Depending on which functionality we want to test we can use those routers.


![image](https://user-images.githubusercontent.com/113199775/205621990-79cff9cd-6095-414e-8b98-5131f2b741cb.png)
![image](https://user-images.githubusercontent.com/113199775/205622035-0e8c48e7-06c3-4fa2-afb1-7a8bdbbf0d64.png)



## Streamlit

The streamlit app consists of a sidebar that works as a Menu to navigate throught metrics as shown in the image below:

![image](https://user-images.githubusercontent.com/113199775/205622929-91f8bdff-020b-4065-ab72-e583833b6826.png)

There are 4 metric clusters:
- Goals Data
![image](https://user-images.githubusercontent.com/113199775/205622519-2a2e03dd-06d3-4da8-bc27-99b8d629f136.png)

- Stage Data
![image](https://user-images.githubusercontent.com/113199775/205622593-39eaed00-d40b-4cbd-97e4-efa095c419e2.png)

- Shots Data
![image](https://user-images.githubusercontent.com/113199775/205622441-28f64bf6-7b1f-4e74-a674-6a5e24c17ccd.png)

- Fairplay Data
![image](https://user-images.githubusercontent.com/113199775/205622681-0829adc6-1f47-4c74-8687-dbd7df842707.png)



### Requirements:

- [API](https://github.com/Crypto-topo/mid_project/blob/mp1/api/requirements.txt)
- [DASHBOARD](https://github.com/Crypto-topo/mid_project/blob/mp1/streamlit/requirements.txt)


Uvicorn run:
```sh
  uvicorn api.main:app 
  ```
  This command is to run the API in our computer

Streamlit run:
```sh
  streamlit run main.py
  ```
  This command is to run the dashboard in our computer 
  
 ## Roadmap
 
 - [x] Limpiar base de datos
 - [x] Conectar con api
 - [x] Creacion de diferentes dashboards con streamlit
 - [ ] Añadir datos geoespaciales de los estadios a la db
 - [ ] Crear una dashboard con un mapa de los estadios en donde se jugo cada partido
 - [ ] Crear varias paginas con multiapp
 - [ ] Export to PDF
 - [ ] Empaquetar con Docker
 - [ ] Subir a Heroku
