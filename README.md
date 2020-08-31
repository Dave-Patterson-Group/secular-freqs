# secular-freqs
Programs that quickly approximate the secular frequencies in the Paul trap and whale trap potentials, and quantify how harmonic they are.
Each program will calculate the DC potential + RF pseudopotential for whatever voltages you input into it, then will plot that potential near the trap center, for both the axial and radial potentials. It will calculate a best-fit harmonic potential, plot it on the same graph, and calculate the secular frequency of a strontium ion in that potential. It will also calculate the sum of squared residuals between the true potential and best-fit harmonic, as a measure of how close the potential is to harmonic. It will list the frequency and SSR at the top of each generated graph.

The inputs of each function are the DC electrode voltages, the RF amplitude, and the RF frequency. For the Paul trap, we assume that each top electrode is assumed to be connected with each bottom electrode. So, we have 5 DC potentials to input, the far left electrodes, the left electrodes, the center electrodes, the right electrodes, and the far right electrodes. For the whale trap, we assume the DC electrodes are at the same voltage, so we only have 1 DC potential to input. 

To calculate Paul trap secular frequencies, all you need to do is type the following into the command line:

paulCalcSecularFreqs(Vfarleft,Vleft,Vcenter,Vright,Vfarright,RFamplitude,RFfrequency);

Where you replace each variable with whatever value you want. The units of the voltages and RF amplitude are in volts, and the RF frequency is in Hz. If you wanted to calculate the secular frequencies with 60 V on the far left, left, right, and far right electrodes, 0 V on the center electrodes, 100 V RF amplitude, and 2 MHz RF frequency, you would input the following:

paulCalcSecularFreqs(60,60,0,60,60,100,2e6);


To calculate whale trap secular frequencies, you type:

whaleCalcSecularFreqs(VDCelectrodes,RFamplitude,RFfrequency);

If you wanted to put, say 1 V on the DC electrodes, 100 V for the RF amplitude, and 2 MHz for the RF frequency, you would type:

whaleCalcSecularFreqs(1,100,2e6);

A warning, if you input voltages such that you don't have a stable equilibrium point in the center such as 

paulCalcSecularFreqs(60,60,60,60,60,150,2e6);

Then it will throw an error (and/or give weird results), in this case because the axial potential is no longer a harmonic stable equilibrium. So, keep the physics in mind when you're calculating secular frequencies, don't just put random voltages into the functions.
