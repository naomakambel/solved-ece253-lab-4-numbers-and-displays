Download Link: https://assignmentchef.com/product/solved-ece253-lab-4-numbers-and-displays
<br>
This is an exercise in designing combinational circuits that can perform binary-to-decimal number conversion and binary-coded-decimal (BCD) addition.

Preparation marks for this lab: 1 mark for verilog code for each of Parts I through IV. Also, 1 mark in total for simulation results of just Parts II and III.

In-Lab marks: 2 marks for Part III, 3 marks Part IV. One bonus mark is available for Part V.

<h1>Part I</h1>

We wish to display on the 7-segment displays <em>HEX1 </em>and <em>HEX0 </em>the values set by the switches <em>SW</em><sub>7−0</sub>. Let the values denoted by <em>SW</em><sub>7−4 </sub>and <em>SW</em><sub>3−0 </sub>be displayed on <em>HEX1 </em>and <em>HEX0</em>, respectively. Your circuit should be able to display the digits from 0 to 9, and should treat the valuations 1010 to 1111 as don’t-cares.

<ol>

 <li>Create a new project which will be used to implement the desired circuit on the Altera DE1-SoC board. Theintent of this exercise is to manually derive the logic functions needed for the 7-segment displays. Therefore, you should use only simple Verilog assign statements in your code and specify each logic function as a Boolean expression.</li>

 <li>Write a Verilog file that provides the necessary functionality. Include this file in your project and assign thepins on the FPGA to connect to the switches and 7-segment displays. Make sure to include the necessary pin assignments.</li>

 <li>Compile the project and download the compiled circuit into the FPGA chip.</li>

 <li>Test the functionality of your design by toggling the switches and observing the displays.</li>

</ol>

<h1>Part II</h1>

You are to design a circuit that converts a four-bit binary number <em>V </em>= <em>v</em><sub>3</sub><em>v</em><sub>2</sub><em>v</em><sub>1</sub><em>v</em><sub>0 </sub>into its two-digit decimal equivalent <em>D </em>= <em>d</em><sub>1</sub><em>d</em><sub>0</sub>. Table 1 shows the required output values. A partial design of this circuit is given in Figure 1. It includes a comparator that checks when the value of <em>V </em>is greater than 9, and uses the output of this comparator in the control of the 7-segment displays. You are to complete the design of this circuit.

<table width="128">

 <tbody>

  <tr>

   <td width="66"><em>v</em>3<em>v</em>2<em>v</em>1<em>v</em>0</td>

   <td width="39"><em>d</em><sub>1</sub></td>

   <td width="23"><em>d</em><sub>0</sub></td>

  </tr>

  <tr>

   <td width="66">0000</td>

   <td width="39">0</td>

   <td width="23">0</td>

  </tr>

  <tr>

   <td width="66">0001</td>

   <td width="39">0</td>

   <td width="23">1</td>

  </tr>

  <tr>

   <td width="66">0010</td>

   <td width="39">0</td>

   <td width="23">2</td>

  </tr>

  <tr>

   <td width="66"><em>…</em></td>

   <td width="39"><em>…</em></td>

   <td width="23"><em>…</em></td>

  </tr>

  <tr>

   <td width="66">1001</td>

   <td width="39">0</td>

   <td width="23">9</td>

  </tr>

  <tr>

   <td width="66">1010</td>

   <td width="39">1</td>

   <td width="23">0</td>

  </tr>

  <tr>

   <td width="66">1011</td>

   <td width="39">1</td>

   <td width="23">1</td>

  </tr>

  <tr>

   <td width="66">1100</td>

   <td width="39">1</td>

   <td width="23">2</td>

  </tr>

  <tr>

   <td width="66">1101</td>

   <td width="39">1</td>

   <td width="23">3</td>

  </tr>

  <tr>

   <td width="66">1110</td>

   <td width="39">1</td>

   <td width="23">4</td>

  </tr>

  <tr>

   <td width="66">1111</td>

   <td width="39">1</td>

   <td width="23">5</td>

  </tr>

 </tbody>

</table>

Table 1. Binary-to-decimal conversion values.

The output <em>z </em>for the comparator circuit can be specified using a single Boolean expression, with the four inputs <em>V</em><sub>3−0</sub>. Design this Boolean expression by making a truth table that shows the valuations of the inputs <em>V</em><sub>3−0 </sub>for which <em>z </em>has to be 1.

Notice that the circuit includes a 4-bit wide 2-to-1 multiplexer (a similar multiplexer was described as part of Laboratory Exercise 1). The purpose of this multiplexer is to drive digit <em>d</em><sub>0 </sub>with the value of <em>V </em>when <em>z </em>= 0, and the value of <em>A </em>when <em>z </em>= 1. To design circuit <em>A </em>consider the following. For the input values <em>V </em>≤ 9, the circuit <em>A </em>does not matter, because the multiplexer in Figure 1 just selects <em>V </em>in these cases. But for the input values <em>V &gt; </em>9, the multiplexer will select <em>A</em>. Thus, <em>A </em>has to provide output values that properly implement Table 1 when <em>V &gt; </em>9. You need to design circuit <em>A </em>so that the input <em>V </em>= 1010 gives an output <em>A </em>= 0000, the input <em>V </em>= 1011 gives the output <em>A </em>= 0001, <em>…</em>, and the input <em>V </em>= 1111 gives the output <em>A </em>= 0101. Design circuit <em>A </em>by making a truth table with the inputs from <em>V </em>and the outputs <em>A</em><sub>3−0</sub>.

