# Radar-Range-Equation
# Aim
To calculate the maximum range of a radar system using the Radar Range Equation and verify the results through Scilab programming.

# Theory
The Radar Range Equation is a key relationship used in radar system design to determine the maximum distance (range) at which a radar can detect a target.

It is expressed as:
<img width="597" height="272" alt="image" src="https://github.com/user-attachments/assets/3485235b-abbb-4284-9c0a-7b008238a27f" />


# Algorithm
Initialize constants:

* λ (wavelength) = 0.03 m
* σ (radar cross section) = 1 m²
Vary each parameter while keeping the others constant:

* Pt: 0.1 → 10
* Gt: 1 → 50
* Pm: 1e⁻¹⁵ → 1e⁻¹⁰
Compute maximum range using: R_max = ((Pt * Gt² * λ² * σ) / ((4π)³ * Pm))¼

Plot the following:

* Pt vs Rmax
* Gt vs Rmax
* Pm vs Rmax
# Procedure
1.Refer to the Algorithm and write the Scilab code for the experiment.
2.Open Scilab on your system.
3.Create a New Editor File:
Go to File → New → Script.
4.Type Your Code in the editor window.
5.Save the File with a suitable name (e.g., radar_range.sce).
6.Execute the Code:
Press F5 or click Execute → File with echo.
7.If Any Errors Occur:
* Review and correct the code.
* Save and run it again until it executes successfully.
# Code
```
clc;
clear;
clf;
// Updated values (same trend preserved)
Gt = 30;
Gr = 25;
l = 0.03;
s = 5;
Pm = 5e-11;
K = (4 * %pi)^3;

// --------- Plot 1: Range vs Transmit Power ---------
Pt = 0:1:120;
x = Pt .* Gt .* Gr .* l .* l .* s;
y = K * Pm;
z = x ./ y;
R = z.^(1/4);

subplot(3,1,1);
plot(Pt, R);
xlabel('Transmit Power (W)');
ylabel('Range (m)');
title('Range vs Transmit Power');
xgrid();

// --------- Plot 2: Range vs Received Power ---------
Pr = 0:20:1500;
Pt_fixed = 30;
x = Pt_fixed .* Gt .* Gr .* l .* l .* s;
y = K .* Pr;
z = x ./ y;
R1 = z.^(1/4);

subplot(3,1,2);
plot(Pr, R1);
xlabel('Received Power (W)');
ylabel('Range (m)');
title('Range vs Received Power');
xgrid();

// --------- Plot 3: Range vs Antenna Gain ---------
G = 0:0.1:80;
Pm_fixed = 5e-11;
Pt_fixed = 30;
a = Pt_fixed .* G .* l .* l .* s;
b = K * Pm_fixed;
c = a ./ b;
R2 = c.^(1/4);

subplot(3,1,3);
plot(G, R2);
xlabel('Antenna Gain (G)');
ylabel('Range (m)');
title('Range vs Antenna Gain');
xgrid();
```
# Output
<img width="750" height="698" alt="image" src="https://github.com/user-attachments/assets/6496b265-7788-4aeb-8422-5815ea79c476" />


# Manual Calculation
![WhatsApp Image 2025-11-23 at 10 50 20_e5b34143](https://github.com/user-attachments/assets/3129f079-e68d-471b-916e-07e28868fdb1)

Result


Thus, the maximum range of a radar system calculated using the Radar Range Equation is successfully verified using Scilab programming.
