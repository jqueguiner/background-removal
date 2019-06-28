# Portrait Segmentation using Tensorflow

This script removes the background from an input image. You can read more about segmentation [here](http://colab.research.google.com/github/tensorflow/models/blob/master/research/deeplab/deeplab_demo.ipynb)

### Setup
The script setup.sh downloads the trained model and sets it up so that the seg.py script can understand. 
>	./setup.sh

### Running the script
Go ahead and use the script as specified below, to execute fast but lower accuracy model:
>	python3 seg.py sample.jpg sample.png 

For better accuracy, albiet a slower approach, go ahead and try :
>	python3 seg.py sample.jpg sample.png 1

### Dependencies
>	tensorflow, PIL

### Sample Result
Input: 
![alt text](https://github.com/callmesusheel/image-background-removal/raw/master/sample.jpg "Input")

Output: 
![alt text](https://github.com/callmesusheel/image-background-removal/raw/master/sample_bgremoved.png "Output")


#### Docker for API

You can build and run the docker using the following process:

Cloning
```console
git clone https://github.com/jqueguiner/background-removal.git background-removal
```

Building Docker
```console
cd background-removal && docker build -t background-removal -f Dockerfile-api .
```

Running Docker
```console
echo "http://$(curl ifconfig.io):5000" && docker run -p 5000:5000 -d background-removal
```

Calling the API for image detection
```console
curl -X POST "http://MY_SUPER_API_IP:5000/process" -H "accept: image/png" -H "Content-Type: application/json" -d '{"url":"https://i.ibb.co/W0JpjrY/input.jpg"}' --output no-background-image.png
```
