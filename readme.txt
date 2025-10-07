CLASS D AMPLIFIER 

	◦	Why Use LM393 in Triangle Wave Generation for Class D Amplifiers?

	◦	LM393 is a dual comparator IC, and in Class D amplifiers, triangle waves are used as a carrier signal for generating PWM (Pulse Width Modulation). LM393 plays a key role in this process.

	◦	Key Reasons:

	◦	1. Comparator-Based Oscillator

	◦	• LM393 can be configured as a Schmitt trigger oscillator to produce a square wave.
	◦	• This square wave is then passed through an RC integrator circuit to convert it into a triangle wave.


	◦	2. Fast Switching

	◦	• LM393 has fast response time and sharp transitions, which are ideal for generating clean PWM signals.
	◦	• This helps maintain fidelity and efficiency in Class D amplification.

	◦	 Resistor R1 used between Negative Feedback for Controlled Switching

	◦	If LM356 is acting as a signal source (say, a sine wave or ramp), and LM393 is used as a comparator, the resistor provides negative feedback to stabilize or shape the comparator’s response.

	◦	• Purpose: It prevents rapid toggling or noise-induced chatter near the threshold.
	◦	• Effect: Adds hysteresis—so LM393 doesn’t flip back and forth too easily.

	◦	Pull-Down or Biasing Role of resistor R1

	◦	If LM393’s −IN is floating or weakly driven, the resistor from LM356 output can pull it toward a known voltage, ensuring predictable behavior.

	◦	• Especially useful if LM356 output is high-impedance or not rail-to-rail.

	◦	R2 is also doing the same as it is connected  between output and inverting input of the op amp which is usually called as negative feedback and is used to stabilise the output by controlling input signal all this setup is made to get a clean signal output without noise. 

	◦	similarly capacitor C1 across output of lm356 is used  in positive feedback circuit  and its other function is to introduce hystresis because lm356 shift instantly which can effect our output signal in this case we are creating a triangle wave using schmitt trigger and integrator 

	◦	so C1 capacitor introduces a threshold value and when this threshold value is crossed both for raising input and falling input then it will allow for signal transition which will help us get great triangle wave at output without unwanted ripple near changing phase


	◦	Next this input is fed to our comparator Tl072 which compares our triangle wave and audio signal fed by audio jack and controls its output according to audio signal fed 

	◦	we have provided small value capacitor across each component which are acting as high frequency bypass circuit since Xc=1/2pieFC higher the frequency or ripple less will be the capacitance path and unwanted noise will get minimum resistance path to get out of our system which further increase our noise immunity in our circuit and signal which we get will be desired one without noise components

	◦	furthermore the output current component which we get out of our comparator is around 10 to 20mA but in order to drive our mosfet which are fitted in push pull configuration needs at least 200mA of current so feeding this PWM signal directly to MOSFET’S gate make no sense 
	◦	thats why we need a mosfet driver circuit with 2 major properties that it can charge and discharge mosfet gate capacitence easily so we get fast switching which is most crucial in class d amplifier since audio signal changes with time so our switching should follow


	◦	now when pwm high signals comes .Pnp bjt get forward biased as a result high side mosfet turns on and  while the second one being reversed biased gets discharged during the same process like that both of them charge and discharge simultaneously achieving efficient switching function in accordance with pwm wave fed 


	◦	but still there i one problem here we need to introduce some delay between the switching of 2 mosfet so that their output does not overlap which we can see under oscilloscope so in order to do so we had introduced RC delay circuit between our MOSFET’s so the voltage across mosfet will rise gradually since capacitor current component lags voltage in short phase difference 

	◦	Output is fed to the LC circuit which smoothens the sharp edges of pwm signal thus converting it to ac signal which can be fed to our load.

	◦	CONCLUSION- By applying this logic i have tried to make a class d amplifier .I hope my approach will get us a working class d amplifier prototype 
	◦	PCB DESIGN emf/DFM
	◦	I  have made all my tracks under 60degree in order to prevent signal loss
	◦	for power supply my traces width are 1mm and for signals its around 0.5mm so each signal  can travel easily without generating heat in our pcb 
	◦	Heat generating components are iched on outside boundaries of pcb taking into consideration IPC-2221 standards 
	◦	emc introducing components such as inductor are also placed at outer edges of pcb boundaries so it can not disturb signal traces which can further induce noise in our circuit making them less efficient 
	◦	furthermore in order to make mosfet more efficient we can connect heat sinks with mosfet as their placement is optimal following IPC-2221 standards 
