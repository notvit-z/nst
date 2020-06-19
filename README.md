# Neural Style Transfer

This is a python-tensorflow1 implementation of Neural Style Transfer, described in detail by [Gatys et al. 2015](http://arxiv.org/abs/1508.06576). 

This work wouldn't have been possible without the knowledge obtained from the "[Convolutional Neural Networks](https://www.coursera.org/learn/convolutional-neural-networks)" course, offered by [deeplearning.ai](http://www.deeplearning.ai). By the other hand, it is worth mentioning that those guys, in turn, took inspiration from [Harish Nayaranan](https://harishnarayanan.org/writing/artistic-style-transfer)'s and [log0](https://github.com/log0/neural-style-painting)'s work for developing their own version. The following codes use transfer learning from the vgg-19 model to process the images, which you can download from [here](http://www.vlfeat.org/matconvnet/models/imagenet-vgg-verydeep-19.mat).

## Requirements
- python (v3.7.7 was used).
- scipy  (v1.4.1 was used).
- numpy (v1.18.1 was used).
- tensorflow (v1.14.0-gpu was used).
- imageio (v2.8.0 was used).
- tqdm (v4.46.1 was used).
- PIL/Pillow (v7.1.2 was used).
- opencv (v3.4.2 was used)
- os, sys, matplotlib, glob.
- VGG-19 model (download on link above).

This repo has three different implementations of neural style transfer:

### 1. Classic ([nst.py](nst.py))
It generates a new image by combining a content image and a style image. You have to run it giving two inputs as follows:

```
$ python nst.py path/to/content_image.jpg path/to/style_image.jpg
```

### 2. To all frames of a video ([nst_video.py](nst_video.py))
It applies neural style transfer to all the frames of a video file. It requires two inputs, the path to the video file and to the style image. Here an example:

```
$ python nst_video.py ./input_videos/video01.mp4 ./input_images/style_image01.jpg
```

### 3. To specific frames of a video ([nst_video_frames_interval.py](nst_video_frames_interval.py))
Same as the last one, but adding the option of specifying which frames you want to run the model over. It has four inputs, where the last two ones are the number of the fisrst and last frame to run the model. Here an example:

```
$ python nst_video_frames_interval.py ./input_videos/video01.mp4 ./input_images/style_image01.jpg 8 97
```

All codes automatically create an output folder to save the created images, whose name is a combination of the filenames of the content and the style inputs. Some functions, not directly related with the actual Deep Learning part, are stored on the [nst_fxs.py](nst_fxs.py) code.

Both code 2 and 3 end up saving all the generated videoframe image files, and not a video file. In order to create a video back from these new frames, the code [mkvideo.py](mkvideo.py) is provided, which needs the folder containing your frames as the only input. Here an example:

```
$ python mkvideo.py ./outputs/video01_style_image01
```
