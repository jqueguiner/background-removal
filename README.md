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


Image Background Removal API will remove the background of the provided image using Deep Learning and especially image segmentation.

read this paper to learn more about this technic:
[Removing Background with Semantic Segmentation
Based on Ensemble Learning ](https://eudl.eu/pdf/10.4108/eai.21-6-2018.2276586)

```
@INPROCEEDINGS{10.4108/eai.21-6-2018.2276586,
    author={Junhong Xu and Hanqing Guo and Aron Kageza and Shaoen Wu and Saeed AlQarni},
    title={Removing Background with Semantic Segmentation Based on Ensemble Learning},
    proceedings={11th EAI International Conference on Mobile Multimedia Communications},
    publisher={EAI},
    proceedings_a={MOBIMEDIA},
    year={2018},
    month={9},
    keywords={deep learning image segmentation background removal},
    doi={10.4108/eai.21-6-2018.2276586}
}
```

- - -

EXAMPLE  
![output](https://i.ibb.co/1JK1j7b/example.png)

- - -

INPUT

``` json
{
  "url": "https://i.ibb.co/W0JpjrY/input.jpg"
}
```

- - -
EXECUTION
```bash
curl -X POST "https://api-market-place.ai.ovh.net/image-background-removal/process" -H "accept: image/png" -H "X-OVH-Api-Key: XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX" -H "Content-Type: application/json" -d '{"url":"https://i.ibb.co/W0JpjrY/input.jpg"}' --output no-background-image.png
```

- - -

OUTPUT
Binary output image.
![output](https://i.ibb.co/vkrFnq4/output.png)

please refer to swagger documentation for further technical details: [swagger documentation](https://market-place.ai.ovh.net/#!/apis/fc91fdd4-14f6-4bc9-91fd-d414f67bc9dc/pages/5f533287-9e4d-48b6-9332-879e4dd8b666)

