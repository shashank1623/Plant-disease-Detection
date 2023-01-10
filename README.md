# Plant-disease-Detection

## Setup for Python:
1. Install Python ([Setup instructions](https://wiki.python.org/moin/BeginnersGuide))
2. Make a Virtual Env.
3. Install Python packages

```
pip3 install -r api/requirements.txt
```
3. Install Tensorflow Serving ([Setup instructions](https://www.tensorflow.org/tfx/serving/setup))

## Setup for ReactJS

1. Install Nodejs ([Setup instructions](https://nodejs.org/en/download/package-manager/))
2. Install NPM ([Setup instructions](https://www.npmjs.com/get-npm))
3. Install dependencies

```bash
cd frontend
npm install --from-lock-json
npm audit fix
```
4. Copy `.env.example` as `.env`.

5. Change API url in `.env`.

## Training the Model
Note :- If have gpu based machine then run it otherwise it will take more than a day for model building . or you can reduce the size of data from every folder then train the model.
1. Download the data from [kaggle](https://www.kaggle.com/arjuntejaswi/plant-village).
2. Keep all the data in a seprate folder in a project directory. 
3. Run Jupyter Notebook in Browser.

```bash
jupyter notebook
```

4. Open `training/potato-disease-training.ipynb` in Jupyter Notebook.
5. In cell #2, update the path to dataset.
6. Run all the Cells one by one.
7. Copy the model generated and save it with the version number in the `models` folder.

### Using FastAPI

1. Get inside `api` folder

```bash
cd api
```

2. Run the FastAPI Server using uvicorn

```bash
uvicorn main:app --reload --host 0.0.0.0
```

3. Your API is now running at `0.0.0.0:8000`

### Using FastAPI & TF Serve

1. Get inside `api` folder

```bash
cd api
```

2. Copy the `models.config.example` as `models.config` and update the paths in file.
3. Run the TF Serve (Update config file path below)

```bash
docker run -t --rm -p 8501:8501 -v C:/Code/potato-disease-classification:/potato-disease-classification tensorflow/serving --rest_api_port=8501 --model_config_file=/potato-disease-classification/models.config
```

4. Run the FastAPI Server using uvicorn
   For this you can directly run it from your main.py or main-tf-serving.py using pycharm run option (as shown in the video tutorial)
   OR you can run it from command prompt as shown below,

```bash
uvicorn main-tf-serving:app --reload --host 0.0.0.0
```

5. Your API is now running at `0.0.0.0:8000`

## Running the Frontend

1. Get inside `api` folder

```bash
cd frontend
```

2. Copy the `.env.example` as `.env` and update `REACT_APP_API_URL` to API URL if needed.
3. Run the frontend

```bash
npm run start
```
<hr>
Datasets credits:- https://www.kaggle.com/arjuntejaswi/plant-village <br>
Contact Us:- shashankbhardwaj2030@gmai.com









