import cv2
import argparse
import imutils

## creates new arguments that take an input and output file
ap = argparse.ArgumentParser()
ap.add_argument("-i","--input",required=True,
	help="specifies input file path")
ap.add_argument("-o","--output",required=True,
	help="specifies output file path")
args = vars(ap.parse_args())

## reading a image file
img = cv2.imread(args["input"])
grayScale = cv2.cvtColor(img,cv2.COLOR_BGR2GRAY)
blur = cv2.GaussianBlur(grayScale,(101,101),0)
thresh = cv2.threshold(blur,200,255,cv2.THRESH_BINARY)[1]

cv2.imwrite(args["output"],thresh)


cnts = cv2.findContours(thresh.copy(), cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)
cnts = imutils.grab_contours(cnts)
print("There are {} basketballs in this picture".format(len(cnts)))
