# What is this?

This is a pretrained PyTorch-Model based on YoloV5 that allows identifying most of the stuff that flies around in the skies that are often misinterpreted as UFOs.

Input: an Image (or video, depending on your implementation).

Output: List of Bounding Boxes, that is, a list of coordinates, categories it detects something as and how certain the network is that this category.

![Example](example.jpg)

# How to prepare your environment

This guide is for Debian-Linux only. 

## Preparation

The following snippet will prepare your environment (install, Python, PyTorch, ...), so you can simply use this model:

```console
sudo apt-get install python3 python3-pip 
python3 -m pip install --upgrade pip
pip3 install virtualenv
python3 -m venv ~/.yolo_env
source ~/.yolo_env/bin/activate
git clone --depth 1 https://github.com/ultralytics/yolov5.git
cd yolov5
pip3 install -r requirements.txt
```

Now you can use `source ~/.yolo_env/bin/activate` to load this environment before loading the main script with `python3 example.py`.

## Explanation of the results

### `result.pandas().xywh[0]`:

```
       xcenter     ycenter       width      height  confidence  class    name
0   668.862244  626.564819  586.275146  768.257690    0.497301     45  sprite
1  1448.861938  710.136047  135.020264  298.230469    0.458381     45  sprite
2  1122.084961  520.964966  278.182434  440.907013    0.336716     45  sprite
```

Each line (except the first one) is one bounding box. The `xcenter` is the absolute position of the center on the X-Axis on the image, the ycenter the vertical center (see image). `width` and `height` are (obviously) the width and height of the bounding box. `confidence` is "how sure" the network is (see it as a score of similiarity to other images the network has been trained on in the same category). `class` is the number of the category, and `name` the name of the category.

![Bounding Box Format](bbox_format.jpg)

(Source: https://github.com/ultralytics/yolov5/issues/2293)
