Multiprocessing code to simulate real-time photoplethysmography sensor readings with already collected data for real-time data analysis removing motion artifacts.

## Background

Photoplethysmography sensors give you blood pulse data, which have primary peak, dicrotic notch, and secondary peaks. It should be a consistent reading as we are recording pulses.

However, motion artifacts can severly disrupt the quality of this data, making it unrecognizable to be useful.

My data had two photoplethysmography channels, one device on the big toe and one on the index finger. I wanted to have 10 good peaks where both toe data and finger data are "good quality."

## Work done

I had a pulse kernel that I deemed of "good quality." I convolved it over the data, taking notes of spikes where the cosine simularity is high, which means that the data resembles the kernel/is a "good peak."

I then utilized simple functions to remove outliers and find intervals where there were 10 consistent good peaks. The number of good peaks can be adjusted (10, 20, 5, 100).

I already had the time-series data of photoplethysmography sensors but I wanted to mimic the sensor reading the data sequentially so I utilized multiprocessing for both the "reading" and to do real-time analysis. Real time analysis is more useful as when people are wearing photoplethysmography sensors for a while, you don't want the data to be inaccessible until after they take it off. This can be considered a batched real time analysis.

## Files

MultiprocessingTestCase.ipynb - Jupyter notebook to simulate sensor readings

1100.txt - Pre-collected photoplethysmography data, 100 hertz

toConvolve.txt - Kernel of "good peak"


