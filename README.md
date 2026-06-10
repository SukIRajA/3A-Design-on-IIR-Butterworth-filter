# IIR-FILTER-DESIGN
# EXP 3 A: DESIGN OF LOW PASS BUTTERWORTH FILTER USING BILINEAR TRANSFORMATION TECHNIQUE

# AIM: 

# To perform design of Butterworth Filter Using Impulse Invariant and Bilinear Transformation Techniques using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```
clc;
close;

wp=input('Enter the pass band frequency (Radians) = ');
ws=input('Enter the stop band frequency (Radians) = ');
alphap=input(' Enter the pass band attenuation (dB)= ');
alphas=input(' Enter the stop band attenuation(dB)= ');
T=input('Enter the Value of sampling Time=');

omegap=(2/T)*tan(wp/2);
disp(omegap,'omegap=');

omegas=(2/T)*tan(ws/2);
disp(omegas,'omegas=');

N=log10(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1))/(2*log10(omegas/omegap));
disp(N,'N=');

N=ceil(N);
disp(N,'Round off value of N=');

omegac=omegap/(((10^(0.1*alphap)-1)^(1/(2*N))));
disp(omegac,'omegac=');

disp('Normalised Analog LPF Transfer function H(S)=');
hs_Normalised = analpf(N,'butt',[0,0],1);
disp(hs_Normalised);

disp('Analog LPF Transfer function H(S)=');
hs = analpf(N,'butt',[0,0],omegac);
disp(hs);

z=poly(0,'z');

Hz=horner(hs,(2/T)*((z-1)/(z+1)));

disp('Digital LPF Transfer function H(Z)=');
disp(Hz);

HW=frmag(Hz,512);
w=0:%pi/511:%pi;
plot(w/%pi,abs(HW));

xlabel('Normalized Digital Frequency w');
ylabel('Magnitude ');
title(' Frequency Response of Butterworth IIR LPF');
```

# OUTPUT: 
<img width="945" height="952" alt="image" src="https://github.com/user-attachments/assets/8e3a898f-9b17-4f75-a096-1813351f080c" />
<img width="692" height="982" alt="image" src="https://github.com/user-attachments/assets/fbf4261a-f247-47cf-a1a5-6a3dc77ac88b" />

#CALCULATION:

<img width="899" height="1599" alt="image" src="https://github.com/user-attachments/assets/4bdde5e0-eebf-4685-9a3e-645c1b326ac2" />

<img width="899" height="1599" alt="image" src="https://github.com/user-attachments/assets/3058fd10-b8e3-43fd-ad78-d429cb2d6558" />

<img width="899" height="1599" alt="image" src="https://github.com/user-attachments/assets/4e6e302c-90ab-4218-ab82-ebd3819c2d5c" />
<img width="899" height="267" alt="image" src="https://github.com/user-attachments/assets/9fa9a53c-228e-4497-9abf-5851275ab893" />


# RESULT: 

Thus, design of Butterworth Low pass IIR filter waveforms were plotted and output was verified.

