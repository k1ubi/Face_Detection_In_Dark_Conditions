<div align="center">

```
______ ___  _____  _____  ______ _____ _____ _____ _____ _____ 
|  ___/ _ \/  __ \|  ___| |  _  \  ___|_   _|  ___/  __ \_   _|
| |_ / /_\ \ /  \/| |__   | | | | |__   | | | |__ | /  \/ | |  
|  _||  _  | |    |  __|  | | | |  __|  | | |  __|| |     | |  
| |  | | | | \__/\| |___  | |/ /| |___  | | | |___| \__/\ | |  
\_|  \_| |_/\____/\____/  |___/ \____/  \_/ \____/ \____/ \_/
```

`[ contrast stretching vs. histogram eq. vs. CLAHE, then Haar cascade face detection ]`

![python](https://img.shields.io/badge/PYTHON-ff00c8?style=for-the-badge&logo=python&logoColor=00fff9&labelColor=0a0014)
![opencv](https://img.shields.io/badge/OPENCV-00fff9?style=for-the-badge&logo=opencv&logoColor=0a0014&labelColor=0a0014)
![colab](https://img.shields.io/badge/COLAB-ff00c8?style=for-the-badge&logo=googlecolab&logoColor=00fff9&labelColor=0a0014)

</div>

<br>

```
▓▒░ 0x00 // SITREP ░▒▓
```

Single notebook (`FacialDetection_High_Dark.ipynb`, built for Colab) benchmarking three
low-light image enhancement techniques against the same dark photo, then running OpenCV's
Haar cascade face detector on each output to see which enhancement actually gets a face
detected that the raw dark frame doesn't.

<br>

```
▓▒░ 0x01 // PIPELINE ░▒▓
```

```
 dark input photo
        │
        ├──▶ contrast stretching     np.percentile(img, 2, 98) + rescale_intensity
        ├──▶ histogram equalization  skimage.exposure.equalize_hist
        └──▶ adaptive equalization   skimage.exposure.equalize_adapthist(clip_limit=0.03)
                        │
                        ▼
        haarcascade_frontalface_default.xml + haarcascade_eye.xml
                        │
                        ▼
         bounding boxes drawn per technique → side-by-side comparison
```

This is the exploratory sibling of [`Low-Light-Face-Recognition`](https://github.com/k1ubi/Low-Light-Face-Recognition) —
this notebook compares *which* enhancement helps detection most; that repo takes the winning
technique (adaptive equalization) and turns it into an automated pre-processing gate.

<br>

```
▓▒░ 0x02 // RUN IT ░▒▓
```

```console
root@node:~# # open FacialDetection_High_Dark.ipynb in Google Colab
root@node:~# # (imports google.colab.patches.cv2_imshow — needs a Colab runtime, not local Jupyter)
root@node:~# # drop a source image at /content/images/, run all cells
```

<br>

<div align="center">

`GNU GPLv3` — see [`LICENSE`](./LICENSE)

</div>
