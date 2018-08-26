# Machine Learning on iOS
## Hands-on with IBM Watson and Core ML

* Session: https://360idev.com/sessions/machine-learning-on-ios-hands-on-with-ibm-watson-and-core-ml/

* Workshop Based on: https://watson-developer-cloud.github.io/watson-vision-coreml-code-pattern/arduino/introduction.html

* Shortened Session Link: http://ibm.biz/coremlworkshop
* Image Downloads: http://ibm.biz/arduino_images

* Demo:
https://www.ibm.com/watson/services/visual-recognition/demo

### Speakers
* Tom Mariewicz
* Yacine Rezgui

IBM teammates who primarily work with Watson

Workshop Skill level: Beginner

We will build an image recognition app we can use offline.  For working Arduino boards and ones with issues like burnt-out capacitors.  This can help us troubleshoot bad components.

### Getting Started with Artificial Intelligence
Written by the Authors

### Watson Services + Core ML
Last Spring, Apple partnered with IBM to bring Watson (IBM's visual recognition system) to iOS.

GPU required to use some services.  But IBM now offers offline cloud one that's pay-by-usage.

### IBM Watson

Watson is a brand over many different types of products

- Collection of APIs for implementing AI/ML/DL
- Integration with wide range of products/services
- Security/privacy

### IBM Watson Services for CoreML

- Build apps to use Watson models on iOS (even offline)

Just using the API will mean smaller app sizes.  Developer chooses when to pull down models.

- Custom models

Identify shoe brands (Adidas vs Nike)

- Upload training data from real world, then download the updated model

### Workshop

Go to this website:
* http://ibm.biz/coremlworkshop

We'll use Carthage (>0.29)

Get up and take 10 images of arduino boards OR dowload them at ibm.biz/arduino_images

Make sure models images are done in different backgrounds.  In one example, they tested ML on identifying Russian tanks versus American tanks.  Because all the training photos of Russian tanks were taken during the day, it tended to classify any night photos as American tanks.

Negative training sets of similar items is useful.  For instance, instead of Arduinos, get Raspberry Pis and similar looking items that are close enough for relevant training.  Taking background-only images (like empty table, empty hand, etc) can also help the model know what to look for.
