# head-mri

import cv2
import numpy as np
from skimage import measure
from skimage.measure import regionprops
import matplotlib.pyplot as plt

class BrainTumorAnalyzer:
    def __init__(self, image_path):
        self.image_path = image_path
        self.image = cv2.imread(image_path, cv2.IMREAD_GRAYSCALE)
        if self.image is None:
            raise ValueError("Could not load image. Please check the file path.")