Perform the following steps:

<ol>

 <li>Write Verilog code to implement your design. The code should have the 4-bit input <em>SW</em><sub>3−0</sub>, which should be used to provide the binary number <em>V </em>, and the two 7-bit outputs <em>HEX1 </em>and <em>HEX0</em>, to show the values of decimal digits <em>d</em><sub>1 </sub>and <em>d</em><sub>0</sub>. The intent of this exercise is to use simple Verilog assign statements to specify the required logic functions using Boolean expressions. Your Verilog code should not include any if-else, case, or similar statements.</li>

 <li>Make a Quartus project for your Verilog module.</li>

 <li>Compile the circuit and use functional simulation to verify the correct operation of your comparator, multiplexers, and circuit <em>A</em>.</li>

 <li>Download the circuit into an FPGA board. Test the circuit by trying all possible values of <em>V </em>and observing the output displays.</li>

</ol>

Figure 1: Partial design of the binary-to-decimal conversion circuit.

<h1>Part III</h1>

Figure 2<em>a </em>shows a circuit for a <em>full adder</em>, which has the inputs <em>a</em>, <em>b</em>, and <em>c<sub>i</sub></em>, and produces the outputs <em>s </em>and <em>c<sub>o</sub></em>. Parts <em>b </em>and <em>c </em>of the figure show a circuit symbol and truth table for the full adder, which produces the two-bit binary sum <em>c<sub>o</sub>s </em>= <em>a </em>+ <em>b </em>+ <em>c<sub>i</sub></em>. Figure 2<em>d </em>shows how four instances of this full adder module can be used to design a circuit that adds two four-bit numbers. This type of circuit is usually called a <em>ripple-carry </em>adder, because of the way that the carry signals are passed from one full adder to the next. Write Verilog code that implements this circuit, as described below.

<ol>

 <li>a) Full adder circuit b) Full adder symbol</li>

</ol>

<table width="85">

 <tbody>

  <tr>

   <td width="55"><em>b a c<sub>i</sub></em></td>

   <td width="31"><em>c<sub>o</sub></em></td>

  </tr>

  <tr>

   <td width="55">0 0 00 0 10 1 00    1 11    0 01 0 11 1 01 1 1</td>

   <td width="31">00010   1111   1</td>

  </tr>

 </tbody>

</table>

<em>s</em>

0

1

1

0

0

0

<ol>

 <li>c) Full adder truth table d) Four-bit ripple-carry adder circuit</li>

</ol>

Figure 2: A ripple-carry adder circuit.

<ol>

 <li>Create a new Quartus project for the adder circuit. Write a Verilog module for the full adder subcircuit andwrite a top-level Verilog module that instantiates four instances of this full adder.</li>

 <li>Use switches <em>SW</em><sub>7−4 </sub>and <em>SW</em><sub>3−0 </sub>to represent the inputs <em>A </em>and <em>B</em>, respectively. Use <em>SW</em><sub>8 </sub>for the carry-in <em>c<sub>in </sub></em>of the adder. Connect the outputs of the adder, <em>c<sub>out </sub></em>and <em>S</em>, to the red lights LEDR.</li>

 <li>Include the necessary pin assignments for the DE1-SoC board, compile the circuit, and download it into theFPGA chip.</li>

 <li>Test your circuit by trying different values for numbers <em>A</em>, <em>B</em>, and <em>c<sub>in</sub></em>.</li>

</ol>

<h1>Part IV</h1>

In part II we discussed the conversion of binary numbers into decimal digits. For this part you are to design a circuit that has two decimal digits, <em>X </em>and <em>Y </em>, as inputs. Each decimal digit is represented as a 4-bit number. In technical literature this is referred to as the <em>binary coded decimal </em>(BCD) representation.

You are to design a circuit that adds the two BCD digits. The inputs to your circuit are the numbers <em>X </em>and <em>Y </em>, plus a carry-in, <em>c<sub>in</sub></em>. When these inputs are added, the result will be a 5-bit binary number. But this result is to be displayed on 7-segment displays as a two-digit BCD sum <em>S</em><sub>1</sub><em>S</em><sub>0</sub>. For a sum equal to zero you would display <em>S</em><sub>1</sub><em>S</em><sub>0 </sub>= 00, for a sum of one <em>S</em><sub>1</sub><em>S</em><sub>0 </sub>= 01, for nine <em>S</em><sub>1</sub><em>S</em><sub>0 </sub>= 09, for ten <em>S</em><sub>1</sub><em>S</em><sub>0 </sub>= 10, and so on. Note that the inputs <em>X </em>and <em>Y </em>are assumed to be decimal digits, which means that the largest sum that needs to be handled by this circuit is <em>S</em><sub>1</sub><em>S</em><sub>0 </sub>= 9+9+1 = 19. Perform the steps given below.

