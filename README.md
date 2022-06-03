# mobileNetv2SSD-ForestSettings
mobileNet based SSD setting for Korea Forest Detection

### 1. Requirement program setup

```bash
# python env setting
conda create -n mobileSSD python=3.9 pip -y
conda activate mobileSSD
pip install --ignore-installed --upgrade tensorflow==2.5.0
conda install -c conda-forge cudatoolkit=11.2 cudnn=8.1.0
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$CONDA_PREFIX/lib/
python3 -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"
```

```bash
mkdir models && cd Tensorflow
git clone https://github.com/tensorflow/models
cd ../
```

```bash
sudo apt install protobuf-compiler -y
pip install cython
```

```bash
git clone https://github.com/cocodataset/cocoapi.git
cd cocoapi/PythonAPI
make
cp -r pycocotools ../../Tensorflow/models/research/
```

```bash
cp object_detection/packages/tf2/setup.py .
python -m pip install --use-feature=2020-resolver .
```

```bash
# From within TensorFlow/models/research/
python object_detection/builders/model_builder_tf2_test.py
conda install ipykernel -y
```

### 2. Sample Execution

- [sample code](./sample.ipynb)

### 3. Training Sample Dataset & Test

- download dataset sample : https://public.roboflow.com/object-detection/mask-wearing/4/download

```bash
mkdir Tensorflow/workspace && mkdir Tensorflow/workspace/mask_detection
cd Tensorflow/workspace/mask_detection
mkdir annotations
mkdir exported-models
mkdir -p images/test
mkdir -p images/train
mkdir models
mkdir pre-trained-models
```

- [use sample dataset train code](./sample_train.ipynb)

### 4. Training Custom Dataset & Test



### Reference

- https://tensorflow-object-detection-api-tutorial.readthedocs.io/en/latest/
- https://github.com/tensorflow/models