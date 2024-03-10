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

  
a=     ( A’C’ (B + D) (B’ + D’) )'	


b=	(A’B (C + D) (C’ + D’))'
	
	
c=	( CD’B )'
	
 
d=	( A’ (C’ + D) (B + D) (B + C’ + D’) (B’ + C + D’) )'

 
e=	( (B +D) (C’ + D) )'

 
f=	( A’ (B’ + C) (A + C + D) (B’ + C’ +D) )'

 
g=	( A’ (B’ + C) (C’ + D) (B + C’) )'


In this project the IC design is completed up to Schematic and testing by giving appropriate inputs.



Now, the logic circuit is taken as follows


![image](https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/7bb50f71-1829-461c-8068-489c5cee9a08)


# SCHEMATIC DESIGN
Here there are 7 outputs (a, b, c, d, e, f, g) and four inputs (A, B, C, D)


Here one subcircuit is used for taking inputs and also the complements of these inputs by making use of inverters.


The inverter is designed in such a way that the W/L ratio of the pmos is 2.5 times the W/L ratio of nmos transistor for the purpose of proper switching voltage (0.5 VDD).


The schematic of the basic inverter used in this project is as shown below.


Transistor dimensions table:


![image](https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/4e889b76-38f5-4dd8-b3a5-57fa9356bcb0)


INVERTER:

![image](https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/aadf5e49-d874-4342-9f60-7b8a286c1fc4)


INVERTER SYMBOL:


![image](https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/4b90713e-5742-4018-9208-dce6939570a6)


Now by making use of these inverters the inputs subcircuit is designed as shown below.


INPUTS SUBCIRCUIT:


![image](https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/e624a198-8a47-446b-b57b-d43b1937e638)


Now each of the output an individual subcircuit is designed by using pseudo nmos logic where single pmos is used as pull up network and nmos transistors are used according to the required logic as pull-down network.


Here an additional pin CKCA’ is used to select the common cathode (CACK’=0) or common anode (CKCA’=1) operation of the IC. For this purpose xor gates are employed to take the final output. 


For these xor gates one of the inputs is CKCA’ and the other input is the output of the subcircuit whenever the CKCA’ is logic ‘0’ it will allow the outputs to pass without any changes and achieving the common cathode mode of operation.


Also, whenever the CKCA’ is logic ‘1’ it will give the complements of the outputs of the subcircuit, by this it achieves the common anode mode of operation.


The exor gate is also designed by using pseudo nmos logic, for obtaining the good enough noise margin the W/L ratio of the NMOS transistors are taken 6 times the W/L ratio of the PMOS transistor.


The schematic of the basic xor used in this project is as shown below.


Transistor dimensions table:


![image](https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/0ff313c1-7d47-4c41-8b2d-63e9282c01fa)


SCHEMATIC XOR GATE:


![image](https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/3e434193-5fbf-4553-b9fe-b59684486eeb)


XOR SYMBOL:


![image](https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/e2c08c56-a787-4874-9220-ab61b9d67728)


Now by making use of these inverters and the pseudo NMOS logic the subcircuit for output a is designed as shown below.


Transistor dimensions table:


![image](https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/b23e87f0-f71f-42c6-9885-eca7448aa162)


SCHEMATIC OF SUBCIRCUIT a:


![image](https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/374b7826-5cff-4943-82a6-3c5ef0a9dbe4)


a=     ( A’C’ (B + D) (B’ + D’) )'	


SCHEMATIC OF SUBCIRCUIT b:


![image](https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/5cc6b946-fd90-44e7-9324-76ce9ef55afb)


b=	(A’B (C + D) (C’ + D’))'


SCHEMATIC OF SUBCIRCUIT c:


![image](https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/897066fa-44aa-4455-aa57-c15fd3a31dfa)


c=	( CD’B )'


SCHEMATIC OF SUBCIRCUIT d:


![image](https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/225109b4-7844-4a3b-b255-86bc25bb03bc)


d=	( A’ (C’ + D) (B + D) (B + C’ + D’) (B’ + C + D’) )'


SCHEMATIC OF SUBCIRCUIT e:


![image](https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/aceb4e00-60e8-4a38-b9a7-eb10f1227a35)


e=	( (B +D) (C’ + D) )'


SCHEMATIC OF SUBCIRCUIT f:

![image](https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/d60a7bf7-6609-4679-bf99-0a2d6915b8dd)


f=	( A’ (B’ + C) (A + C + D) (B’ + C’ +D) )'


SCHEMATIC OF SUBCIRCUIT g:


![image](https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/f52fc4db-8504-4ca3-a327-91e3f9dc60fc)


g=	( A’ (B’ + C) (C’ + D) (B + C’) )'


THE ENTIRE DESIGN:


![image](https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/e2d75197-8e58-4695-bc55-d3bcbf5edac2)


SYMBOL OF THE BCD TO SEVEN SEGMENT CODE CONVERTER IC:


![image](https://github.com/vishveshgoud/Design-of-BCD-to-Seven-segment-code-converter-using-pseudo-NMOS-logic-/assets/147975068/a9ef6ce5-61c7-4830-8110-84a972a28a86)