<ol>

 <li>Create a new Quartus project for your BCD adder. You should use the four-bit adder circuit from part III toproduce a four-bit sum and carry-out for the operation <em>X </em>+ <em>Y </em>.</li>

</ol>

A good way to work out the design of your circuit is to first make it handle only sums (<em>X </em>+<em>Y </em>) ≤ 15. With these values, your circuit from Part II can be used to convert the 4-bit sum into the two decimal digits <em>S</em><sub>1</sub><em>S</em><sub>0</sub>. Then, once this is working, modify your design to handle values of 15 <em>&lt; </em>(<em>X </em>+ <em>Y </em>) ≤ 19. One way to do this is to still use your circuit from Part II, but to modify its outputs before attaching them to the 7-segment display to make the necessary adjustments when the sum from the adder exceeds 15.

Write your Verilog code using simple assign statements to specify the required logic functions–do not use other types of Verilog statements such as if-else or case statements for this part of the exercise.

<ol start="2">

 <li>Use switches <em>SW</em><sub>7−4 </sub>and <em>SW</em><sub>3−0 </sub>for the inputs <em>X </em>and <em>Y </em>, respectively, and use <em>SW</em><sub>8 </sub>for the carry-in. Connect the four-bit sum and carry-out produced by the operation <em>X </em>+ <em>Y </em>to the red lights LEDR. Display the BCD values of <em>X </em>and <em>Y </em>on the 7-segment displays <em>HEX5 </em>and <em>HEX3</em>, and display the result <em>S</em><sub>1</sub><em>S</em><sub>0 </sub>on <em>HEX1 </em>and <em>HEX0</em>.</li>

 <li>Since your circuit handles only BCD digits, check for the cases when the input <em>X </em>or <em>Y </em>is greater than nine. If this occurs, indicate an error by turning on the red light <em>LEDR</em><sub>9</sub>.</li>

 <li>Include the necessary pin assignments for the DE1-SoC board, compile the circuit, and download it into theFPGA chip.</li>

 <li>Test your circuit by trying different values for numbers <em>X</em>, <em>Y </em>, and <em>c<sub>in</sub></em>.</li>

</ol>

<h1>Part V</h1>

In part IV you created Verilog code for a BCD adder. A different approach for describing the adder in Verilog code is to specify an algorithm like the one represented by the following pseudo-code:

<ul>

 <li><em>T</em><sub>0 </sub>= <em>A </em>+ <em>B </em>+ <em>c</em><sub>0</sub></li>

 <li>if (<em>T</em><sub>0 </sub><em>&gt; </em>9) then</li>

 <li><em>Z</em><sub>0 </sub>= 10;</li>

 <li><em>c</em><sub>1 </sub>= 1;</li>

 <li>else</li>

 <li><em>Z</em><sub>0 </sub>= 0;</li>

 <li><em>c</em><sub>1 </sub>= 0;</li>

 <li>end if</li>

 <li><em>S</em><sub>0 </sub>= <em>T</em><sub>0</sub>− <em>Z</em><sub>0</sub></li>

 <li><em>S</em><sub>1 </sub>= <em>c</em><sub>1</sub></li>

</ul>

It is reasonably straightforward to see what circuit could be used to implement this pseudo-code. Lines 1 and 9 represent adders, lines 2-8 correspond to multiplexers, and testing for the condition <em>T</em><sub>0 </sub><em>&gt; </em>9 requires comparators. You are to write Verilog code that corresponds to this pseudo-code. Note that you can perform addition operations in your Verilog code instead of the subtraction shown in line 9. The intent of this part of the exercise is to examine the effects of relying more on the Verilog compiler to design the circuit by using if-else statements along with the Verilog <em>&gt; </em>and + operators. Perform the following steps:

<ol>

 <li>Create a new Quartus project for your Verilog code. Use switches <em>SW</em><sub>7−4 </sub>and <em>SW</em><sub>3−0 </sub>for the inputs <em>A </em>and <em>B</em>, respectively, and use <em>SW</em><sub>8 </sub>for the carry-in. The value of <em>A </em>should be displayed on the 7-segment display <em>HEX5</em>, while <em>B </em>should be on <em>HEX3</em>. Display the BCD sum, <em>S</em><sub>1</sub><em>S</em><sub>0</sub>, on <em>HEX1 </em>and <em>HEX0</em>.</li>

 <li>Use the Quartus RTL Viewer tool to examine the circuit produced by compiling your Verilog code. Comparethe circuit to the one you designed in Part IV.</li>

 <li>Download your circuit onto the DE1-SoC board and test it by trying different values for numbers <em>A </em>and <em>B</em>.</li>

</ol>