import numpy as np
import matplotlib.pyplot as plt

def avg(data):
    return (sum(data)/len(data))

#if q = cA^a B^b where c, m, n are constants, then
def rul4(Q, A, dA, a, B, dB, b):
    dQ = Q * np.sqrt(((a*(dA/A))**2) + (b*(dB/B))**2)
    return dQ

#Experiment 1
cv = [0., 3.93, 6.23, 7.76, 8.73, 9.34, 9.69, 9.95, 10.09, 10.21, 10.33, 10.37]
ct = [0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100, 110]

plt.plot(ct, cv)
plt.title('Experiment 1: Charging')
plt.show()

#Experiment 1 pt 2
dv = [11.71, 7.85, 5.42, 3.69, 2.56, 1.78, 1.22, 0.86, 0.68, 0.42, 0.29, 0.21, 0.15]
dt = [0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100, 110, 120]

plt.plot(dt, dv)
plt.title('Experiment 1: Discharging')
plt.show()


#Experiment 2
tau_d = [27.73, 28., 26.07, 26.68, 26.2, 26., 26.38, 26.78, 26.13, 26.38]
dtau_d = (np.std(tau_d)/np.sqrt(len(tau_d)))
tau_d = avg(tau_d)

print('The average time constant for a discharging RC circuit is', tau_d, '+/-', dtau_d)

tau_c = [29.56, 29.33, 29.28, 29.12, 29.38, 29.4, 29.3, 29.56, 29.53, 29.35]
dtau_c = (np.std(tau_c)/np.sqrt(len(tau_c)))
tau_c = avg(tau_c)
print('The average time constant for a charging RC circuit is', tau_c, '+/-', dtau_c)

#Experiment 3
r = 500 * 10**3
dr = 0.01 * 10**3
c = 54 * 10**-6
dc = 0.01 * 10 **-6
tau = r * c
dtau = rul4(tau, r, dr, 1, c, dc, 1)
print('Direct measuremnets show the time constant for this circuit to be', tau, '+/-', dtau)


