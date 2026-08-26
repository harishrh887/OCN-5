# Free-Space Optical Communication (FSO) Implementation

## Aim: 
To implement and analyze a free space optical communication link using a laser/LED transmitter and photodiode/APD receiver.

## Apparatus/Software Required:
Python Colab

## Theory:
	FSO uses light beams to transmit data through free space instead of fiber.
	Performance depends on distance, alignment, and atmospheric attenuation.
	Received power decreases exponentially with distance.

## Formula:
Loss=10⋅〖log⁡〗_10 (P_in/P_out )

## 1
## Setup the Transmitter
Info
Prepare the optical source for transmission.
	Use a Laser/LED source
	Mount it on an optical bench
	Ensure stable power supply

## 2
## Align the Optical Path
Warning
Proper alignment ensures maximum received signal.
	Place transmitter and receiver in line of sight
	Adjust using lenses/mirrors if needed
	Minimize beam divergence

## 3
## Connect the Receiver
Setup the photodiode/APD to detect the optical signal.
	Mount detector opposite to transmitter
	Connect to oscilloscope for signal observation
	Record received power

## 4
## Measure Received Power
Collect data at different distances.
Loss = 10 log10(Pin / Pout)
	Vary distance (1 m, 5 m, 10 m, etc.)
	Note received power in µW
	Calculate link loss

## 5
## Plot Graphs
Visualize performance of FSO link.
	Plot Received Power vs Distance
	Observe exponential decay trend
	Compare with theoretical model

## 6
## Conclude Results
Success
Summarize findings of the experiment.
	Reliable communication up to ~10 m indoors
	Loss increases with distance
	Alignment critical for performance

## Sample Output
Graph: Received Power vs Distance (decay curve)
<img width="630" height="467" alt="image" src="https://github.com/user-attachments/assets/0ec8bb24-ddfb-4d3a-b0f2-a5b661798ad4" />
<img width="672" height="466" alt="image" src="https://github.com/user-attachments/assets/2a113e54-2433-4072-ba62-16539939e93a" />
<img width="672" height="461" alt="image" src="https://github.com/user-attachments/assets/448e0d3f-a834-4e14-953f-4d429b7a9996" />

## Python Code
import numpy as np
import matplotlib.pyplot as plt

#Input optical power in microwatts
Pin = 1500  # µW

#Distance between transmitter and receiver in metres
distance = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])

#FSO attenuation coefficient
alpha = 0.20  # per metre

#Calculate received power using exponential attenuation
Pout = Pin * np.exp(-alpha * distance)

#Calculate link loss in dB
loss = 10 * np.log10(Pin / Pout)

#Display results
print("FSO Communication Results")
print("-------------------------")
print("Distance (m) | Received Power (µW) | Loss (dB)")

for d, p, l in zip(distance, Pout, loss):
    print(f"{d:11} | {p:20.2f} | {l:8.2f}")

#Plot received power versus distance
plt.figure(figsize=(8, 5))
plt.plot(distance, Pout, marker='o')
plt.xlabel("Distance (m)")
plt.ylabel("Received Power (µW)")
plt.title("FSO Received Power vs Distance")
plt.grid(True)
plt.show()

#Plot link loss versus distance
plt.figure(figsize=(8, 5))
plt.plot(distance, loss, marker='o')
plt.xlabel("Distance (m)")
plt.ylabel("Link Loss (dB)")
plt.title("FSO Link Loss vs Distance")
plt.grid(True)
plt.show()

## Output
 <img width="652" height="217" alt="image" src="https://github.com/user-attachments/assets/a306ef17-5e67-4ef0-920f-e8a2d615bddc" />
The graph shows that the received optical power decreases exponentially as the distance between the transmitter and receiver increases. The link loss increases with distance, demonstrating the effect of atmospheric/path attenuation on an FSO communication link.
  
## Result
The free-space optical communication link was successfully implemented and analyzed using Python. The received optical power decreased exponentially with increasing transmission distance, while the link loss increased correspondingly. The results demonstrate that distance and proper alignment significantly affect FSO link performance, and reliable indoor communication can be achieved over short distances under suitable conditions.
