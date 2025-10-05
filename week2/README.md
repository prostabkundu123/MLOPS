# Week-2: IRIS + DVC on GCS

- DVC remote: gs://21f1001797-assignment-5-sept-2025/dvcstore
- Tracked: `data/` and `model/` (DecisionTree)
- Versions: `v1` (data.zip) and `v2` (new-data.zip)
- Demo: `git checkout v1 && dvc checkout` ⇄ `git checkout v2 && dvc checkout`

## Reproduce
gsutil cp gs://21f1001797-assignment-5-sept-2025/datasets/data.zip .
unzip -q data.zip && rm data.zip
dvc add data
python train.py
dvc add model --force
dvc push
git tag v1

gsutil cp gs://21f1001797-assignment-5-sept-2025/datasets/new-data.zip .
unzip -q new-data.zip && rm new-data.zip
dvc add data --force
python train.py
dvc add model --force
dvc push
git tag v2
