# -License-Plate-Detection-using-OpenCV-and-Haar-Cascade-Classifier
# Name: Jaya Vishwa S
# Register Number: 212224230105
# Aim
To implement a License Plate Detection system using OpenCV and Haar Cascade Classifier, draw bounding boxes, crop the detected region, and blur the license plate to improve privacy. The detection accuracy is improved by tuning Haar Cascade parameters.

# Software Used
Python 3.7 or above

OpenCV (opencv-python)

NumPy

Matplotlib

Jupyter Notebook (Anaconda)

Haar Cascade File: haarcascade_russian_plate_number.xml

# Algorithm
Import necessary libraries such as OpenCV and Matplotlib

Read the input vehicle image

Convert the original image to grayscale for faster computation

Load the Haar Cascade classifier for license plate detection

Detect license plate using detectMultiScale function

Draw rectangle around detected area

Crop the detected region using numpy slicing with (x, y, w, h) values

Apply median blurring on the cropped region

Replace the original region with blurred version

Display final result using Matplotlib

# Program
```
def detect_plate(img):
    img_copy = img.copy()

    gray = cv2.cvtColor(img_copy, cv2.COLOR_BGR2GRAY)

    plates = plate_cascade.detectMultiScale(
        gray,
        scaleFactor=1.1,
        minNeighbors=4
    )

    for (x, y, w, h) in plates:
        cv2.rectangle(
            img_copy,
            (x, y),
            (x + w, y + h),
            (0, 255, 0),
            3
        )

    return img_copy




def detect_and_blur_plate(img):
    img_copy = img.copy()

    gray = cv2.cvtColor(img_copy, cv2.COLOR_BGR2GRAY)

    plates = plate_cascade.detectMultiScale(
        gray,
        scaleFactor=1.1,
        minNeighbors=4
    )

    for (x, y, w, h) in plates:
        roi = img_copy[y:y+h, x:x+w]

        blurred_roi = cv2.medianBlur(roi, 15)

        img_copy[y:y+h, x:x+w] = blurred_roi

    return img_copy
```
<img width="502" height="547" alt="655082821-b3f52d73-70f1-4e13-ac45-f044f0595a67" src="https://github.com/user-attachments/assets/7c542617-2100-4ca8-b513-53915097b051" />

<img width="536" height="558" alt="655082842-87b0201f-1967-418b-a9d2-0b0ed57ab10a" src="https://github.com/user-attachments/assets/2a4ca25a-bf7d-4cff-a977-700579c761ee" />

<img width="533" height="548" alt="655082855-49e5f0ea-eb89-4b73-9013-bbaeb932ab4d" src="https://github.com/user-attachments/assets/bcc99d0d-0821-44da-918b-219963b577f6" />

# Modification Done
Parameter tuning was performed by adjusting scaleFactor and minNeighbors values in detectMultiScale to improve accuracy and reduce false detections. Median blur was applied to protect license plate information.

# Result
The License Plate Detection system was successfully implemented using OpenCV and Haar Cascade. The detected license plate region was blurred using median filtering. The modified values improved overall detection performance and output quality.

# Conclusion
This workshop demonstrates how classical computer vision methods like Haar Cascades can be used for real-time applications such as automated toll systems, smart parking, and traffic surveillance. Proper preprocessing and parameter tuning significantly improve detection results.
