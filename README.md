<img src="https://github.com/redhox/labeling_mlflow/blob/main/Capture%20d%E2%80%99%C3%A9cran%20du%202024-04-15%2016-51-53.png?raw=true"></img><br>
local python/serveur-mlflow/bucket-s3
<h1>mlflow en server distant</h1>
local python/serveur-mlflow/bucket-s3
<h2>serveur-mlflow</h2>

        python -m venv .venv
        source .venv/bin/activate
        pip install mlflow
        pip install boto3
        pip install awscli
        export MLFLOW_S3_ENDPOINT_URL=http://1.2.3.4:9000/
        export AWS_ACCESS_KEY_ID=
        export AWS_SECRET_ACCESS_KEY=
        mlflow server -h 0.0.0.0 --default-artifact-root s3://artifacts --backend-store-uri sqlite:///mlflow.db --app-name basic-auth

<h2>conexion et train</h2>
.env

    AWS_ACCESS_KEY_ID=
    AWS_SECRET_ACCESS_KEY=
    MLFLOW_S3_ENDPOINT_URL=http://1.2.3.4:9000/
    MLFLOW_TRACKING_URI=http://1.2.3.4:5000/
    MLFLOW_TRACKING_USERNAME=admin
    MLFLOW_TRACKING_PASSWORD=password
    

app.py
pip install mlflow ultralytics boto3 awscli setuptools python-dotenv
    
    import os
    from dotenv import dotenv_values
    import mlflow
    from ultralytics import YOLO
    
variable

    project_name= "" #experiment
    run_name=""
    model_size="yolov8s.pt" #yolov8n.pt/yolov8s.pt/yolov8m.pt
    data_yaml_path=""
    epochs=
    image_sise=
    patience=
start mlflow experimante

    mlflow.set_tracking_uri(temp["MLFLOW_TRACKING_URI"])
    mlflow.set_experiment(project_name)
    with mlflow.start_run(run_name=run_name):
        model = YOLO(model_size)
        results  = model.train(project=project_name,name=run_name,data=data_yaml_path, epochs=epochs,imgsz=image_sise)
    



