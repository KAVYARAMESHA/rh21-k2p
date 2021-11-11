import cv2
from math import hypot
from ctypes import cast,POINTER
from comtypes import CLCTX_ALL
from pycaw.pycaw import audioUtilities,IAudioEndpoinVolume
inport numpy as np

cap=cv2.VideoCapture(0)

mpHands=mp.solutions,hands
hands=mpHands.Hands()
mpDraw=mp.solutions.drawing_utils

devices=AudioUtilities.GetSpeakers()
interface=devices.Activate(IAudioEndpointVolume._iid_,CLSCTX_ALL,None)
volume=cast(interface,POINTER(IAudioEndpointVolume))

volMin,volMax=volume.GetVolumeRange()[:2]
While True:
success,img=cap.read()
imgRGB=cv2.cvtColor(img,cv2.COLOR_BGR2RGB)
result=hand.process(impRGB)

lmList=[]
if result.multi_hand_landmarks:
  for handlandmark in result.multi_hand_landmarks:
      for id,lm in enumerate(handlandmark.landmark):
          h,w,_=img.shape
          cx,cy=int(lm.x*w),int(lm.y*h)
          lmList.append([id,cx,cy])
      mpDraw.draw_landmarks(img,handlandmark,mpHands.HAND_CONNECTIONS)
if lmList !=[]: 
