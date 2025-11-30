# -Amplitude-Modulation-and-Demodulation-using-NumPy-and-Matplotlib

__Aim__: 

To implement and analyze amplitude modulation (AM) using Python's NumPy and Matplotlib libraries. 

__Apparatus Required__: 

Software: Python with NumPy and Matplotlib libraries 
Hardware: Personal Computer 

__Theory__: 

Amplitude Modulation (AM) is a technique used in electronic communication, primarily for transmitting 
information via a radio carrier wave. In AM, the amplitude of the carrier wave is varied in proportion to that of 
the message signal. The general form of an AM signal is: 


__Algorithm__:
1. Initialize Parameters: Set the values for carrier frequency, message frequency, and sampling frequency. 
2. Generate Time Axis: Create a time vector for the signal duration. 
3. Generate Message Signal: Define the message signal as a cosine wave. 
4. Generate Carrier Signal: Define the carrier signal as a cosine wave. 
5. Modulate Signal: Apply the AM formula to obtain the modulated signal. 
6. Plot the Signals: Use Matplotlib to plot the message signal, carrier signal, and modulated signal.
   
 __Program__:
 ````c
import numpy as np
import matplotlib.pyplot as plt
from scipy.signal import hilbert

# Parameters (from your photo)
A_c = 11.4       # Carrier amplitude
f_c = 4580       # Carrier frequency (Hz)
A_m = 5.7        # Message amplitude
f_m = 458        # Message frequency (Hz)

sampling_frequency = 100000   # VERY IMPORTANT for proper waveform
duration = 0.015              # show only 15ms like your picture

# Time axis
t = np.linspace(0, duration, int(sampling_frequency * duration))

# Message Signal
m_t = A_m * np.cos(2 * np.pi * f_m * t)

# Carrier Signal
c_t = A_c * np.cos(2 * np.pi * f_c * t)

# Amplitude Modulated (AM) Signal
s_t = (1 + (m_t / A_c)) * c_t   # normalized so waveform looks correct

# Demodulation using Hilbert Transform
analytic_signal = hilbert(s_t)
envelope = np.abs(analytic_signal)
demodulated_message = envelope - A_c

# Plot results
plt.figure(figsize=(12, 10))

plt.subplot(4, 1, 1)
plt.plot(t, m_t)
plt.title('Original Message Signal')
plt.grid(True)

plt.subplot(4, 1, 2)
plt.plot(t, c_t)
plt.title('Carrier Signal')
plt.grid(True)

plt.subplot(4, 1, 3)
plt.plot(t, s_t)
plt.title('Amplitude Modulated (AM) Signal')
plt.grid(True)

plt.subplot(4, 1, 4)
plt.plot(t, demodulated_message)
plt.title('Demodulated Signal')
plt.grid(True)

plt.tight_layout()
plt.show()
`````
 __Output__:
![WhatsApp Image 2025-11-30 at 10 17 39_a4705aac](https://github.com/user-attachments/assets/4ec074b1-a4f7-4284-9e0c-6b3f6cc3ac3f)


 __Result__:
  The program successfully implemented Amplitude Modulation (AM) using Python's NumPy and Matplotlib libraries.
![WhatsApp Image 2025-11-30 at 10 19 41_e9bd2c25](https://github.com/user-attachments/assets/1e68b55c-a06f-4df1-adc7-3e8e4bf6598d)


