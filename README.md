# head-mri

import cv2
import numpy as np
from skimage import measure
from skimage.measure import regionprops
import matplotlib.pyplot as plt

class BrainTumorAnalysis:
    def __init__(self, image_path):
        self.image_path = image_path
        self.image = cv2.imread(image_path, cv2.IMREAD_GRAYSCALE)
        if self.image is None:
            raise ValueError("Image cannot be loaded, double check file path.")
        self.tumor_present = False
        self.tumor_type = "No tumor"
        self.tumor_size = (0, 0)
        self.tumor_position = (0, 0)
        self.process_image = None
        self.tumor_mask = None

    def analyze(self):
        self._preprocess_image()
        self._detect_tumor()
        if self.tumor_present:
            self._analyze_tumor()
            self._measure_size()        
