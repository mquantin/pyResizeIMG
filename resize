import bpy
import os
import glob
from PIL import Image

# get the path of the folder where pictures are saved
blenderFilePath = bpy.data.filepath
path = blenderFilePath + "/tmp" # this is where my images are saved

# parameters
dpi_cible = 300# ppi
largeur_cible = 1024# px; mettre false pour ne pas downscaler les images

# downscale the image to widthTarget (ex: 1024px). 
def resize(img, widthTarget):
    length_x, width_y = img.size
    factor = min(1, float(widthTarget) / length_x)
    size = int(factor * length_x), int(factor * width_y)
    return img.resize(size, Image.ANTIALIAS)


for infile in glob.glob("*.jpg"):
  file, ext = os.path.splitext(infile)
  with Image.open(infile) as im:
    if largeur_cible:
      im = resize(im, largeur_cible)
    im.save(file + ".new", "JPEG", dpi=(dpiTarget, dpiTarget))# "JPEG" ou "PNG" autre format: https://pillow.readthedocs.io/en/stable/handbook/image-file-formats.html
