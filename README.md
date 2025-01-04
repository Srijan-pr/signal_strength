# signal_strength
import numpy as np
import matplotlib.pyplot as plt
plt.style.use('ggplot')
from math import *
def signal_strength(distance,attenuation,hardware_degradation,rate_degradation,time_exposure,initial_signal):
    signal_initial = (initial_signal*np.exp(-attenuation*distance))*(1 - hardware_degradation)
    signal_final = np.zeros(len(time_exposure))
    for i in range(len(time_exposure)):
        signal_final[i] = (initial_signal*exp(-attenuation*20))*(1 - (hardware_degradation)/(1 - rate_degradation*time_exposure[i]))

    fig, (ax1,ax2) = plt.subplots(1,2,constrained_layout = True, figsize = (12,4))
    ax1.plot(distance,signal_initial,c ='red')
    ax2.plot(time_exposure,signal_final,c='blue')
    ax1.set_xlabel("distance from the source( in 10^5 metres)")
    ax1.set_ylabel("signal strength")
    ax1.set_title("signal strength vs distance")
    ax2.set_xlabel("time of exposure(in hours)")
    ax2.set_ylabel("signal strength")
    ax2.set_title("signal strength vs time")
    plt.show()
distance = np.array([0,0.1,0.3,0.5,0.7,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20])
attenuation_constant = 0.05
hardware_degradation_factor = 0.2
rate_of_degradation = 0.01
inital_signal_strength = 100
time = np.array([5,10,15,20,25,30,35,40,45,50,55,60,65,70,75,80,85,90])
max_distance = 20
signal_strength(distance,attenuation_constant,hardware_degradation_factor,rate_of_degradation,time,inital_signal_strength)
