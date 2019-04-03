## Install
- Create Python REPL Using Docker
[https://hub.docker.com/r/jjanzic/docker-python3-opencv/](https://hub.docker.com/r/jjanzic/docker-python3-opencv/)
```
docker pull jjanzic/docker-python3-opencv
docker run -it jjanzic/docker-python3-opencv python     ## this will create a python prompt where you can import cv2
>>> import cv2
```
- Install Opencv using Conda environment
[https://anaconda.org/anaconda/opencv](https://anaconda.org/anaconda/opencv)
```
conda remove opencv
conda install -c menpo opencv
pip install --upgrade pip
pip install opencv-contrib-python

```
- Additional installs
```
sudo apt install libgtk2.0-dev
```

## Save edited image
- [http://answers.opencv.org/question/54142/how-to-save-detected-face-in-opencv/](http://answers.opencv.org/question/54142/how-to-save-detected-face-in-opencv/)


## Opencv with Android
- [https://medium.com/@akshikawijesundara/object-recognition-with-opencv-on-android-6435277ab285](https://medium.com/@akshikawijesundara/object-recognition-with-opencv-on-android-6435277ab285)
- [https://www.kotlindevelopment.com/face-detection-age-and-gender-prediction-on-android-with-kotlin/](https://www.kotlindevelopment.com/face-detection-age-and-gender-prediction-on-android-with-kotlin/)
- [https://github.com/opencv/opencv/tree/master/samples/android/face-detection](https://github.com/opencv/opencv/tree/master/samples/android/face-detection)
- [https://www.youtube.com/watch?v=D5qxPrp-zng](https://www.youtube.com/watch?v=D5qxPrp-zng)

## Face recognition
- [https://www.pyimagesearch.com/2018/09/24/opencv-face-recognition/](https://www.pyimagesearch.com/2018/09/24/opencv-face-recognition/)
- [https://www.pyimagesearch.com/2018/06/18/face-recognition-with-opencv-python-and-deep-learning/](https://www.pyimagesearch.com/2018/06/18/face-recognition-with-opencv-python-and-deep-learning/)
- [https://github.com/ageitgey/face_recognition](https://github.com/ageitgey/face_recognition)


## Color detection
- [https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_imgproc/py_colorspaces/py_colorspaces.html](https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_imgproc/py_colorspaces/py_colorspaces.html)
- [https://www.geeksforgeeks.org/detection-specific-colorblue-using-opencv-python/](https://www.geeksforgeeks.org/detection-specific-colorblue-using-opencv-python/)
- [https://www.pyimagesearch.com/2014/08/04/opencv-python-color-detection/](https://www.pyimagesearch.com/2014/08/04/opencv-python-color-detection/)
 

## References
- [https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_objdetect/py_face_detection/py_face_detection.html](https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_objdetect/py_face_detection/py_face_detection.html)
- [https://github.com/Aidenjn/RealTimeFaceRecognition/blob/master/scripts/main.py](https://github.com/Aidenjn/RealTimeFaceRecognition/blob/master/scripts/main.py)
- [https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_feature2d/py_table_of_contents_feature2d/py_table_of_contents_feature2d.html](https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_feature2d/py_table_of_contents_feature2d/py_table_of_contents_feature2d.html)
- [https://www.pyimagesearch.com/2018/11/12/yolo-object-detection-with-opencv/](https://www.pyimagesearch.com/2018/11/12/yolo-object-detection-with-opencv/)
- [https://realpython.com/face-detection-in-python-using-a-webcam/](https://realpython.com/face-detection-in-python-using-a-webcam/)

## Academic Publications Reference
- [http://stevenputtemans.github.io/#about](Senior contributor of Opencv)
- [http://stevenputtemans.github.io/files/VISAPP2018_industrial.pdf](Industrial detection research paper)
