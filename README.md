Multiprocessing code to simulate real-time photoplethysmography data reading from a sensor and analyzing data to get "10 good peaks"

## Background

Photoplethysmography sensors give you blood pulse data, which have primary peak, dicrotic notch, and secondary peaks. It should be a consistent reading as we are recording pulses.

However, motion artifacts can severly disrupt the quality of this data, making it unrecognizable to useful data.

I had two photoplethysmography sensors attached, one to the toe and one to the finger. I wanted to have 10 good peaks where the toe data and finger data are nice.

## Work done

I had a pulse kernel that I deemed of "good quality." I convolved it over the data, taking notes of spikes where the cosine simularity is high, which means that the data resembles the kernel/is a "good peak."

I then utilized simple functions to remove outliers and find intervals where there were 10 consistent good peaks. The number of good peaks can be adjusted (10, 20, 5, 100).

I already had the time-series data of photoplethysmography sensors but I wanted to mimic the sensor reading the data sequentially so I utilized multiprocessing for both the "reading" and analysis.
