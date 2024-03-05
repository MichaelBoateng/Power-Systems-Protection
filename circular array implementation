%Michael Boateng
%This code utilises the circular array implementation for 
% phasor computation

n=readmatrix('Homework_2_Spring_2024');

count=n(:,1)';
time=n(:,2)';
T=(1/9600.06144);
s1=[]; 
s2=[]; 
voltage=[];
current=[];

%Actual voltage and current sample was derived by v(k)=a*d(k) + b
voltage=[voltage (2.7629898265.*(n(:,3))+1.0439283977)]';
current=[current (5.3212752722e-03.*(n(:,4))+3.4031605102e-02)]';


% Preallocate arrays for efficiency
s1 = zeros(1, 52241);  
s2 = zeros(1, 52241);

%Question: 4-6
%Fourier implementation
for i = 1:52241
a = 0;
b = 0;
for j = 1:160
a=a + voltage(I+j).*cos(2*pi*60*time(i+j).*(10^-6));
b=b + voltage(I+j).*sin(2*pi*60*time(i+j).*(10^-6));

end

s1(i)=a;
s2(i)=b;

end

V1 = [];
V2 = [];

for i =1:52241
    V1(i)=(sqrt(2)/160)*s1(i);
    V2(i)=(sqrt(2)/160)*s2(i);  
end

Magnitude = [];
Phase = [];

for i =1:52241
    Magnitude= [Magnitude sqrt(V1(i)^2 + V2(i)^2)];
    Phase=[Phase atan(-(V2(i)/V1(i)))];  
end

Frequency = [];
for i =1:52240
    Frequency=[Frequency (60 + (Phase(i+1)-Phase(i))/(2*pi*T))];
end


%Graphs for voltage, magnitude, phase and frequency
%To find Question:7 (current), this time the current matrix is used
%in the initial fourier transformation


figure (1)
time=time*10^-6;
plot(time, voltage);
grid on
xlabel('time (us)');
ylabel('Voltage (V)');
axis([0 5.5 inf inf])

figure (2)
time=(time(1:52240))*10^-6;
plot(time,Frequency);
grid on
xlabel('time (us)');
ylabel('Frequency (Hz)');
axis([0 5.5 59.8 60.2])

figure (3)
time=(time(1:52241))*10^-6;
plot(time,Magnitude);
grid on
xlabel('time (us)');
ylabel('Magnitude');
axis([0 5.5 inf inf])

figure (4)
time=(time(1:52241))*10^-6;
plot(time,Phase);
grid on
xlabel('time (us)');
ylabel('Phase (rad)');
axis([0 5.5 inf inf])
