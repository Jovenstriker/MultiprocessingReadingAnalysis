Multiprocessing code to simulate real-time reading photoplethysmography data from a sensor and analyzing data to get "10 good peaks"

Photoplethysmography sensors give you blood pulse data, which have primary peak, dicrotic notch, and secondary peaks. It should be a consistent reading as we are recording pulses.

However, motion artifacts can severly disrupt the quality of this data, making it unrecognizable to useful data.

I had a pulse kernel that I deemed of "good quality." I convolved it over the data, taking notes of spikes where the cosine simularity is high, which means that the data resembles the kernel/is a "good peak."

I then utilized simple functions to remove outliers and find intervals where there were 10 consistent good peaks. The number of good peaks can be adjusted (10, 20, 5, 100).

I already had historical data of photoplethysmography sensors but I wanted to mimic sensor reading the data sequentially with time so I utilized multiprocessing for both the "reading" and analysis.
