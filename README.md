Multiprocessing code to simulate real-time photoplethysmography sensor readings with already collected data for real-time data analysis removing motion artifacts.

## Results
![Alt text](https://private-user-images.githubusercontent.com/146682743/407160955-c5d9591e-db38-4627-b463-abfcd9905126.jpg?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MzgwMzIwODUsIm5iZiI6MTczODAzMTc4NSwicGF0aCI6Ii8xNDY2ODI3NDMvNDA3MTYwOTU1LWM1ZDk1OTFlLWRiMzgtNDYyNy1iNDYzLWFiZmNkOTkwNTEyNi5qcGc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMTI4JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDEyOFQwMjM2MjVaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0zM2U2Y2Y1NGFjNjNiNjA0ZGFkM2M3ZTE2NTFiMDBhZWM0MjkxM2JiODcxYzdmNWM2MjliNTkzYjUyOTBhYTE4JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.vaxgsFeNbqN_NuuHEwFa0oaXKleBNP0ZQZzykyx0v_4)
## Background

My data had two photoplethysmography channels, one device on the big toe and one on the index finger. I wanted to have 10 good peaks where both toe data and finger data are "good quality."

Photoplethysmography sensors give you blood pulse data, which have primary peak, dicrotic notch, and secondary peaks. It should be a consistent reading as we are recording pulses.

However, motion artifacts can severly disrupt the quality of this data, making it unrecognizable to be useful. The finger and toe data should be displaced a little by a phase shift because the sensors were located in different areas from the pulse-beating heart, but it should be a constant phase shift and the overall pulse shapes should be similar for both finger and toe.


## Work done

I had a pulse kernel that I deemed of "good quality." I convolved it over the data, taking notes of spikes where the cosine simularity is high, which means that the data resembles the kernel/is a "good peak."

I then utilized simple functions to remove outliers and find intervals where there were 10 consistent good peaks. The number of good peaks can be adjusted (10, 20, 5, 100).

I already had the time-series data of photoplethysmography sensors but I wanted to mimic the sensor reading the data sequentially so I utilized multiprocessing for both the "reading" and to do real-time analysis. Real time analysis is more useful as when people are wearing photoplethysmography sensors for a while, you don't want the data to be inaccessible until after they take it off. This can be considered a batched real time analysis.

## Files

MultiprocessingPPGSimulation.ipynb - Jupyter notebook to simulate sensor readings

1100.txt - Pre-collected photoplethysmography data, 100 hertz

toConvolve.txt - Kernel of "good peak"


