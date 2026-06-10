# IIR-FILTER-DESIGN
# EXP 3 A: DESIGN OF LOW PASS BUTTERWORTH FILTER USING BILINEAR TRANSFORMATION TECHNIQUE

# AIM: 

# To perform design of Butterworth Filter Using Impulse Invariant and Bilinear Transformation Techniques using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
~~~
clc ; 
close ; 
wp=input('Enter the pass band frequency (Radians )= ' ); 
ws=input('Enter the stop band frequency (Radians )= ' ); 
alphap=input( ' Enter the pass band attenuation (dB)=' ); 
alphas=input( ' Enter the stop band attenuation(dB)=' ); 
T=input('Enter the Value of sampling Time=');

//Pre warping- Bilinear Transformation 
omegap=(2/T)*tan(wp/2); 
disp(omegap,'omegap='); 
omegas=(2/T)*tan(ws/2); 
disp(omegas,'omegas=');

//Order of the filter 
N=log10(((10^(0.1*alphas))-1)/((10^(0.1*alphap))-1))/(2*log10(omegas/omegap)); 
disp(N,'N='); 
N=ceil(N); 
disp(N,'Round off value of N=');

//Cut off frequency 
omegac=omegap/(((10^(0.1*alphap)) -1)^(1/(2* N))); 
disp(omegac,'omegac='); 
 
disp('Normalised Analog LPF Transfer function H(S)='); 
hs_Normalised = analpf(N,'butt',[0,0],1); 
disp(hs_Normalised); 
 
disp('Analog LPF Transfer function H(S)='); 
hs= analpf(N,'butt',[0,0],omegac); 
disp(hs); 
z=poly(0,'z');//Defining variable z 
Hz=horner(hs,(2/ T)*((z -1)/(z+1)))// Bilinear Transformation 
disp('Digital LPF Transfer function H(Z)='); 
disp(Hz);
HW=frmag(Hz,512); // Frequency response 
w=0:%pi/511:%pi ; 
plot(w/%pi,abs(HW)); 
xlabel(' Normalized Digital Frequency w'); 
ylabel('Magnitude ');
title(' Frequency Response of Butterworth IIR LPF');
~~~

# CALCULATION
<img width="899" height="1599" alt="image" src="https://github.com/user-attachments/assets/823ecad4-c7fc-4b8b-991c-ca415ae065d8" />
<img width="899" height="1599" alt="image" src="https://github.com/user-attachments/assets/14ae0ddc-dded-4eed-9cb8-e2ae9613bc69" />
<img width="899" height="1599" alt="image" src="https://github.com/user-attachments/assets/e403484e-d991-439f-ae93-0a8d5911627c" />
# OUTPUT
<img width="1398" height="1600" alt="image" src="https://github.com/user-attachments/assets/f4d44443-160e-4550-9e6d-e820222c5dd5" />
<img width="1300" height="1600" alt="image" src="https://github.com/user-attachments/assets/7fb18d43-27b1-4814-99f8-d4c5f97d7b50" />


# RESULT: 

Thus, design of Butterworth Low pass IIR filter waveforms were plotted and output was verified.

