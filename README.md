# awesome-ml-model
This project contains an example of how to use a DVC data registry to import training data. 

Initialize the project with:
```bash
poetry install
```

Initialize DVC with the following command:
```bash
poetry run dvc init
```

Then we need to configure the remote storage.

```bash
poetry run dvc remote add -d storage /Users/marco/Documents/image_data_registry_dvc_storage
```

## Add a new processed dataset

Import the processed day image data into the data
```bash
poetry run dvc import https://github.com/marcopaspuel/image-data-registry-dvc \
                      processed/01_image_dataset/data/outputs/day_images \
                      -o data/training
```

Import the processed night image data into the data
```bash
poetry run dvc import https://github.com/marcopaspuel/image-data-registry-dvc \
                      processed/01_image_dataset/data/outputs/night_images \
                      -o data/training
```

## Update processed dataset

Create a new branch
```bash
git checkout -b update-processed-dataset
```
Update the datasets 

```bash
poetry run dvc update data/training/day_images.dvc
```

```bash
poetry run dvc update data/training/night_images.dvc
```

Commit and push
```bash
git push
poetry run dvc push
```
