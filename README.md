Nuclei-Counter
==============

import numpy as np
import scipy as s
import matplotlib.pylab as pl
from scipy import misc
import matplotlib.pyplot as plt
import mahotas as mmm
from scipy import ndimage
import pymorph as h
#########################################################
l = misc.imread('C:\Users\PRITHVIRAJ\Desktop/h.jpg')  
pl.imshow(l)                                            
l=mmm.colors.rgb2gray(l,dtype=np.uint8)                 
pl.gray()
thresh=mmm.thresholding.otsu(l)
pl.imshow(l>thresh)
new=(l>thresh)
z=ndimage.gaussian_filter(l,16)
pl.imshow(z)
rmax=h.regmax(z)
pl.imshow(h.overlay(l, rmax))
seeds,nr_nucle = ndimage.label(rmax)
print nr_nucle

