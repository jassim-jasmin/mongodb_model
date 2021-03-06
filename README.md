# Mongodb ML Model Managing

Mongodb can store machine learning binary models. Using this package ml models can be versioned.
Also, possible to modify existing version. When the version is available the package use the local model.
If packages are not available in the local storage, it will download.


Requires python 3.8+

Mongodb: 

# Prediction Model management
- Models are stored in mongodb
- Config setting `mongodb.model` for settings
- Uploading model
    -
    - Model name in db has 3 part
        - First part project name
        - Second part model name (should be unique)
        - Third version number
    - If model name exist in db
        - Delete it automatically
        - Insert new model
    
- Downloading model
    -
    - If file exist in the local, file will be reused, discard the downloading
    - File will be saved in `/ml/model/modele_name/version`
    
- Adding new model
    -
    - Create a class name in config file
        - Format
            - `model.class_name`
            - Required attributes
                - `name`
                - `version`
    
- Installation
    -
     `pip install mongodb-ml-models`
- Usage
    -
    - Importing package
      -
      `from mongodb_ml_models import ManageModel`
      - ManageModel.get_model()
      - ManageModel.upload_model()
      - ManageModel.get_model_versions()
    - upload_model(binary_model, model_class)
        - model_class is the reference name in config file for mapping
        - Model will be saved in mongodb
        - Model will be saved in local path, ml/model/model_name/version (model name and model version should mention in config)
    - get_model(model_class)
        - Check for local path (ml/model/model_name/version)
        - If not available then download from db
    - get_model_versions(model_class)
        - It lists out all the available versions
    
