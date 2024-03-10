# Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-
DESIGN OF A BCD TO SEVEN SEGMENT CODE CONVERTER USING PSEUDO NMOS LOGIC IN CADENCE USING GPDK90 LIBRARY


Contents:


-> Introduction


-> Logic circuit Design


-> SCHEMATIC DESIGN


->INPUTS AND OUTPUTS
# Introduction:		
A seven-segment display is used to display digits from 0 to 9 


These displays are more frequently used when we have to obtain output only in the form of digits like a digital clock or digital speedometer etc.


This seven segment LED display has seven individual LEDs and these displays are available in two forms one is the common cathode display and the other one is common anode display.


In common cathode display all the seven LEDs cathodes are tied together and anodes are individually controlled through the display controller IC to display the required digit.
Similarly in common anode display all the seven LEDs anodes are tied together and cathodes are individually controlled.

![image](https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/b1a0cec9-5c9e-4496-90b5-cc713f1513b5)


In this seven segment LED display along with the seven segments there is another eighth segment for the purpose of representing the decimal point but most of the times it is not used.
# Logic circuit Design:
Here in this project the circuit is designed only for valid BCD codes i.e. 0-9.
 Invalid BCD codes are taken as don’t cares i.e. A-F.


The truth table is taken as follows,


For Common cathode display where ABCD is the BCD code (A is MSB)


<img width="461" alt="table1" src="https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/4fedb297-b435-4cf1-9b91-40378f37a9a9">


Now, in order to design the logic circuit for controlling this this seven-segment display we need to solve the k map for each of the seven functions a, b , c , d , e , f ,g. 
Solving K-map for function a:
	

![image](https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/a527ddc9-0bec-4ee6-a251-012e5dc3a6c7)



a= A + C + BD + B’D’


on following the similar procedure for solving the k-maps for the other functions also we obtain the following final expressions


b=A + B’ + C’D’ + CD


c=C’ + D +B


d=A + CD’ + B’D’ + B’CD + BC’D


e=B’D’ + CD’


f=A + BC’ + A’C’D’ + BCD’


g=A + BC’ + CD’ + B’C


now in order to implement these functions using the pseudo nmos logic we need to convert these expressions to expressions that come out as an output in complementary form like below
These conversions are required in order to reduce one inverter for each function.

  
a=     ~( A’C’ (B + D) (B’ + D’) )	


b=	~(A’B (C + D) (C’ + D’))
	
	
c=	~( CD’B )
	
 
d=	~( A’ (C’ + D) (B + D) (B + C’ + D’) (B’ + C + D’) )

 
e=	~( (B +D) (C’ + D) )

 
f=	~( A’ (B’ + C) (A + C + D) (B’ + C’ +D) )

 
g=	~( A’ (B’ + C) (C’ + D) (B + C’) )


In this project the IC design is completed up to Schematic and testing by giving appropriate inputs.



Now, the logic circuit is taken as follows


![image](https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/7bb50f71-1829-461c-8068-489c5cee9a08)
