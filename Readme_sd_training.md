## Table of contents

+ **[ Day_0 : System/Tool Setup Check & GitHub ID creation ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_0)**
+ **[ Day_1 : Introduction to Verilog RTL design and Synthesis ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_1)**
+ **[ Day_2 : Timing libs(QTMs/ETMs), hierarchical vs flat synthesis and efficient flop coding styles ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_2)**  
+ **[ Day_3 : Combinational and sequenial optimizations ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_3)** 
+ **[ Day_4 : GLS, blocking vs non-blocking and Synthesis-Simulation mismatch ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_4)** 
+ **[ Day_5 : DFT ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_5)**
+ **[ Day_6 : Introduction to Logic Synthesis ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_6)**
+ **[ Day_7 : Basics of STA ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_7)**
+ **[ Day_8 : Advanced SDC Constraints ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_8)**
+ **[ Day_9 : Optimization in synthesis ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_9)**
+ **[ Day_10 : QOR ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_10)** 
+ **[ Day_11 : Introduction to the BabySoC ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_11)** 
+ **[ Day_12 : BabySoC Modelling ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_12)**
+ **[ Day_13 : Post-synthesis simulation ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_13)**
+ **[ Day_14 : Synopsys DC and timing analysis ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_14)**

#
# Day_0 
**⭐System/Tool Setup Check & GitHub ID creation**

<details><summary> ⚡ Lecture Session: System/Tool Setup Check. GitHub ID creation - Live session </summary>

### *__Lecture Session__*

**(A) Introduction on Package**

1. IC packaging refers to the material that contains a semiconductor device
2. The wafer level chip scale package (WLCSP) is a variant of the flip-chip interconnection technique where all packaging is done at the wafer level. With WLCSPs, the active side of the die is inverted and connected to the printed circuit board (PCB) using solder balls  
<img width="301" alt="packagetype" src="https://user-images.githubusercontent.com/118953915/203907496-1f4e1038-a868-402e-9e2d-ecaf64505b54.PNG" width=20& height=20%>
 (i) QFN (Quad flat no-lead package) is a leadless package that comes in small size and offers moderate heat dissipation in PCBs <-popular

 (ii) QFP{Quad flat package) is a surface-mounted integrated circuit package with "gull wing" leads extending from each of the four sides.  
<img width="301" alt="package3" src="https://user-images.githubusercontent.com/118953915/203914693-f3ca5866-f174-429c-8297-9e432c957e43.PNG">  

3. Details on architecture:   
(i) Wire board- Connect chip (Wire bonding is the process of creating electrical interconnections between semiconductors (or other integrated circuits) and silicon chips)    
(ii) I/O Pads-Intermediate structures connecting internal signals from the core of the integrated circuit to the external pins of the chip package  
(iii) Core-All fundamental logic of the design (eg: AND gates,pnoms,...) is placed  
(iv) Die-Consists of core, is small semiconductor material specimen on which the fundamental circuit is fabricated  
(v) IP core (intellectual property core)-functional block of logic or data used to make a field-programmable gate array (FPGA) or application-specific integrated circuit for a product (Eg of Foundry IPis: PLL (phase lock loop), SRAM,..)  
(vi) Macros-IP which is available in google that can directly use in own design (eg:memories, CBB(custom building block))


**(B) Concept on communication Software & Hardware**
1. Synthesis is process of transferring higher level of abstraction (RTL) to implementable lower level of abstraction.  
--> It is the process of transforming RTL to gate-level netlist  
2. Compiler will translate a high level programming language's source code (Java/C++) into machine level language code  
3. Assembler is a program that takes basic computer instructions and converts them into a pattern of bits that the computer's processor can use to perform its basic operations (in binary form)

Here is the Overview that show by instructor:  
![Concept](https://user-images.githubusercontent.com/118953915/203926658-55d68a6b-4f1e-4df3-9111-595c4a44e531.png)

</details>

<details><summary> Lab Session -> Lab0: Setup Lab </summary>

### *__Lab Session__*

Setup directory and invoke icc2

>Lab steps: [DAY_0..txt](https://github.com/ChianNi/Intel_SD_Training/files/10088800/DAY_0.txt)

Here is the screenshot of lab final outputs:

![day_0](https://user-images.githubusercontent.com/118953915/203699203-8f3cccc3-8cdc-4494-a25d-3d6e29c3d7ba.JPG)

</details>

#
# Day_1   
**⭐Introduction to Verilog RTL design and Synthesis**

<details><summary> ⚡Lecture Session: Introduction to Verilog RTL design and Synthesis </summary>
 
### *__Lecture Session__*

**(A) Introduction to open-source simulator iverilog**
>Course Website -> https://vsdiat.com/course_content?uniqueid=20220801054525  
1. Simulator --> Will use iverilog for this training onwards  
Tool for checking RTL design (implementation of spec) by simulating the design (looks for changes on the input signals and output is evaluated. If no changes in input then output also will not have any changes)  
-Design: Verilog codes which has the intended functionality to meet with the required specifications  
-TestBench (TB): setup to apply stimulus (test_vectirs) to the design to checks its functionality by observe the outputs whether obeys to the spec of the design  
Design+Test Bench --> iverilog --> vcd file (value chnage dump format-looking for changes in value) -> gtkwave (this use to view output)

</details>
<details><summary> Lab Session -> Lab1: Introduction to lab </summary>

### *__Lab Session__*
#### *Lab1: Introduction to lab*  
Command to install workshop-> git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git  
<img width="600" alt="lab1" src="https://user-images.githubusercontent.com/118953915/205265411-2feb1121-9cdd-44d7-9120-36c80d5741d9.PNG">  
In the directory consists:
my_lib: contain library files (lib-contain std cell for synthesis in .lib and verlog_model-contain std cell verilog model in .v)
verilog_files: contain verilog source file and testbench file
</details>
<details><summary> Lab Session -> Lab2: Introduction iverilog gtkwave </summary>
 
#### *Lab2: Introduction iverilog gtkwave part 1*  
Steps:     
(i) Load mux to stimulator-> iverilog good_mux.v tb_good_mux.v , then new file created: a.out    
(ii) Execute this new created file from (i)-> ./a.out, then will dump out tb_good_mux.vcd     
<img width="600" alt="lab1l" src="https://user-images.githubusercontent.com/118953915/205426153-fbd574f1-4bf7-4175-b545-fb752fcaa235.png">  
(iii) Click the design and drag the signals into the window and click "Zoom Fit" on the toolbar     
<img width="600" alt="lab1b" src="https://user-images.githubusercontent.com/118953915/205270195-f6e6eb96-0ca4-413d-90a4-fd6cf33dd718.PNG">  
From the waveform: When the sel is "1", the output(y) will follow the input(i1)
 
*Lab2: Introduction iverilog gtkwave part 2*  
Understanding the content:  
vi tb_good_mux.v & vi good_mux.v (suppose is this command->gvim tb_good_mux.v -o good_mux.v)
![lab1e](https://user-images.githubusercontent.com/118953915/205290366-3d96a298-204f-4172-a602-1502fe829a66.png)  
testbench no primary input and output, but got design instantiate- UUT (Unit under test) or DUT (Design under test)

</details>
<details><summary> ⚡Lecture Session: Introduction to Yosys and Logic synthesis </summary>
 
### *__Lecture Session__*

**(B) Introduction to Yosys and Logic synthesis**
1. Synthesizer --> Will use Yosys for this training onwards  
Tool used for converting the RTL to netlist (in the form of std cell)
2. Design + .lib --> yosys --> netlist file  
Use read_verilog to read the Design ; Use read_liberty to read .lib ; write_verilog to write the netlist file  
3. Verify the synthesis  
Design+Test Bench --> iverilog --> vcd file -> gtkwave  
--> must ensure same as output observed during RTL simulation
4. The set of primary inputs/outputs will remain the same between the RTL design and synthesize netlist -> same test bench can be used  
5. RTL design: Behavioral representation of the required specification  
RTL Code (Verilog HDL) --> Digital logic circuit (hardware circuit)  
6. RTL to gate level translation - design converted into gates and the connections are made between the gates, output file: netlist  
7. Collection of logical modules in formal .lib  
-basic logix gates: AND,OR,...  
-different floavors of same gate: 2 input AND gate, 3 input AND gate, slow/medium/fast...
8. Combinational delay in logic path determines the max speed of operation of digital logic circuit  
(i) Fast cell needed to meet setup:
Tclk> TF1+Tcombi+TsetupofF2 (data must be stable before the capturing edge of clock)  
fclkmax=1/Tclkmin (low period==high freq==fast speed==max performance, so means delay must less, must faster cell, Tcombi must less)    
(i) Slow cell needed to meet hold
TholdF2<TF1+Tcombi  
so the .lib will have various collection of logical modules with difference behaviour  
9. Load in digital logic circuit is capacitance  
-Faster the charging/discharging of capacitance, lesser the propagation delay  
 -so need transistors capable of sourcing more current (wider transistors==low delay==more area&power<- not good)  
10. Need to guide the syn thesizer to select the flavour of cells that is optimum fo rthe implementation of logic circuit  
fast cell-> comsume high power and area, causing hold violation  
slow cell-> not meet performance  
So constraints is needed as a guidance for the 

</details>
<details><summary> Lab Session -> Lab3: yosys good mux </summary>
 
#
### *__Lab Session__*
#### *Lab3: good mux Part 1,2,3*  

Steps:  
Command to invoke yoysy > yosys  
(i) Read library-> read_liberty -lib ../my_lib/lib/sky*.lib  
(ii) Read design-> read_verilog good_mux.v  
(iii) Synthesis-> synth -top good_mux  
(iv) thn can generate netlist -> abc -liberty ../lib/sky*.lib (std cell will get pick from library)    
<img width="600" alt="lab1g" src="https://user-images.githubusercontent.com/118953915/205316337-5ccd9b3d-7cef-4cf6-81a4-b8e5953c8b86.png">  
(v) See logic realiazed in graphicel -> show        
There is 3 input, 1 output, no internal wire, 1 mux 2to1    
<img width="600" alt="lab1h" src="https://user-images.githubusercontent.com/118953915/205317486-e3c559a1-19c9-484a-84b4-29cb7ceeeaf6.png">  
-nand2_1: nand gate with 2 input, o2ai: OR+AND+INV  
(vi) Write netlist-> write_verilog  good_mux_netlist.v / write_verilog -noattr good_mux_netlist.v <- simplified netlist    
<img width="600" alt="lab1j" src="https://user-images.githubusercontent.com/118953915/205425197-8e128ef0-7944-4afc-b11d-f8531c5ccdd2.png">  

Here is my nelist and logic diagram:  
<img width="600" alt="lab1k" src="https://user-images.githubusercontent.com/118953915/205425631-f8eab904-fe59-4ae1-9bc7-97f259758fc6.png">
</details>

#
# Day_2   
**⭐Timing libs(QTMs/ETMs), hierarchical vs flat synthesis and efficient flop coding styles**

<details><summary> ⚡Lecture Session: Introduction to course live session </summary>

### *__Lecture Session__*

1. CMOS (complementary metal-oxide semiconductor) is the semiconductor technology used in most of today's integrated circuits (ICs), also known as chips or microchips 
There are two types of MOSFETs: the NMOS and the PMOS  
MOSFETs-specifying the circuits physically and characterizing them electricity    
2. FF (flip flop) serves as memory element in a digital design  
3. Setup time is the time for the input data signals to remain stable before the clock edge, while hold time is the time for the input data signals to remain stable  after the clock edge  
 
</details>
<details><summary> Lab Session -> Lab4: Introduction to dot Lib  </summary>
 
### *__Lab Session__*  
 
#### **Lab4: Introduction to dot Lib**    

1. Here is the contents of .libs in this training   
<img width="600" alt="Capture" src="https://user-images.githubusercontent.com/118953915/206341918-17e165df-0d95-4605-8fec-b283f48c8481.PNG">  
<img width="600" alt="lab2a" src="https://user-images.githubusercontent.com/118953915/205808293-af4da4c9-ed20-4912-9573-98451b599ad3.PNG">  

 Enter ":syn of" to switch off highlighted word in vim

(i)Name of library: sky130_fd_sc_hd_tt_025c_1v80      
(ii)PVT (Process,Voltage,Temperature)  
-Process variation due to fabrication (variations in the manufacturing conditions such as temperature, pressure, and dopant concentrations)    
-Voltage will cause variation in behaviour of the circuit    
-Semiconductor sensitive to temperature    
In the library of sky130_fd_sc_hd_tt_025c_1v80:    
tt-typical process (can be slow/fast/typical) ; 025c-temperature ; 1v80 -volatge    

In order to make sure our silicon can be function in all possible conditions  
we need to factor in all variation when we design circuit, so our library will be charaterize to model this variations  

2. .lib is buckect of all std cell that avaiable  
Containing different flavours of different cell & different flavours of same cell with different number of inputs   
<img width="600" alt="lab2b" src="https://user-images.githubusercontent.com/118953915/205820406-e6b086cf-35ce-406f-bc61-35f58de851bb.PNG">  

 and each of them have different features, can open equivalent verilog model to see the details of gates by using command ":vsp ../my_lib/verilog_model/sky130_fd_sc_hd.v" 
File with <file>.pp.v is consisting power port information 
<img width="600" alt="lab2c" src="https://user-images.githubusercontent.com/118953915/205829566-3b17871b-3a2c-4fa4-a6ad-0141246b6c7c.PNG">  

we can see that there is
The cell is having 5 inputs, so there will be 2^5=32 combinations. In the libs will state out all details for each combinations (Eg: Leakage power)   
3. Inside the lib will also state out cell area, power port  
<img width="300" alt="lab2d" src="https://user-images.githubusercontent.com/118953915/205839427-24e92d8b-0eb7-4ef8-9550-a420ad39d329.PNG">  

 Each of the cell pin have its own information: capacitance, transition, power associated to the pin  
<img width="300" alt="lab2e" src="https://user-images.githubusercontent.com/118953915/205839432-e3914736-c691-48d9-af9c-80976b2b849e.PNG">  

 Besides power, the lib also will contains timing information  
<img width="600" alt="lab2f" src="https://user-images.githubusercontent.com/118953915/205839439-f176fd34-4d19-479c-a2f3-c6ed72a9f1b0.PNG">  

 3. Here is the comparison on different flavours of same cell with different number of inputs  
 <img width="900" alt="lab2g" src="https://user-images.githubusercontent.com/118953915/205848330-ab153dd2-9ab3-4542-b802-6c6de19f6e45.PNG">  

 -Smaller cell: More delay, Less area, Less power  
-Bigger cell: Less delay, More area, More power  
 
💡Conclusion: 
 
-Pros of Bigger cell: wider transisteor == faster/small delay      
-Pros of Smaller cell: small area == small power comsume
 
</details>
<details><summary> Lab Session -> Lab5: Hierarchical vs Flat Synthesis  </summary>
 
#### **Lab5: Hierarchical vs Flat Synthesis**    
 
 1. Command to setup the design:
(i) yosys  
(ii) read_liberty -lib ../lib/sky*.lib  
(iii) read_verilog multiple_modules.v  
(iv) synth -top multiple_modules  
 <img width="500" alt="Capture" src="https://user-images.githubusercontent.com/118953915/206349270-59c806c7-a885-4519-8847-88b0f0a19142.PNG">  
 <img width="300" alt="lab2h" src="https://user-images.githubusercontent.com/118953915/206076867-a565dc90-74d4-432c-ad12-c028c85c5a47.PNG">  

(v) linking deisgn to library  
 abc -liberty ../lib/sky*.lib    
(vi) show multiple_modules <- key in the top modules name      
Then will display out the hierarchy design -> not showing AND and OR gate, but only showing the u1 and u2, which is the instance of submodule 1 and 2   
 <img width="600" alt="lab2i" src="https://user-images.githubusercontent.com/118953915/205855372-92273978-5913-4f81-a92e-575f0ea3f9ff.PNG">  

(vii) write_verilog -noattr multiple_modules_hier.v then !vim multiple_modules_hier.v  
  > Refer this link for learning DeMorgan's Theorems in boolean algebra:  https://www.allaboutcircuits.com/textbook/digital/chpt-7/demorgans-theorems/    
 
 My run:   
 <img width="600" alt="Capture" src="https://user-images.githubusercontent.com/118953915/206344644-6f9a7367-797e-471c-8f79-4659eb3feb87.PNG">  
 <img width="200" alt="lab2q" src="https://user-images.githubusercontent.com/118953915/206092566-801b13b7-9422-4b92-bada-dc6b26cc4156.PNG">  
 Run from trainning video:   
 <img width="455" alt="lab2j" src="https://user-images.githubusercontent.com/118953915/205927497-d3452277-6b91-4324-8e94-91050a9627cd.PNG">  
(v) Reason on why the netlist construct 2INV+NAND instead of directly OR gate:
Here is the screenshot from lecture video:  
From the figure: [Left] If cmos NAND, have stacked nmos, [Right] NOR follow by iNV to get OR, have staked pmos
<img width="330" alt="lab2k" src="https://user-images.githubusercontent.com/118953915/205933439-d48489b7-8c53-4a1b-8b57-38f57bc2a987.PNG">  
-Stacked pmos is bad, due to poor mobility. In order to improvce this need to make it wide cell (to get good logic effort)

-Logical effort is defined as the ratio of the input capacitance of a gate to the input capacitance of an inverter delivering the same output current. It is defined as the number of times worse it is at delivering output current than would be an inverter with identical input capacitance  
 
(vi) write out flat netlist by using command flatten  
(vii)write_verilog -noattr multiple_modules_flat.v then ! vim multiple_modules_flat.v  
 Here is the comparison among multiple_modules_hier.v vs multiple_modules_flat.v
 <img width="900" alt="lab2l" src="https://user-images.githubusercontent.com/118953915/205939781-4c3ae3d4-cd4c-4123-8d61-db09f5b1b216.PNG">  
From the figure: [Right] it is a single netlist without any submodule inside the flatten.v and can directly see each of the instantiation of the gate  
(viii) Invoke show, not seing u1 and u2 anymore after flattem
 <img width="929" alt="lab2m" src="https://user-images.githubusercontent.com/118953915/205941268-ef256f34-9b8d-4da1-a5b0-39b587688f58.PNG">  
 2. Now looking at sub-modules
 (i) Need to exit and repeat the step from (i) to (iii)   
 (ii) Then, use this command and only synthesis one of the sub_module: synth -top sub_module1 
 <img width="600" alt="Capture" src="https://user-images.githubusercontent.com/118953915/206367130-927887da-4e04-4406-82e9-f350fcc37ba7.PNG">  
 Only consists one sub_module1 which is AND gate:    
 <img width="600" alt="lab2zsub" src="https://user-images.githubusercontent.com/118953915/206192139-d2e9e102-8d68-450a-bde7-bd6e785d4e25.PNG">  

   
💡 Modular synthesis is prefer when we have multiple instances of same module (Eg: when there is 6 x multiplier, only required to synthesize one and duplicate 6 times) or divide and conquer (Eg: when there is huge and massive design, then the tool will not run smartly. Recommend to run by portion so the netlist will get optimize, after that stick all those netlist together at the top level)  
 
 **Various Flop Coding Styles and optimization**  
 
1. In a combinational circuit, there is multiple logic gate. Each of the logic gate will have some propagation delay, which will lead to glitch occur. (Eg: 1st gate having propagtion delay 1ns and the next gate have 2ns, so at the end the output dint have the right value which means that output will glitch due to propagation delay)  
💡 so we need Flop to store the value (place between the gates)  
-Output of the D-FF only will trigger during the positive edge of clocks, so the data at output is stable.  
-The next logic gate will also receive a stable data, because the output(Q) of previous Flop have shielded the changes from its own input(D)
 2. We need to initialize the flops - sel/reset/syn/async   
 <img width="541" alt="Capture" src="https://user-images.githubusercontent.com/118953915/206346230-17b19539-3857-46c4-b9ce-0c032f7b75cc.PNG">  
 <img width="960" alt="lab2p" src="https://user-images.githubusercontent.com/118953915/206098264-9a0301ac-743d-4c7d-ba98-6bcd7fb93914.PNG">
 
 
 All of the output will get trigger as long as there is posedge clock -> "always@(posedge clk)"  
 (i) D FF with async reset: Output(q) will get trigger when there is positive clocck edge and positive async_reset  
-Asynchronous happen anytime irrespective to clock edge (without dependency to clock)    
-When there is positive async_reset, the output will have value "0", else will read in value from input(d)  
(ii) D FF with sync reset: Output(q) will get trigger if condition:   
 -when the sync_reset is toggle to 1, it will wait for posdge of clock, then only will trigger the output    
📖 asyn FF: always (posedge clk,posedge async reset) ; syn FF: always(posedge clk)  
  
**Lab flop syntheses simulation**
1. Here is all the FF, will check the behavioural simulation:  
(i) iverilog dff_*.v tb_dff_*.v  ; ./a.out ; gtkwave <>.vcd    
<img width="1000" alt="lab2r" src="https://user-images.githubusercontent.com/118953915/206105360-d43817af-6876-426b-9ba4-9542abc7ecc0.PNG">  

 (ii) Asyn reset  
<img width="600" alt="lab2s" src="https://user-images.githubusercontent.com/118953915/206105370-b1ee39b8-fe08-4b3e-8e1c-72b83cf1113a.PNG">  
 
 - The output(q) will get trigger for each of the posedge clock    
 - If the async_reset is "1", the output(q) will directly change to "0" irrespective to clock edge  
 - The output(q) will remain "0" until the async_reset is toggle back to "0", then it will read in value from input(d) during posedge clock  

 (iii) Asyn set  
<img width="600" alt="lab2t" src="https://user-images.githubusercontent.com/118953915/206105378-02c19451-6487-495f-8e31-0a11ac56c102.PNG"> 
 - The output(q) will get trigger for each of the posedge clock    
 - If the async_set is "1", the output(q) will directly change to "1" irrespective to clock edge  
 - The output(q) will remain "1" until the async_set is toggle back to "0", then it will read in value from input(d) during posedge clock  

 (iv) Sync reset  
<img width="600" alt="lab2u" src="https://user-images.githubusercontent.com/118953915/206105390-9a0f5015-29fb-45f7-a597-e395247f2500.PNG">  
 - The output(q) will get trigger for each of the posedge clock    
 - If the sync_reset is "1", the output(q) will change to "0" in the next posedge clk  
 - The output(q) will remain "0" until the sync_reset is toggle back to "0", then it will read in value from input(d) during posedge clock  
 
 💡set&reset have higher priority thn input(d) due to if(condition)...else  
 
2. Proceed to synthesis  
(i) Steps: yosys ; read_liberty -lib ../lib/sky*.lib ; read_verilog dff*.v ; synth -top dff_* ; using dff, dfflibmap -liberty ../lib/sky*.lib ; abc -liberty ../lib/sky*.lib  
 <img width="600" alt="Capture" src="https://user-images.githubusercontent.com/118953915/206341471-8c2badc7-f839-4107-abb9-73bf081cdd29.PNG">  
 
-If use dfflimap, then the tool will only search for ff lib (and sometimes all the ff lib will keep in another folder in */lib, so need to point correctly)
only look for dff flops (ss)  
<img width="600" alt="lab2v" src="https://user-images.githubusercontent.com/118953915/206117867-e22b7618-1707-4379-9ebb-68a36c561b47.PNG">  
(ii) async res: stated "RESET", flop is active high reset so need inv (behaviour of AND gate in order to get "1")  
 <img width="600" alt="lab2w" src="https://user-images.githubusercontent.com/118953915/206117885-ebbd4855-52fa-4c31-be0d-696f94c065e1.PNG">    
async set: stated "SET", flop is active high reset so need inv (behaviour of AND gate in order to get "1") 
<img width="600" alt="lab2x" src="https://user-images.githubusercontent.com/118953915/206117889-ee19efe6-7926-4949-ad39-747769d7ea9b.PNG"> 
syncres: no set/reset pin on ff  
 Explanation from training video:
 <img width="800" alt="lab2y" src="https://user-images.githubusercontent.com/118953915/206125946-43360ff0-9462-42b2-9df3-35a7db90d595.PNG">  
 My run:  
<img width="600" alt="lab2z" src="https://user-images.githubusercontent.com/118953915/206125962-e5eb007c-fe5b-4996-8491-7d67c11d25f7.PNG"> 
 
**Interesting optimisations**

Here is some special case:  
1. If looking at multiplexer:  
 <img width="600" alt="lab2za1" src="https://user-images.githubusercontent.com/118953915/206133157-cbc9abe7-19c8-400f-86f6-83da18aade6c.PNG">  
 
 (i) Explanation from training video:   
 <img width="600" alt="lab2za" src="https://user-images.githubusercontent.com/118953915/206132337-4969c59c-0cbb-48f9-99a7-da98f1b6a6c3.PNG">  

 -When the number from the truth table convert to decimal value and times 2 and convert back to digital value, the pattern of output is the same for y[3:1] and then y[0]=0  
 (ii) Steps: yosys ; read_liberty -lib ../lib/sky*.lib ; read_verilog mult_2.v ; synth_top mul2 ; show  
 <img width="600" alt="lab2zb" src="https://user-images.githubusercontent.com/118953915/206185966-0bbfee96-fec1-49dc-a7d6-e43af9563009.PNG">  
 
 From the figure, we can see that there is no memories,no processor and no cell have been infferred. It is expected as show in (i), value y is from a and append with 1'b0.    
 
 Since there is no standard cell, 
 <img width="600" alt="lab2zc" src="https://user-images.githubusercontent.com/118953915/206187270-4f08db9e-bc3c-495c-ac67-d3746a534594.PNG">

2. Another multiplexer:  
 Explanation from training video:   
<img width="600" alt="lab2zd" src="https://user-images.githubusercontent.com/118953915/206198618-443bdc46-4601-4381-b3bf-5bc43ebf14f4.PNG">  
 
 (i) Steps: yosys ; read_liberty -lib ../lib/sky*.lib ; read_verilog mult_8.v ; synth_top mul8 ; show  
 Similar operation for mult_8 too  
 <img width="600" alt="lab2ze" src="https://user-images.githubusercontent.com/118953915/206199435-600e2f24-6ce4-4d7b-8380-211d5c1e2b7b.PNG">  

💡 No hardware required for the special case show above, only rewiring the signal will do. Not required any std cell to obtain the logic functionality 
</details> 
 
#
# Day_3 
**⭐Combinational and sequenial optimizations**

<details><summary> ⚡Lecture Session: Introduction to course live session </summary>

### *__Lecture Session__*

Synthesis is not a push-button solution, it is dependent on out design statement and clarity of implementation whether we want to optimize some particular places or not by setting ‘don’t touch’  
1. Optimization-minimizing cost functions: max delay cost(important!, weight in each path group-same clock constraint), min delay cost (expected-actual delay,unaffected by path group), max power cost, max area cost  
2. Constant propagation    
-Due to some requirement, there is 2 AND gate with one constant input “0”, so the output of the AND gate will directly obtain “0”, and depends on the another AND gate. While the another one have one constant input “1”, so the output only depends on one of the input, can directly understand as input A being wired as the output  
From training video:                          
![Picture1](https://user-images.githubusercontent.com/118953915/206745943-f7d65dae-7276-45a5-bc93-f7243e69371d.png)  
3. Combinational and sequential optimization  
-synthesis optimization for speed can be achieved through isolating the “and” portion of the circuit by assigning internal wire  
From training video:  
![Picture2](https://user-images.githubusercontent.com/118953915/206745950-9f696d1d-2ccd-4881-b51a-62a53861c83b.png)  
4. Another method: register retiming   
![Picture3](https://user-images.githubusercontent.com/118953915/206745951-1fc0c848-a096-4951-8491-90889fdcae33.png)  
5. Difference Among Constant propagation in :  
combinational logic is on Boolean Algebra  
sequential logic is on Boolean Algebra+Timing Diagram Analysis  (eg:timing in dff) 
> Boolean algebra table: https://www.electronics-tutorials.ws/boolean/boolean-algebra-simplification.html  
6. Additional optimization  
Resource sharing  
![Picture4](https://user-images.githubusercontent.com/118953915/206745954-fcf504ef-8667-40dd-8387-50d1ef777b46.png)  
-cons: increase in fanout  
 > Can refer this link: https://slideplayer.com/slide/3480933/ 
 
 -removal of un-connected logic across boundaries , removal of double inverting logic across boundaries, propagation of constants to reduce logic  

 </details> 
 
<details><summary> ⚡Lecture Session: Combinational and sequential optmizations </summary>

### *__Lecture Session__*
 
**(A) Introduction to optimization**

1. Combinational Logic Optimization – squeezing logic to get most optimised design -area & power saving  
Tech: constant propagation,boolean logic optimisation  
![Picture5](https://user-images.githubusercontent.com/118953915/206745955-a84d87f6-6b77-4353-a12f-e12a19f9b5c6.png)  
-Reduce to 2mos transistor-> less area and less power  
Example of sequential optimisation (boolean logic):  
 ![Picture6](https://user-images.githubusercontent.com/118953915/206745962-9a6bbcb7-37c1-4893-b9cf-cfbb370de588.png)  

2. Sequential Logic Optimization  
Tech: Sequential constan propagation, (advance: state optimisation,retiming,sequetial logic clonning)  
No hardware circuti required for below, since after optimization, it is getting y=1   
![Picture7](https://user-images.githubusercontent.com/118953915/206745967-d120b09d-83d1-42f7-bf60-882fba36aea0.png)  
However for this situation SET, the logic cannot being optimize due to Q=SET is not funtionally correct
-This is asynchronous dff, when the SET is ‘0’, the Q will wait for posedge clock to read in D   
![Picture8](https://user-images.githubusercontent.com/118953915/206745971-113bf5a6-34bf-41eb-83bf-ed9b8acb5ad7.png)  
State optimisation- optimize of unuse state (condense state machine)  
Cloning-physical aware synthesis (reduce large routing delay as shown in the figure below)  
Retiming both of the flop by reduce the logic at  1st combi and add those into 2nd combi, which can help in increase the frequency  operation of the circuit by reduce some delay in 1st combi  
![Picture9](https://user-images.githubusercontent.com/118953915/206745974-5ee450f6-9ad2-40c5-9c71-f5b75c655484.png)  

</details>
<details><summary> Lab Session -> Lab6: Combinational Logic Optimisations </summary>

### *__Lab Session__* 
#### **Lab6: Combinational Logic Optimisations**  
Here is the contents of each opt_check:  
![Picture10](https://user-images.githubusercontent.com/118953915/206745982-59de4300-0cc6-4b0b-9aad-0b62add5ca10.png)  
For opt_check:  
Steps: yosys ; read_liberty -lib ../lib/sky*.lib ; read_verilog opt-check.v ; synth -top opt_check ; opt_clean -purge ; abc -liberty ../lib/sky*.lib  
![Picture11](https://user-images.githubusercontent.com/118953915/206745985-e3103002-9d2e-470b-b72c-e3a6294e7efc.png)  
While for the opt_check2:    
![Picture12](https://user-images.githubusercontent.com/118953915/206745987-eec5bf43-36f2-4c8e-9266-6504363c21ce.png) 
While for the opt_check3:   
![Picture13](https://user-images.githubusercontent.com/118953915/206745990-1ff6c1a3-3ca9-41f6-b67f-612e74b8bc96.png)  
While for opt_check_4:      
![Picture14](https://user-images.githubusercontent.com/118953915/206745994-ce09709f-ba4f-4189-be89-733f0c9dec3c.png)  
For multiple_module_opt.v:  
Before opt_clean -purge need flatten  
Steps: yosys ; read_liberty -lib ../lib/sky*.lib ; read_verilog multiple_module_opt.v ; synth -top multiple_module_opt ; flatten ; opt_clean -purge ; abc -liberty ../lib/sky*.lib  
![Picture15](https://user-images.githubusercontent.com/118953915/206745996-d373cc0b-782a-4f22-846f-e405e3ca537d.png)  
Addional info:
![Picture16](https://user-images.githubusercontent.com/118953915/206745999-34084cd2-0a79-4590-907a-a507089831ad.png)  
Previous(before optimize):  
<img width="570" alt="Capture" src="https://user-images.githubusercontent.com/118953915/206753157-86ceb110-234d-4be5-87dc-05084d22bde4.PNG">  
While for multiple_module_opt2:    
Steps: yosys ; read_liberty -lib ../lib/sky*.lib ; read_verilog multiple_module_opt2.v ; synth -top multiple_module_opt2 ; flatten ; opt_clean -purge ; abc -liberty ../lib/sky*.lib  
Here is the verilog:     
![Picture18](https://user-images.githubusercontent.com/118953915/206746011-e8c442cc-13a9-46c0-8e3a-05a11bf37e72.png)  
After optimize:     
-Direct assigned '0' to y
![Picture19](https://user-images.githubusercontent.com/118953915/206746015-b9403176-1496-4ed8-930d-007567abc1c1.png)  
Previous (before optimize):   
![Picture20](https://user-images.githubusercontent.com/118953915/206746019-05c06841-3f11-4a9f-9e2d-2f401380271a.png)   
</details>
<details><summary> Lab Session -> Lab7: Sequential Logic Optimisations </summary>
 
#### **Lab7: Sequential Logic Optimisations**

Explanation from training video:   
-The output(Q) of dff_const2 will always HIGH, so the optimisation can be done on this dff  
![Picture21](https://user-images.githubusercontent.com/118953915/206746020-43e47618-a922-4115-b63a-bcebf485a17d.png)  
Here is the waveform for dff_const1.v: 
 -Wait for next clock edge  
![Picture22](https://user-images.githubusercontent.com/118953915/206746024-a3782b6f-3fd0-4ec8-806e-c142dc6757af.png)  
Here is the waveform for dff_const2.v:    
-Output always HIGH   
![Picture23](https://user-images.githubusercontent.com/118953915/206746025-0199c2d2-50ea-4ee5-9a22-034570a1cebc.png)   
For const1.v & Const2.v:  
![Picture24](https://user-images.githubusercontent.com/118953915/206746026-677d49e5-4b6e-4a29-8896-2b44eea71c0d.png) 
Now, looking at dff_const3.v  
Here is the explanation from training video:  
![Picture25](https://user-images.githubusercontent.com/118953915/206746028-0601838d-336e-41ef-8fa4-4ebdc80074e2.png)     
Here is the waveform:
![Picture26](https://user-images.githubusercontent.com/118953915/206746031-a9663eeb-6635-4d40-8f0f-f2c539b08811.png)  
For dff_const3.v  
Here is the details:   
![Picture27](https://user-images.githubusercontent.com/118953915/206746035-500bfc65-73ea-4974-9325-d912002c73aa.png)  
For dff_const4.v:   
![Picture28](https://user-images.githubusercontent.com/118953915/206746037-fef3eb9e-8317-4aad-ac36-cead4d573ef4.png)  
Here is the waveform:   
![Picture29](https://user-images.githubusercontent.com/118953915/206746039-d0505376-74e3-4a75-91a7-4d6a2aafcc8f.png)  
For dff_const4.v:      
![Picture30](https://user-images.githubusercontent.com/118953915/206746042-adea7672-ea04-45a7-97af-ed6759f16253.png)  
For dff_const5  
Here is the details:  
![Picture31](https://user-images.githubusercontent.com/118953915/206746046-b10f71c6-8a7d-4fef-95af-760457547ca7.png)  
Here is the waveform:   
![Picture32](https://user-images.githubusercontent.com/118953915/206746048-cf3cc483-65ba-4efa-9bba-c77935007821.png)
For dff_const5.v:  
 ![Picture33](https://user-images.githubusercontent.com/118953915/206746057-02bcf9cf-acab-4db9-a9f3-bdd6439c71b1.png) 

**Unused Output Optimization**
 
Here is the explanation from training video:  
![Picture34](https://user-images.githubusercontent.com/118953915/206746059-4f022587-fb41-4eaf-9a7a-0920248bac28.png)  
Here is the counter_opt:  
![Picture35](https://user-images.githubusercontent.com/118953915/206746061-58a2b0a6-8fe4-47ab-9069-70b28cb3885c.png)
Remodified the file to look for 3 dff:  
![Picture36](https://user-images.githubusercontent.com/118953915/206746066-8c2d932b-36f2-45c7-b6d6-c086b166d449.png)
![Picture37](https://user-images.githubusercontent.com/118953915/206746071-ab02105c-d9cb-4d5a-92a0-b2bf4fccb585.png)  
💡In previous counter_opt, all those logic not having a direct role in determining the primary output of the module will optimize directly
</details>
 
#
# Day_4 
**⭐GLS, blocking vs non-blocking and Synthesis-Simulation mismatch**  
<details><summary> ⚡Lecture Session: GLS, blocking vs non-blocking and Synthesis-Simulation mismatch </summary> 
 
### *__Lecture Session__*

**(A) Introduction Gate Level Simulation (GLS & Synthesis-Simulation Mismatches)** 
 
1. GLS  
-Running the test bench with netlist as Design Under Test: validate functionality of rtl code by giving stimulus to the rtl design and check the output whether met with our specification/expectation 
-Netlist is logically same as RTL code and same test bench will allign with the deisgn  
-Purpose:  
(i)Verify the logical correctness of design after synthesis- might happen design not same with synthesis  
(ii)Ensuring the timing of the design is met -steup.hold (prevoius training:different flavour of cell-slow/fast)  
<img width="900" alt="4d1" src="https://user-images.githubusercontent.com/118953915/206904531-0dcc38e7-9cc8-4209-87c5-ae34be6a94d1.PNG">   
 
From the training video:    
<img width="900" alt="4d2" src="https://user-images.githubusercontent.com/118953915/206904466-8063e648-a45f-4871-b784-f15d74ef3fd9.PNG">  
Gate level verilog model can be timing aware or just functional, if just funtion thn can validate funtionality and if timing aware thn can validate funtionality and ensure timing   
 
Here is the notes from lecture session:    
<img width="900" alt="47" src="https://user-images.githubusercontent.com/118953915/207021148-a0581cb9-aeb1-4f12-9635-41422678572d.PNG">     

2. Synthesis simulation mismatch  
(i) Missing sensitivity list  
-simulator works based on "activity" : output will change when there is changes in inputs, else will not change  
-If always@(sel), only based on one input signal: sel  
-treat as latch  
-so should always(*), so when there is any signal changes, the output will change    
From training video:  
 <img width="900" alt="4d3" src="https://user-images.githubusercontent.com/118953915/206904463-73a208cb-ec90-44e0-ab02-c6ba12f92e18.PNG">    
 
(ii) Blocking vs non-blocking statements in verilog  
-inside always block  
<img width="900" alt="4d5" src="https://user-images.githubusercontent.com/118953915/206908341-3b26bef2-9c69-4595-8b19-747d38f81635.PNG">  
<img width="900" alt="4d4" src="https://user-images.githubusercontent.com/118953915/206908256-9760735a-996c-4831-a52c-333e0e4be284.PNG">  
Another example:  
<img width="900" alt="4d6" src="https://user-images.githubusercontent.com/118953915/206909203-28836049-b5c2-4bb6-a077-2cbae8532d2a.PNG">  
Here is the additional notes from lecture session:  
<img width="900" alt="46" src="https://user-images.githubusercontent.com/118953915/207019050-8dca9480-2b22-4fbf-ab73-eddad60bcb60.PNG">   
(iii) non standard verilog coding   
</details>
<details><summary> Lab Session -> Lab8: GLS Synth Sim Mismatch </summary> 

### *__Lab Session__*
#### **Lab8: GLS Synth Sim Mismatch**  
For ternary_operator_mux:
Here is the details and waveform:  
<img width="900" alt="40" src="https://user-images.githubusercontent.com/118953915/206954215-44b22399-165d-4bbe-b225-c0e0de0862c2.PNG">  
Here is the diagram:  
<img width="900" alt="41" src="https://user-images.githubusercontent.com/118953915/206954228-686c9c47-8214-40da-b6bd-e344aad06ba8.PNG">  
In order to run GLS, required 4 files: iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_mux.v tb_ternary_operator_mux.v  
-For GLS, in the left hand side window, under uut have further hier (4,base)    
<img width="900" alt="42" src="https://user-images.githubusercontent.com/118953915/206972631-a006a6e4-2752-4a9c-b0ab-4f6155e551f1.PNG">  
For bad_mux:   
<img width="900" alt="43" src="https://user-images.githubusercontent.com/118953915/206972621-69d1cf13-3bf8-4575-ac14-76996cabaf19.PNG">   
Another example, for blocking_caveat:   
 <img width="683" alt="44" src="https://user-images.githubusercontent.com/118953915/206986825-4e92e930-1717-416f-9c80-fb57b9fe6382.PNG">   
 💡 Avoid using blocking statement, because high posibility will lead to synthesis simulation mismatch  
</details>

#
# Day_5 
**⭐DFT**  
<details><summary> ⚡Lecture Session: DFT (Design for Testability) </summary> 
 
### *__Lecture Session__*

**(A) Introduction on DFT (Design for testability)** 
 
1.	$\textcolor{blue}{\text{Testability}}$-ability to run an experiment to test a hypothesis or theory  
In VLSI term: If a design is $\textcolor{coral}{\text{well-controllable}}$ and $\textcolor{coral}{\text{well-observable}}$, it is said to easily testable  
 
2.	$\textcolor{green}{\text{What}}$ is DFT?  
DFT is a technique which facilitates a design to become testable after production  
or adding an extra design for an existing design to make sure it can be tested after being fabricated  
Eg of designs included for making the whole chip testable:  
(i) For macro(ip), including MBist(memory built in seld test) logic  
(ii) For flops(sequential logic), using scan chains  
(iii) For combination circuit, generating test patterns (3 bits input will need generate 2^3=8 patterns)  
 
3.	$\textcolor{green}{\text{Why}}$ need DFT?  
-It makes the testing easy at the post-production process  
-Have 3 main levels of testing after a chip being fabricated:  
(i)	Chip-level: when chips are manufactured  
(ii)	Board-level: when chips are integrated on boards/packages (eg:raspberry pi)  
(iii)	System-level: when several boards are assembled together (laptops) 
DFT is also done due to economical and market needs (Eg: if test at chip-level can reduce lost compare to test at system-level)  
 
4.	When or where implement DFT (in basic ASIC design flow)  
$\textcolor{green}{\text{When}}$ implemet DFT? -> At the beginning of design flow  
$\textcolor{green}{\text{Where}}$ to implement DFT? -> During the synthesis   
-including a design per an existing design to make sure that it is testable after post and route
-make sure is synthesizable/manufacturable  
>Can refer here for details on ASIC design flow : https://www.allaboutvlsi.in/2020/12/asic-design-flow.html   

 ![sch](https://user-images.githubusercontent.com/118953915/207799275-3e5ea1c8-6e9a-4fe3-a4ce-2af9fd3399fc.png)  

5.	Here is the Pro’s and Con’s of DFT:  
 <img width="900" alt="d5" src="https://user-images.githubusercontent.com/118953915/207634053-7c272823-85a0-4541-94a3-53bb2010bdb4.PNG">  
 
 
6.	Here is the basic terminologies on DFT:  
 
 Terms | Defination|
---|---|
$\textcolor{blue}{\text{Controllability}}$| Ability to establish a specific signal value at each node in a circuit from setting values at the circuit’s inputs-Can adding multiplexer |
$\textcolor{blue}{\text{Observability}}$|Ability to determine the signal value at any node in a circuit by controlling the circuit’s inputs and observing its outputs -Can observe the node by adding flip flop |
Fault| There is a physical damage/defect compared to the good system, which may or may not cause system failure (eg: might cause by fabrication wire-connection problem) |
Error| An error is caused by a fault because of which system went to erroneous state (eg: there is x/z(high impedance)–might cause by connection cutoff) |
Failure| System is not providing the expected service (eg: design not meeting specification) |
💡 A fault causes an error when leads to the system failure 
Fault Coverage| Percentage of the total number of logical faults that can be tested using a given test set T -After post production, have a testing list (eg: make sure all wire connected, data transfer properly, no crosstalk) |
Defect level| Refers to the fraction of shipped parts that are defective. Or, the proportion of the faulty chip in which fault isn’t detected and has been classified as good (eg: out of 100 chips, 10 chips are faulty chips) |  

Adding multiplexer for controllability:  
<img width="600" alt="addmux" src="https://user-images.githubusercontent.com/118953915/207799184-1bdc171f-052e-48e1-b3bc-3903ada61005.PNG">   
Adding FF for observability:   
<img width="600" alt="addff" src="https://user-images.githubusercontent.com/118953915/207799176-04f0f79e-7d02-4cfc-949f-089233a49f41.PNG">  
 
7. DFT techniques  
There are mainly categorized 2 main ones:  
(i)	Ad-hoc technique/steps (following basic step by designing it self)   
 -All flip flops must be initializable (if ff get into unknown state x/z, then need reset to set to initial state)  
 -Partition a large circuit into small blocks  
 -Provide test control for the signals which are not controllable (controllability-give test case)  
 -While designing test logic we have consider the ATE requirement  
(ii) Structured technique (Ad-hoc have some limitation, so introduced this technique)  
 -Scan: in the design all the flip flops are converted into scan flip flops  
 -Boundary scan (partition-which small group causing issue)  
 -Built-in self-test   
   ->MBist (Memory built-in self-test) -all condition put in memory, thn check output expected or not, check in all corner –(Eg: macros-IP: pll)  
   ->LBist (Logic built-in self-test)- Eg: AND gate (input ‘0’ & ‘1’, output ‘0’)  
> Can refer here for details on race condition: Avoid combinational feedback (race condition)    
 https://learn.microsoft.com/en-us/troubleshoot/developer/visualstudio/visual-basic/language-compilers/race-conditions-deadlocks
 
![rc](https://user-images.githubusercontent.com/118953915/207799261-07ad1683-138c-4075-aba0-d0401637e238.png)  
 
8. Scan-chain technique  
(i) Specifying the scan constraint  
(ii) Specifying scan ports and scan enables  
(iii) compiling the dft  
(iv) Identifying the number of scan chains  
 
9. Scan based technique/Scan-chains  
-scan chains are the elements in scan-based designs that are used shift-in and shift-out test data  
-A scan chain is formed by a number of flops connected back-to-back in a chain with the output of one flop connected to another    
 ->The input of first flop is connected to the input pin of the chip (called $\textcolor{orange}{\text{scan-in}}$) from where scan data is fed. The output of the last   flop is connected to the output pin of the chip (called $\textcolor{orange}{\text{scan-out}}$) which is used to take the shifted data out. There is another one is scan selection (called $\textcolor{orange}{\text{scan-enable}}$)  
 ->use multiplexer to select test data(test data input-scan-in) or actual data(normal input)  
-There are 3 types of scan flip-flops configurations namely-multiplexed,clocked,lssd (level sensitive deisgn)   
<img width="300" alt="ff" src="https://user-images.githubusercontent.com/118953915/207799191-a2ffefcb-c038-4f2e-97a4-ac8ae5271cce.png">  
 
10. What is the purpose of this scan flops?  
-To test stuck-at faults in manufactured devices  
-To test the paths in the manufactured devices for delay (eg: to test whether each path is working at functional frequency or not, any failure)  
 
11. Functionality of scan chain   
💡 Goal : is to make each node in the circuit controllable and observable  
 
**$\textcolor{purple}{\text{Steps to do basic scan-in and scan-out:}}$**   
1. Assert scan_enable (make it high) so as to enable (SI -> Q) path for each flop   
2. Keep shifting in the scan data until the intended values at intended nodes are reached   
3. De-assert scan_enable (for one pulse of clock in case of stuck-at testing and two or more cycles in case of transition testing) to enable D->Q path so that the combinational cloud output can be captured at the next clock edge   
4. Again assert scan_enable and shift out the data through scan_out  
<img width="1000" alt="1" src="https://user-images.githubusercontent.com/118953915/207886159-46740738-ff6b-40cd-802a-5efc50adf53e.PNG">    
 
12. How long one single scan-chain is?   
By chain length, it means the number of flip-flops in a single scan chain  
-Larger the chain length, more the number of cycles required to shift the data in and out  
-However, considering the number of flops remains same, smaller chain length means more number of input/output ports is needed as scan_in and scan_out ports   
>Formula:   
>Number of ports required = 2 X Number of scan chain   

Eg: If there is 3 scan chains, then there will be 6 ports  
Also, Since for each scan chain, scan_in and scan_out port is needed   
💡 Number of cycles required to run a pattern = Length of largest scan chain in design   

>QnA: Suppose, there are 10k flops in the design and there are 6 ports available as input/output, wcich means that there is 3 scan chains (6/2=3)  
>The idea scan chain distribution is [3300,3400,3300], not ideal [9000,100,900], then the maximum number of cycles required will be 3400  
> If there is 9k FFs in one scan chain, then it will causing number of cycles required to shift the data in and out increase   
> 💡 The concept is related to scan chain balancing.  
>if there is 100’s of flip-flops, then the test pattern will up to 2^100= 1.2676506e+30, we can’t put that up manually. So we need using ATPG(Automatic Test Pattern Generator) or ATE(Automatic Test Equipment)  
> Can refer here for details on scan chain: https://vlsiuniverse.blogspot.com/2013/07/scan-chains-backbone-of-dft.html
 
13. ATE (Automatic Test Equipment) <- mentioned at Ad-hoc technique section, but more prefer to use structured technique  
-is any apparatus that performs tests on a device, known as the device under test (DUT), equipment under test (EUT) or unit under test (UUT)   
-using automation to quickly perform measurements and evaluate the test results   
-it can be a simple computer-controlled digital multimeter, or a complicated system containing dozens of complex test instruments (real or simulated electronic test equipment) capable of automatically testing and diagnosing faults in sophisticated electronic packaged parts or on wafer testing, including system on chips and integrated circuits  

14. Basic ATE functionality: -building a whole clk for automating whole design  
Total 5 phase:    
1.Scan-In Phase – each clock edge, data propagate into scan chain  
2.Parallel Measure – each clock cycle, data taken out at parallel output port to perform check  
3.Parallel Capture – capture data to perform check  
4.First Scan-Out Phase – if there is 100 ff, at 101 cycles will get 1st scan-in data out  
5.Scan-Out Phase- all data obtained at scan-out and there is comparator in ATE to compare the data among scan-in and scan-out   

15. Overview of DFT Compiler                                      
<img width="600" alt="3" src="https://user-images.githubusercontent.com/118953915/207886176-cd936ecb-a0ae-4e12-8a40-22f54a5414a2.PNG">      
 
Flow of Synopsys DFT Compiler:  
<img width="600" alt="4" src="https://user-images.githubusercontent.com/118953915/207886192-2a083f44-c521-4ecb-beaf-d4072c57180c.PNG">     
-Design Rule Checking (DRC): Verifies as to whether a specific design meets the constraints imposed by the process technology to be used for its manufacturing
 
>Some sample commands are:   
>set_scan_configuration   
>preview_scan 
>insert_scan  
>set_scan_path   
>set_scan_signal  
 
$\textcolor{green}{\text{Additonal Repo:}}$  
1. Other configurations of scan chains:  
-Test power is a serious problem in the scan-based testing. DFT-based techniques and X-filling are two effective ways to reduce both shift power and capture power   
-In order to reduce test power and keep the defect coverage, there is a paper on "Scan chain configuration based X-filling for low power and high quality testing"  
-In this paper mentioned that the scan chain configuration tries to cluster the scan flip-flops with common successors into one scan chain, in order to distribute the specified bits per pattern over a minimum number of chains.       
> Can refer part of the details on the paper: https://digital-library.theiet.org/content/journals/10.1049/iet-cdt.2008.0163

2. Sample circuit and explain with waveforms (take one faulty circuit and one non faulty)  

Design without faulty:  
<img width="900" alt="5" src="https://user-images.githubusercontent.com/118953915/207904857-d00ece9b-15e9-4fa7-8494-5f132d8bd398.PNG">  
 
Design with faulty:  
-Metastability is a phenomenon of unstable equilibrium in digital electronics in which the sequential element is not able to resolve the state of the input signal; hence, the output goes into unresolved state for an unbounded interval of time  
-If the setup check is violated, data will not be captured properly at the next clock edge. Similarly, if hold check is violated, data intended to get captured at the next edge will get captured at the same edge  
<img width="900" alt="fa" src="https://user-images.githubusercontent.com/118953915/207904879-26edb3f8-4586-41c9-89a5-daca3b704fb3.PNG">   
 
3. My view on how DFT can be game changer for VLSI engineers:  
- From quality aspect: In a design is having huge amount of logic gates, so if there is one faulty logic in one of a circuit, will lead to big issue especially if the logic have multiple connection on it. The higher the test coverage, the higher the quality of design   
- From timing aspect: The ealier the engineer found out where is the issue occur, the earlier the design can be fixed and launch to market    
- From cost aspect: If the test coverage is high and engineer can found out the issue before the chip is fabricated, then this can reduce the lost   
 
4. ATE(Automatic Test equipment)  
(i) When the chip is digital, the stimuli are called test patterns or test vectors  
 <img width="600" alt="2" src="https://user-images.githubusercontent.com/118953915/207886168-b3c3750b-fbf3-464a-9383-70ecbe5a3c88.PNG">   

 -An ATE is used to apply a sequence of stimuli to the die under probe DUP or device under test DUT, monitor and/or record the results of the response from
the device, and make decision on pass/fail status according specifications of the die/device  
 
(ii) Types of ATE automatic test systems:  
 
System | Details|
---|---| 
 PCB inspection systems| Key element in any production process and particularly important where pick and place machines are involved|
 ICT In circuit test| Besides checking short circuits, open circuits, component values, but it also checks the operation of ICs|
 JTAG Boundary scan testing| Joint Test Action Group. to overcome the problems of lack of access to boards and integrated circuits for testing. Boundary scan overcomes this by having specific boundary scan registers in large integrated circuits|
 Functional testing|  Any form of electronics testing that exercises the function of a circuit|
 Combinational test| Combinational testers are generally used for printed circuit board testing|
 
 
(iii) Components of an ATE system
 Components | Details|
---|---|
Hardware | Power supplies, interface modules, embedded controllers, analog inputs and outputs, digital input/output, AC/DC outlets,... |
Software| For test development and management of data collection, storage, reporting, and analysis |
Test instruments | Such as a digital storage oscilloscope (DSO), digital multimeter, or inductance, capacitance, and resistance (LCR) meter |
Signal sources | Such as an arbitrary waveform generator (AWG), function generator, pulse generator, or radio frequency (RF) generator |
Test probes or handlers | Which establish a connection between a test instrument and a DUT, UUT, or EUT |  


(iv) Flow of ATE- As mentioned above previous session [No.14]:  
<img width="900" alt="ss" src="https://user-images.githubusercontent.com/118953915/207914210-5092d2a8-e74e-46df-9408-723ccb5e9ee1.PNG">  

-The scan cells are linked together into “scan chains” that operate like big shift registers when the circuit is put into test mode   
-The scan chains are used by external automatic test equipment (ATE) to deliver test pattern data from its memory into the device   
Here is the flow:  
1.After the test pattern is loaded, the design is placed back into functional mode and the test response is captured in one or more clock cycles   
2.The design is again put in test mode and the captured test response is shifted out, while the next test pattern is simultaneously shifted into the scan cells   
3.The ATE then compares the captured test response with the expected response data stored in its memory   
4.Any mismatches are likely defects and are logged for further evaluation  

>Can refer details on ATE:Advantest Model T6682: http://ece-research.unm.edu/jimp/vlsi_test/slides/html/overview1.htm  
>Can refer details on ATPG flow: http://razzkamal.blogspot.com/2016/05/what-is-dft-closure-why-is-it-important.html

</details>
 
#
# Day_6   
**⭐Introduction to Logic Synthesis**  

<details><summary> ⚡ Lecture Session: Introduction to Logic Synthesis </summary>  

### *__Lecture Session__*  

**(A) Advanced Synthesis and STA with Design Compiler**    

1.Basic of Digital Logic Design and Synthesis  
-Digital Logic: Switching Function, Automation and Decision making  
![1](https://user-images.githubusercontent.com/118953915/208279707-0254aec1-5dc9-4fdf-958a-3e0465a51250.png)  
 
2.Why different flavours of gate  
-combinational delay in logic path determines the maximum speed of operation of digital logic circuit  
![2](https://user-images.githubusercontent.com/118953915/208279712-f323389c-886d-4e4c-9af7-10fc95e295e1.png)
 
3.Faster cells vs slower cells  
-load in digital logic circuit-> capacitance  
-faster the charging/discharging of capacitance-> lesser the cell delay  
 -> To charge/discharge the capacitance fast, we need transistors capable of sourcing more current  
 -->Wider transistor-> low delay-> but more area and power!  
 -->Narrow transistor-> more delay -> less area and power  
>MOSFET current equation, I proportional to W/L  

 4.Selection of cells  
-Need to guide the synthsizer(tool convert hdl->netlist) to select the flavour of cells that is optimum for the implementation of logic circuit  
  ->guidance offered to synthesizer: Constraints  

5.The circuit is created from RTL using the gates available in the .lib and given out as netlist  
![Picture4](https://user-images.githubusercontent.com/118953915/208279715-345f19a3-95fc-4559-a46c-41bf853cb9b2.png)
 
Can have multiple implementation  
![Picture5](https://user-images.githubusercontent.com/118953915/208279716-22bc6fc2-d156-4a07-89b3-936d4019c96e.png)
 
->Logic synthesis must achieve logically correct, electrically correct and timing of design met  

**(B) Introduction to Design compiler (DC)**  
 
1.DC-Synthesis tool targeted for ASIC design flow from Synopsys  
Features of dc:   
(i)Established a premium synthesis tool across semiconductor industry  
(ii)Interoperability with various backend tools from Synopsys  
(iii)Has ability to perform DFT scan stich  
(iv)Can handle huge designs with extreme complexity and provide very good QoR(Quality of result)  

2.Common terminologies associated with DC   
(i)Synopsys Design Constraints (SDC): There a re the design constraints which are supplied to DV to enable appropriate optimization suitable for achieving the best implementation  
 ->SDC is industry standard which used across Electronic Design Automation(EDA) implementation tools -Cadence,Synopsys,…  
 ->Electronic Design Automation (EDA) refers to a category of software tools used in a workflow to design electronic systems such as semiconductors, integrated   circuits, and printed circuit boards  
(ii).LIB: Design library which contains the std cells  
(iii)DB: Same as .lib but in a different format. DC understand libraries in .db format  
 ->So lib-convert to db thn source in DC  
(iv)DDC: Synopsys proprietary format for storing the design information. DC can write out and read in DDC  
(v)Design: RTL files which has the behavioral model of the design  

3.SDC format:  
–design intent in terms of $\textcolor{purple}{\text{timing, power(upf file) and area constraints}}$  
-supported by different EDA tools across semiconductor industry  
-SDC is based on Tool Command Language (TCL)  

4.Here is the Implementation flow of ASIC:  
![Picture6](https://user-images.githubusercontent.com/118953915/208279717-614c5061-d4cc-40f5-9546-6dc80ad15b23.png)
 
5.Here is the DC Setup   
![Picture7](https://user-images.githubusercontent.com/118953915/208279718-d7d02ea0-ff87-46d1-9017-849b9cf8215f.png)
 
6.Here is the DC synthesis flow:  
![Picture8](https://user-images.githubusercontent.com/118953915/208279723-e021b4a3-c13d-4517-896f-2cb31b38bcc2.png)
 
</details>  
 
<details><summary> Lab Session-> Lab1: Invoking DC basic setup</summary>  
 
#### **Lab1: Invoking DC basic setup**   
                                                                                    
>cd into home dir ; mkdir -p training ;  git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git   
>cd  sky130RTLDesignAndSynthesisWorkshop ; enter UE /p/hdk/pu_tu/prd/sams/mig76_wlw/setup/enter_p31 -cfg ip76p31r08hp7rev03 -ov ./   

Here is the .lib file locate at:  
Have converted the .lib format file into .db file, for DC to read in  
<img width="600" alt="Picture9" src="https://user-images.githubusercontent.com/118953915/208279726-9fc38c43-3ae8-4280-a46d-cfc9b57555c9.png">
 
Details of .lib:  
>gvim DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.lib ; switch off syntax :syn off  
  -.lib written out for a PVT corner  
<img width="900" alt="Picture10" src="https://user-images.githubusercontent.com/118953915/208279739-6eb98903-c2ac-46ea-a19e-44101d06bd29.png">
 
To invoke dc_shell, need to enable cshell first:   
>csh ; dc_shell  
>echo $target_library ; echo $link_library  
<img width="900" alt="Picture11" src="https://user-images.githubusercontent.com/118953915/208289654-d2ef9bdd-8724-4f0b-8de9-63cde17f74a8.png">  
 
>gvim DC_WORKSHOP/verilog_files/lab1_flop_with_en.v  
<img width="900" alt="Picture12" src="https://user-images.githubusercontent.com/118953915/208289656-388a7fcc-5bc1-4194-b2f6-808ba08f0ccd.png">  
 
>read_verilog DC_WORKSHOP/verilog_files/lab1_flop_with_en.v  
<img width="900" alt="Picture13" src="https://user-images.githubusercontent.com/118953915/208289657-cea07206-299c-4aef-b8b5-7804fd5fd497.png">  

>Write Verilog format : write -f verilog -out lab1_net.v   
>sh gvim /nfs/png/home/chiannio/training/sky130RTLDesignAndSynthesisWorkshop/lab1_net.v <img width="900" alt="Picture14" src="https://user-images.githubusercontent.com/118953915/208289658-38da9dfb-2a62-4bbd-95ed-19d154464e92.png"> 
 
If running like this , still not correct:  
>read_db DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db  
>write -f verilog -out lab1_net.v  

Should like this:  
There may be multiple libraries loaded in DC’s memory, so need  
set link_library {* <path to std cell library> }  
where * = lib already loaded in DC’s memory  
Eg: in previous DC’s memory have flops libs, now append new libraries to it without overwrite it   
>set target_library /nfs/png/home/chiannio/training/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db  
>set link_library {* /nfs/png/home/chiannio/training/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db}  
>link  
<img width="900" alt="Picture15" src="https://user-images.githubusercontent.com/118953915/208289650-d8f42e52-e691-4b38-8da3-04c550d14652.png"> 

Then, compile design  
>compile  
>write -f verilog -out lab1_net.v  
<img width="900" alt="Picture16" src="https://user-images.githubusercontent.com/118953915/208289652-232375c1-4479-4bd9-8c5c-2e24765801e7.png">
 
</details>  
 
<details><summary> Lab Session-> Lab2: Intro to ddc gui with design_vision</summary>  
 
#### **Lab2: Intro to ddc gui with design_vision**   
Invoke design vision (gui format of dc)   
>csh  
>design_vision  
<img width="900" alt="Picture17" src="https://user-images.githubusercontent.com/118953915/208289663-266bc31b-61b5-49dd-ae14-8d4899ed3312.png"> 

Command write ddc (in dc_shell)  
>Format in ddc: write -f ddc -out lab1.ddc  
Command read ddc   
>read_ddc lab1.ddc  
-ddc (synopsys properiety  format) save all information in the tool memory in that particular session  
-convenient when passing data from dc into icc by using .ddc  
<img width="900" alt="Picture1" src="https://user-images.githubusercontent.com/118953915/208290131-291eb76e-1761-4fa4-b54d-fd04ee42c6a2.png">
 
If read_verilog lab1_flop_with_en.v – read only Verilog file   
<img width="900" alt="Picture1" src="https://user-images.githubusercontent.com/118953915/208301495-a7f6b32a-1e16-49ab-ab62-11756b36b5cf.png">

 Here is the schematic view of design_vision:  
<img width="900" alt="Picture18" src="https://user-images.githubusercontent.com/118953915/208289666-d5d832d6-8ead-4b62-b878-748077fa79c8.png">
 
</details>
 
<details><summary> Lab Session -> Lab3: DC synopsys DC setup </summary>

Everytime invoke dc_shell need to set target_library and link_library  
Can set like this  
>set target_library /nfs/png/home/chiannio/training/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db  
>set link_library { * $target_library }  
<img width="900" alt="Picture19" src="https://user-images.githubusercontent.com/118953915/208289667-70bd1e08-76f0-49b6-ace8-b15805bf669c.png">
 
There are multiple .db files and setting manually is error prone, so we can use .synopsys_dc.setup  
In DC during installed will have a default one, and in out user home directory also will consists one. The DC will pick the one in our user home directory  
all repetitive tasks which is needed for tool setup can be pointed in this file- target_library and link_library  
Preconfigure must in home directory & the file name must .synopsys_dc.setup  
>gvim .synopsys_dc.setup  
>-set target_library ~/training/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db  
>-set link_library { * $target_library }  
 
After invoke dc_shell, the target_library and link_library have been set automatically  
> csh   
> dc_shell  
 <img width="900" alt="Picture20" src="https://user-images.githubusercontent.com/118953915/208289668-5f18ef08-65c8-484a-a37a-32bbce6afa56.png">
 
</details>  
 
<details><summary> ⚡ Lecture session: TCL quick refresher</summary>  
 
TCL quick refresher  
-all dc internal command based on tcl only  
 Here is some details on tcl scripting:  
 <img width="900" alt="Picture21" src="https://user-images.githubusercontent.com/118953915/208289670-1ea638e6-0a3e-4dd1-b999-e106030224d5.png">
 
</details>
 
<details><summary> Lab Session -> Lab4: TCL scripting </summary>
 
Here is example of TCL scripting:  
 <img width="900" alt="Picture22" src="https://user-images.githubusercontent.com/118953915/208289673-1a27b356-d318-4daf-afeb-9bd3ca958fda.png">
 
Another example on DC proprietary command:  
>foreach_in_collection my_var [get_lib_cells */*and*] {  
>set my_var_name [get_object_name $my_var]   
>echo $my_var_name;  
>}  
 <img width="900" alt="Picture23" src="https://user-images.githubusercontent.com/118953915/208289674-192b3bfb-e572-4fd0-9883-38930df1f2db.png"> 

Can save all the commands in a file and the source the file  
>sh gvim myscript.tcl  
>source myscript.tcl  
 <img width="900" alt="Picture24" src="https://user-images.githubusercontent.com/118953915/208289675-81a0329d-02ba-428e-97f3-a32ddb19778d.png">  

 
Further try on:  
<img width="900" alt="Picture25" src="https://user-images.githubusercontent.com/118953915/208289678-115075a2-ef74-4b8c-baf2-062515f554df.png">  
 
 
 💡Must always becareful of syntax and spacing in tcl scripting
 
</details> 

#
# Day_7 
**⭐Basics of STA**
 
<details><summary> ⚡ Lecture session: Introduction to course live session </summary>  

SDC Constraints  
Recap on Setup and Hold violations:  
<img width="900" alt="Picture1" src="https://user-images.githubusercontent.com/118953915/208871506-acd43498-eebe-45d9-a104-d95be05b2884.png">
 
1.Basics of STA  
<img width="900" alt="Picture2" src="https://user-images.githubusercontent.com/118953915/208871509-db0d89f5-74fe-477d-97a4-ea989ec70790.png">  
<img width="900" alt="Picture3" src="https://user-images.githubusercontent.com/118953915/208871468-3e1e1a8f-5ffd-4384-98fa-7063bffe6399.png">  
 
2.Basic terminology:  
Delay:  
<img width="900" alt="Picture4" src="https://user-images.githubusercontent.com/118953915/208871478-c68a70d8-6826-4cdf-9b66-ceddfc135fd3.png">  
 
Timing Arcs:  
<img width="900" alt="Picture5" src="https://user-images.githubusercontent.com/118953915/208871488-233cfc80-0245-4cce-b160-f774f3c84676.png">  
 
3.Timing path:  
<img width="900" alt="Picture6" src="https://user-images.githubusercontent.com/118953915/208871491-02e8928e-dd26-49e9-b2ee-5ede932ef25c.png">
 
4.Constraining the design  
<img width="900" alt="Picture7" src="https://user-images.githubusercontent.com/118953915/208871497-c910b8f7-f069-4ce9-97a0-a0ca45596074.png">

💡 SDC-Inportant on thse 3 metrics: Power,Performance,Area
>Can refer details on PPA card: https://www.vlsisystemdesign.com/ppa-power-performance-area-card

</details> 

<details><summary> ⚡ Lecture session: Introduction to STA</summary> 

*(A)Introduction to STA*  
STA Basic-Static Timing Analysis  
1.Min and Max constraints delay  
<img width="900" alt="Picture8" src="https://user-images.githubusercontent.com/118953915/208874119-554b6ea0-4acd-431e-98e3-8cdfc9c553c2.png">  

If two same bucket size with difference inflow speed->Delay is function of inflow  
->More inflow, less delay == Fast current sourcing, less delay == Fast rise, less delay  
If two bucket with difference size but same inflow speed->Delay is function of bucket size to be filled  
->High load capacitance, more delay  
 
💡 Delay of a cell will be a function of input transition and output load 
 
Here is the example:  
<img width="900" alt="Picture9" src="https://user-images.githubusercontent.com/118953915/208874123-96e7f9e6-0900-48cc-b89b-4bb1438feaf9.png">  

Timing Arcs for combination cell:  
<img width="900" alt="Picture10" src="https://user-images.githubusercontent.com/118953915/208874126-2146e99e-b65d-4125-a662-6fb9fd208892.png">  

Timing Arcs for sequential cell:  
<img width="900" alt="Picture11" src="https://user-images.githubusercontent.com/118953915/208874097-1842c09b-c89b-4495-94e7-a1c05effa5e5.png">  

(B) What are constraints?  
<img width="800" alt="Picture12" src="https://user-images.githubusercontent.com/118953915/208874108-32f57b7b-6514-467c-9aec-d1657f186241.png">  

Here is all the possible combination of timing paths:  
<img width="800" alt="Picture13" src="https://user-images.githubusercontent.com/118953915/208874112-67a2c33f-9724-4e78-968d-390481f5da97.png">  
 
In real design, we will based on frequency/Tclk to decide the delay/Tcombi  
-if design is 500Mhz=2ns, then after deduct the Tsetup=0.5ns and Tcq=0.5ns, we will have Tcombi=1ns  
-so clock period limit the combi  
-clock period will limit the delays in all reg2reg paths  
-synthesis tool will optimize logic based on the clock period (we provide to tool)  
-thn the tool will pick the appropriate cell from .lib to meet the delay  

Here is delay modelling:  
<img width="800" alt="Picture14" src="https://user-images.githubusercontent.com/118953915/208874116-c23c141d-515e-4ed3-9c7d-8fa87971c523.png">  

IO delay modelling is not sufficient, because:  
<img width="800" alt="Picture15" src="https://user-images.githubusercontent.com/118953915/208881153-a43f95c2-f229-4a05-9c4a-b68b6be4e119.png">

IO constraints- input transition and output load  
<img width="800" alt="Picture16" src="https://user-images.githubusercontent.com/118953915/208881157-9d67fb3d-9854-4c7f-9f0e-773b7919110e.png">

Summary on delay constraints:  
<img width="800" alt="Picture17" src="https://user-images.githubusercontent.com/118953915/208881161-72c75d2a-e6fe-48cb-93d0-8faccd51f414.png"> 
 
</details> 

<details><summary> Lab session-> Lab5: Timing Dot Libs</summary>

This is the details in .lib:  
> gvim /nfs/png/home/chiannio/training/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
1.For max_transition:  
<img width="600" alt="Picture18" src="https://user-images.githubusercontent.com/118953915/208881164-5107f673-e052-44e5-a9da-ac1f5dc2e311.png">

Capacitance:  
-input logic gate will fed to the gate terminal of MOSFET which have capacitance, so -there is input pin capacitance  
-net also have capacitance  
-output also have pin capacitance  
Here is the details:  
<img width="800" alt="Picture19" src="https://user-images.githubusercontent.com/118953915/208881171-14d3abd0-2bcc-4e4f-a26b-7a5308817be5.png">   

2.For delay model lookup table  
<img width="600" alt="Picture20" src="https://user-images.githubusercontent.com/118953915/208881176-a8554d3f-d04b-41b7-8f7d-bcbc3fa0d64c.png">

Here is the details:  
<img width="600" alt="Picture21" src="https://user-images.githubusercontent.com/118953915/208881179-e82653a7-5161-4cac-9fc4-f89c3a080dd4.png">  
 

Comparison among 2 AND gates:  
(i) Area an power  
<img width="900" alt="Picture22" src="https://user-images.githubusercontent.com/118953915/208881127-4eeee43b-52f2-48e7-9aa9-56b593177bf8.png">  
(ii) max_transition, clock attribute and direction of both same, but difference in capacitance  
<img width="900" alt="Picture23" src="https://user-images.githubusercontent.com/118953915/208881136-779556ba-3aa8-46b4-a4b6-9b6fa5666139.png">  
 
(iii) value in timing lookup table difference  
<img width="900" alt="Picture24" src="https://user-images.githubusercontent.com/118953915/208881138-52ef20cf-c929-4ed7-8493-708c8531a830.png">  

cell_rise and cell_fall have separate LUT  
<img width="900" alt="Picture25" src="https://user-images.githubusercontent.com/118953915/208881141-fb9d70ba-b760-4892-8f70-fcd94f9caf57.png">
  
(iv) unateness  
<img width="900" alt="Picture26" src="https://user-images.githubusercontent.com/118953915/208881142-5f1a9448-2826-41e6-ab20-02e271cab333.png"> 

</details> 

<details><summary> Lab session-> Lab6: Exploring dotLib</summary>
 
Here is the detail on unate and timing_type: 
<img width="900" alt="Picture27" src="https://user-images.githubusercontent.com/118953915/208881145-87a4f08f-e105-40fe-a885-e70ba7d9f5f6.png">

>get_lib_cells */* -filter "is_sequential==true"
<img width="900" alt="Picture28" src="https://user-images.githubusercontent.com/118953915/208881149-45d57fdb-97e1-4314-bb2b-b5e6da0e2975.png">
 
Select latch from list:
<img width="900" alt="Picture29" src="https://user-images.githubusercontent.com/118953915/208881151-a19401fb-b8db-46a6-a9b0-17abf0c44cb5.png"> 

 </details> 

<details><summary> Lab session-> Lab7: Exploring dot.lib part2</summary>
 
Show loaded library
>list lib
<img width="900" alt="Picture30" src="https://user-images.githubusercontent.com/118953915/208890405-356ed055-c0a1-4b93-be70-edb0e10cc4d8.png">

Trace all the AND cell libs
>get_lib_cell */*and*
<img width="900" alt="Picture31" src="https://user-images.githubusercontent.com/118953915/208890407-413f2314-3404-4f27-b222-e74c0d3ab83a.png">
 
Trace all the AND cell libs and list out one by one  
>foreach_in_collection my_lib_cell [get_lib_cells */*and*] {  
>set my_lib_cell_name [get_object_name $my_lib_cell];  
>echo $my_lib_cell_name;  
>}    

Different flavours of AND and NAND gates  
<img width="900" alt="Picture32" src="https://user-images.githubusercontent.com/118953915/208890397-3267b604-6517-49e4-b117-b9efc0391f28.png">

Here is some example for tracing attribute:  
> get_lib_pins sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and2_0/*

>foreach_in_collection my_pins [get_lib_pins sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and2_0/*] {  
>set my_pin_name [get_object_name $my_pins];  
>set pin_dir [get_lib_attribute $my_pin_name direction];  
>echo $my_pin_name $pin_dir ;  
>}  

>get_lib_attribute sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and2_0/A direction  

>get_lib_attribute sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and2_0/X function  
<img width="900" alt="Picture33" src="https://user-images.githubusercontent.com/118953915/208932144-3c5d8cbf-449e-49d3-ac1a-01272a475567.png">  

Another example on NAND gate:  
<img width="900" alt="Picture34" src="https://user-images.githubusercontent.com/118953915/208932149-7934baf7-668c-4b36-bc69-5da48529f197.png">  
 
Another example:   
<img width="900" alt="Picture35" src="https://user-images.githubusercontent.com/118953915/208932112-fcd69910-7bb4-4f94-ab0f-a647733f4765.png">  

Another example:  
<img width="900" alt="Picture36" src="https://user-images.githubusercontent.com/118953915/208932120-6db8c462-c847-412d-b543-6d19703b01bf.png">  

Example on create a list to trace the functionality of multiple cells:  
<img width="900" alt="Picture37" src="https://user-images.githubusercontent.com/118953915/208932126-26fc637b-9ca4-427d-9798-7ca1eb9e3894.png">  
 
There is more attributes can be trace:  
<img width="900" alt="Picture38" src="https://user-images.githubusercontent.com/118953915/208932138-8f4a1da0-d748-4389-a54d-4e24a4eb5fb3.png">  

Can use this command to check the attribute is define on lib_cell/cell/pin  
>list_attribute -app  
<img width="600" alt="Picture39" src="https://user-images.githubusercontent.com/118953915/208932142-511112b0-3b52-423f-9882-42e5084fc515.png">    

</details>
 
#
# Day_8 
**⭐Advanced SDC Constraints**

<details><summary>⚡Lecture Session: Introduction to course live session </summary>

### *__Lecture Session__*

<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209568494-7961f190-6a56-42d8-887a-6decb87875e3.png">  
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209568568-2c3e52db-751a-4707-af6d-4d467c20db1e.png">  
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209569443-fb1e68eb-b2ff-4f72-8bad-da0a44ad3a78.png">  
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209568624-4aedd451-742d-4fe1-8cb3-d67c53deb758.png">  
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209568649-f5cd5ad5-22dd-44f2-92f8-48abc0876b67.png">  
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209568673-7bfb36dc-a60d-4af8-bd45-02f7c747ddcd.png">  
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209569702-e60ee098-d4c7-4b10-9b70-af557ca4d556.png">     
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209568725-0827078d-5282-409b-adb6-9176b16a8e7e.png">  
 
</details> 

<details><summary> ⚡Lecture Session: Advanced Constraints,Specifying constraints through SD </summary>
 
### *__Lecture Session: Advanced Constraints,Specifying constraints through SD__*
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209569966-dd4c87a4-379d-4b0b-b728-16b072796a78.png"> 
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209570054-2f09a03e-fcf8-4172-8def-3f52348d1606.png">
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209570156-e95e8cbc-cfae-43c1-baab-2e7365694f27.png">
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209570233-3c1c6afe-9e7f-43fa-874b-b834e5a23caa.png">  

Query the ports in the design  
>get_ports clk  

A collection of ports where name contains clk  
>get_ports *clk* <- wildcard ‘*’ supported   

All ports of design  
>get_ports *  

Filtering based on condition, input ports  
>get_ports * -filter “direction==in”  
> get_clocks * -filter ”filter>10”  

Query the attribute  
> get_attribute [get_clocks my_clk] period  
> get_attribute [get_clocks my_clk] is_generated  

Report all detaiks  
>report_clocks my_clk  

Listing all the cells across all the hierarchies in the design (physical and hier cells)  
> get_cells * -hier  

Check hier or phy  
> get_attribute [get_cells u_combo_logic] is _hierarchical  

![image](https://user-images.githubusercontent.com/118953915/209570336-0d297763-7d46-47f9-b299-a53352623736.png)

Clock Distribution  
(i) create clock  
> create_clock -name <clock name> -per <clock period> [clock definition point]  
>Eg: create_clock -name MY_CLK -per 5 [get_ports CLK]  
 
💡 Clock must be created on the clock generators (pll,oscillators) or primary IO pins (for external clocks). Clocks should not be created on hierarchical pins   which are not clock generators  
 
(ii) Bringing in the practicalities(latency,uncertainty) of clock network  
This is for latency, modelling the clock delay in network  
>set_clock_latency 3 MY_CLK  
 
This is setting the clock network (skew+jitter)  
>set_clock_uncertainty 0.5 MY_CLK   
> -> post-cts only reflect jitter, skew calculate from clock network(physical build)  
> -> so during post-cts Set_clock_uncertainty 0.2 MY_CLK (only jitter)  

<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209570792-26dc7298-d8cc-4fc3-ad49-8b89328ef3e8.png">  
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209570810-da9d4267-c2e7-41fe-9840-492071c638b1.png">  
  
</details> 

<details><summary> Lab Session->Lab8: Loading design get_cells,get_ports,get_nets</summary>
 
### *__Lab Session__*
 
<img width="959" alt="image" src="https://user-images.githubusercontent.com/118953915/209571091-49bc92de-317f-45ac-a9c6-add7bab1dbb1.png">  
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209571106-a90b60f9-ca7f-4fd9-9f7c-b7b3256941c3.png">  
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209571128-23f16198-7709-4f99-8487-d3e4a2637166.png">  
 
Here is the shecmatic:   
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209571172-5633ebf3-f60a-4648-9e2a-791ce3343492.png">  
 
</details> 
 
<details><summary> Lab Session->Lab9: get_pins, get_clocks, querying_clocks</summary>  
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209571954-d772211d-9d3c-41f9-9de7-d783a413c61b.png">  
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209571991-24633605-853d-400c-af7c-d6a6da3b3fb8.png">  
 
</details> 
 
<details><summary> Lab Session->Lab10: create_clock waveform</summary>
 
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209572086-eada38be-e6d0-4914-a924-488feac29e4f.png">  
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209572109-8c613e96-ed4a-4498-ae53-df8e4fae6327.png">  

</details> 
 
<details><summary> Lab Session->Lab 11: Clock network modelling-uncertainty,report_timing</summary>

<img width="922" alt="image" src="https://user-images.githubusercontent.com/118953915/209572351-262c65ff-3336-445b-b88d-fc2d8490750c.png">  
Comparison:  
<img width="935" alt="image" src="https://user-images.githubusercontent.com/118953915/209572368-7ee29d3f-d801-4886-8244-6adab301f409.png">  
<img width="923" alt="image" src="https://user-images.githubusercontent.com/118953915/209572421-64fabf87-71db-4e75-bdd1-8b9d35c18b57.png">  
<img width="932" alt="image" src="https://user-images.githubusercontent.com/118953915/209572602-bb4240a9-8818-41a5-a82a-6d45fcad2c09.png">
 
</details> 
 
<details><summary> Lab Session->Lab 12: IO Delays</summary>  
Set input delay:  
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209572739-951b9405-4c60-4bdc-958e-008ecf9a4c85.png">
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209572775-e43d43e8-5540-49ae-9f86-c1cae3601217.png">
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209572786-40d550b1-1c6c-41c8-8a60-78919b8e308e.png">
<img width="674" alt="image" src="https://user-images.githubusercontent.com/118953915/209603151-7ec7f33d-fdd9-4532-907f-8149970fc40a.png">  

Set output delay:  
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209573377-48eb7f80-7faf-4428-80c0-b6e4067a2571.png">
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209573397-fefd62d3-7ce2-484b-a1f9-2ac037b98385.png">

</details> 

<details><summary> ⚡Lecture Session: Generated_clk</summary>
 
### *__Lecture Session: SDC Part3 generated_clk__*
 
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209573559-d81ec488-ecca-44d9-8ddf-c3bdb77af7fc.png">
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209573596-b22bde60-1e23-48c2-95d3-0f66581ad8ad.png">

</details> 
 
<details><summary> Lab Session->Lab13: Generated_clocks</summary>  
Create generated clock:   
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209573793-b2b9ca82-29f1-46d2-82d8-88536b58732e.png">
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209573810-82fcd486-5625-43e1-898f-191941db3408.png">
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209573824-95d5e8cf-1eb2-45b7-88c2-4c2cc61233a1.png">
<img width="960" alt="image" src="https://user-images.githubusercontent.com/118953915/209573856-e6cb8268-cc6c-4609-bb55-173eec0b8d8e.png">
 
</details> 
 
<details><summary> ⚡Lecture Session: VCLK,max_latency, rise_fall IO delays </summary>
 
### *__Lecture Session: SDC part4 vclk, max_latency, rise_fall IO delays__* 
<img width="662" alt="image" src="https://user-images.githubusercontent.com/118953915/209574167-0f5d151e-7620-4167-8ff7-40726f0d06c3.png">
<img width="260" alt="image" src="https://user-images.githubusercontent.com/118953915/209576040-45c771a5-c27d-433b-88fb-c3cdf8f5a72f.png">
<img width="656" alt="image" src="https://user-images.githubusercontent.com/118953915/209574183-43a07d86-0841-4000-b213-33bef60e0a9c.png">
<img width="754" alt="image" src="https://user-images.githubusercontent.com/118953915/209574211-cde776cf-b4be-4f81-8a72-a738ef884e98.png">  

If there is negedge flops:  
<img width="749" alt="image" src="https://user-images.githubusercontent.com/118953915/209574233-01734396-57ee-47fc-9af2-57b298e595a9.png">
<img width="754" alt="image" src="https://user-images.githubusercontent.com/118953915/209574252-65510875-11fd-4d17-8ecc-177432aa1dd7.png">  

Comparison among two:  
<img width="777" alt="image" src="https://user-images.githubusercontent.com/118953915/209574266-132a17a4-6aeb-4a37-8be8-8ba2a7908535.png">

</details> 
 
<details><summary> Lab Session->Lab14: part1 Set_Max_delay</summary>  
 
Proceed with lab14_circuit.v:  
<img width="748" alt="image" src="https://user-images.githubusercontent.com/118953915/209574707-0c3c8fe1-508d-4962-9bcc-2076290537cc.png">
<img width="779" alt="image" src="https://user-images.githubusercontent.com/118953915/209574733-31ccda80-f4e7-4889-adda-f1e94d53c91f.png">  
<img width="773" alt="image" src="https://user-images.githubusercontent.com/118953915/209574758-a0bc273d-d769-481c-810f-25edf09cc463.png">
<img width="780" alt="image" src="https://user-images.githubusercontent.com/118953915/209574781-a60e4673-85d2-4de5-910a-0ad60ec6100c.png">  
 
After compile_ultra, the tool will optimize:  
<img width="779" alt="image" src="https://user-images.githubusercontent.com/118953915/209574800-2f9d8aea-8927-4c46-bc59-918eb57f4502.png">
<img width="781" alt="image" src="https://user-images.githubusercontent.com/118953915/209574813-04e3da81-b2f1-4af0-8768-0f028ddefd46.png">
 
</details> 
 
<details><summary> Lab Session->Lab15: part2-VCLK</summary>  
 
<img width="781" alt="image" src="https://user-images.githubusercontent.com/118953915/209575088-0eebc843-a1e6-40b9-b694-246c3b8054bf.png">
<img width="779" alt="image" src="https://user-images.githubusercontent.com/118953915/209575124-7ec562ac-21f0-44d2-ba91-aacbc016085f.png">

 After compile_ultra, the tool will optimize:  
<img width="782" alt="image" src="https://user-images.githubusercontent.com/118953915/209575139-b0c9e1b8-e005-4fe3-aedf-6523f1d718e7.png">

 > All SDC command -> [SDC.constraints.command.txt](https://github.com/ChianNi/Intel_SD_Training/files/10325261/SDC.constraints.command.txt)
 
</details> 
 
#
# Day_9 
**⭐Optimization in synthesis**

<details><summary> ⚡ Lecture Session: Introduction to course live session </summary>

### *__Lecture Session__*

**Optimizations**

✏️Recap  
-Combinational Optimization is still very much Boolean optimization  
-In DC, Querying makes job easier for manual cell replacement -> wildcard *  
-Replication and reuse of logic can be done for resource sharing, always be cautioned about over-constraining, may lead to explosive area increase <- $\textcolor{green}{\text{must optimal}}$  
-Sequential Optimization remains an exercise in timing plus Boolean optimization   
-Explicit representation of tie cells to represent constant assignment is an addition here    
-Also, sequential constant propagation can be limited via compile_seqmap_propagate_constants set as false    

Synopsys Directives  
1.Embedding Constraints and Attributes  
Constraints and attributes, usually entered at the dc_shell prompt, can be embedded in your Verilog source code   
Prefix the usual constraint or attribute statement with the Verilog comment characters //, and delimit the embedded statements with the compiler directives   
> // synopsys dc_script_begin and // synopsys dc_script_end  

The following limitations apply to the use of constraints and attributes in your design:  
-Constraints and attributes declared outside a module apply to all subsequent modules declared in the file  
-Constraints and attributes declared inside a module apply only to the enclosing module  
-Any dc_shell scripts embedded in functions apply to the whole module  
-Include in your dc_shell script only commands that set constraints and attributes. Do not use action commands such as compile, gen, and report  

(i)Synopsys full_case  
-When adding "full_case" or "parallel_case" directives to a case statement, the directives are added as a comment immediately following the case expression at the end of the case statement header and before any of the case items on subsequent lines of code  
-From a synthesis tool perspective, a "full" case statement is a case statement in which every possible binary pattern is included as a case item in the case statement  
-Synopsys parses all Verilog comments that start with "// synopsys ..." and interprets the "full_case" directive to mean that if a case statement is not "full" that the outputs are "don't care's" for all unspecified case items. If the case statement includes a case default, the "full_case" directive will be ignored  
(ii)Synopsys parallel_case  
-A "parallel" case statement is a case statement in which it is only possible to match a case expression to one and only one case item. If it is possible to find a case expression that would match more than one case item, the matching case items are called "overlapping" case items and the case statement is not "parallel.“
-In general, use parallel_case when you know that only one case item is executed  
-Under certain circumstances, you might not want to build a priority encoder to handle a case statement. You can use the parallel_case directive to force HDL Compiler to generate multiplexer logic instead  

2.Retiming/Pipelining  
Registers stop glitches from propagating through combinational paths  
-Pipelining is a technique that breaks combinational paths by inserting registers  
-By reducing logic-level numbers between registers, pipelining can result in higher clock speed operations  
However, pipelining increases the latency of a circuit in terms of the number of clock cycles to a first result    

![image](https://user-images.githubusercontent.com/118953915/209823059-7b1d332e-1e59-4992-92af-8f4fe5bbb2ad.png)  

Retiming as an algorithm allows shortening of critical paths  
-After providing a proper timing constraint file (consisting of clock definitions, clock uncertainty modelling, io delays and load) and observing a scope of retiming, we can provide the DC switch compile_ultra –retime, to see the results  

3.Boundary Optimization  
-Set_boundary_optimization module_sub false  
-It is helpful in ECOs  
-> because if issue happen associate to submodule, thn we can find out the issue easily if there is no boundary optimization  

4.Multi-Cycle and False Paths (revisited)  
>Set_multicycle_path –setup 2 –to prod_reg[*]/D –through [all_inputs]  
 
-Hold is always checked at 1 edge before setup, if not provided explicit instruction  
-Setup will move by endpoints  
-Whenever MCP is applied for setup, provide for hold as well  
 
>set_multicycle_path –hold 0.5 –to prod_reg[*]/D –through [all_inputs]  
>set_false_path –through <>  
 
5.Isolation of ports  
>set_isolate_ports –type buffer [get_ports Out_Y]  
 
-cell delay is a function of output load, which could impact internal path timing
-Possible Solution: Provide a buffer, which drives the external load and decouples it from internal path  
 
</details>  
 
<details><summary> ⚡ Lecture session: Combinational Optimization</summary>  

**Combinational Optimization** 
 
1.Optimization Goals:   
Cost function based optimizations  
->Optimization till the cost is met  
->Over optimization of one goal will harm other goals  <- $\textcolor{green}{\text{optimal}}$   
->goals for synthesis- meet $\textcolor{blue}{\text{timing}}$[IO delay, clock period, max_delay], meet $\textcolor{blue}{\text{area}}$, meet $\textcolor{blue}{\text{power}}$ (but all this 3 metrics of netlist will be contradictory)  
Eg: fastercell to meet timing, but causing area and power increase  
 
2.Combinational logic optimisation  
-squeenzing the logic to get the most optimized design  
->Area and power savings  
-Constant propagation   
->Direct Optimisation  
-Boolean LogicOptisation  
->K-Map  
->Quine McKuskey  

![image](https://user-images.githubusercontent.com/118953915/209823837-b56094f2-4ecd-48b3-a985-cfd2ae2ee9c5.png)   
![image](https://user-images.githubusercontent.com/118953915/209823874-5d332bae-62fd-4f95-a0d4-0a0c6b2bc598.png)  
![image](https://user-images.githubusercontent.com/118953915/209823902-2f24ade3-6a25-472b-8d8d-1b97267ca0fc.png)  
![image](https://user-images.githubusercontent.com/118953915/209823936-f2a95b95-d061-4b66-bea2-7b8b18733ea9.png)  
 
💡 All implementation decided by constraints, so need setup constraints properly so that tool able to pick up constraints and get the best optimized design 
 
</details>  
 
<details><summary> ⚡ Lecture session: Sequential optimizations</summary>  

**Sequential optimizations**  

1.Sequential logic optimisation  
For basic:  
-Sequential constant propagation  
-Retiming  
-Unused flop removal  
-clock gating  
For advanced(not covered as part of lab):  
-state optimisation  
-sequential logic clonning (floorplan aware synthesis)  
![image](https://user-images.githubusercontent.com/118953915/209824522-3f4b74f2-9461-4a1b-b2ec-a6df260e1009.png)  
![image](https://user-images.githubusercontent.com/118953915/209824541-07272d7d-7545-4c3c-8925-6de583ad4125.png)  
![image](https://user-images.githubusercontent.com/118953915/209824557-9d4bfb74-fb7d-40ac-a6a3-aec8c81dbea2.png)  
![image](https://user-images.githubusercontent.com/118953915/209824576-cb4beb2e-4b0b-4262-9676-07b506a6236d.png)  
Here is the command:   
>compile_seqmap_propagate_constants TRUE  
>compile_delete_unloaded_sequential_cells TRUE  
>compile_register_replication TRUE  [advance-floorplan aware synthesis (for cloning registers, when there is few fanouts far away from reg, we can clone another reg to optimal routing  

 </details>  

<details><summary> Lab Session->Lab16: Part1 Combinational optimizations</summary> 
 
>read_verilog DC_WORKSHOP/verilog_files/opt_check.v  
>report_timing  
>link  
>compile_ultra  
> write -f ddc -out opt_check.ddc  
>read_ddc opt_check.ddc < in design vision 
                            
![image](https://user-images.githubusercontent.com/118953915/209824823-ef4ccdd4-e571-4d8d-b926-b3d1dcb4778a.png)  
![image](https://user-images.githubusercontent.com/118953915/209824869-dbc23996-5ef9-43e7-a6d2-a3f73e12b486.png)  
                            
For the rest 3 opt_check*
>read_verilog DC_WORKSHOP/verilog_files/opt_check<>.v
>link
>compile
>gui_start

![image](https://user-images.githubusercontent.com/118953915/209825840-9b14c480-19a6-4443-9a88-1d46917bd75f.png)  
 
![image](https://user-images.githubusercontent.com/118953915/209824948-41dc1392-e957-4fab-9c64-c3d68487a68a.png)  
Check the timing for opt_check4:  
![image](https://user-images.githubusercontent.com/118953915/209825121-e5c43f58-2d2e-4f42-822a-8668bcf85064.png)
 
>get_lib_cells */sky130_fd_sc_hd__xnor2_*
>size_cell U4 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__xnor2_4  
 
![image](https://user-images.githubusercontent.com/118953915/209825158-09992d37-9231-4736-b663-cb80feb80a9c.png)
                       
</details>  
 
<details><summary> Lab Session->Lab16: Part2 Resource sharing optimizations</summary> 
 
![image](https://user-images.githubusercontent.com/118953915/209826204-20d11d04-1deb-4d5a-acb0-086f7f9f435f.png)  
 
Here is the details on RUN1 without any constraints applied:
>report_area  

![image](https://user-images.githubusercontent.com/118953915/209826233-0f21754c-8c17-4dd5-9ea2-a1a6456b7dfc.png)  
Here is the schematic:  
![image](https://user-images.githubusercontent.com/118953915/209826276-1da7e51e-cf58-45a2-86e7-851537e3173c.png)  
There is no constraints path, so need to  
![image](https://user-images.githubusercontent.com/118953915/209826445-fbd5b41e-ab91-46cb-a94e-657204c0ce99.png)  
![image](https://user-images.githubusercontent.com/118953915/209826485-5b19570a-29c8-4f4e-9db2-1fc81a0bda24.png)

Here is the details on RUN2 with constraints applied:  
![image](https://user-images.githubusercontent.com/118953915/209826664-12a745e8-62b5-466c-81e3-a1db753de00c.png)  
![image](https://user-images.githubusercontent.com/118953915/209826686-8c51fb43-002b-49ff-9448-372f7c90f7c7.png)  
 
Here is the details on RUN3 with constraints applied and area limit:
![image](https://user-images.githubusercontent.com/118953915/209826708-1a8f75a3-b12d-47f5-b02b-5364b2ebe471.png)

</details>  

<details><summary> Lab Session->Lab17: Sequential optimizations</summary>
 
For dff_const1.v:   
![image](https://user-images.githubusercontent.com/118953915/209827711-ae726792-c200-43b2-b721-ede3be263a24.png)  
From the schematic, have notice that there is a cell:  
![image](https://user-images.githubusercontent.com/118953915/209827758-355b358c-8c31-40be-a332-26a39d59bf54.png)

For dff_const2.v:  
![image](https://user-images.githubusercontent.com/118953915/209827853-29c0e662-f592-48f3-bf4d-8e0a02319be7.png)

For dff_const3.v: 
![image](https://user-images.githubusercontent.com/118953915/209827884-cd764bbc-9c37-4f2a-b7b6-8d6085744b69.png)  
Here is the schematic:  
![image](https://user-images.githubusercontent.com/118953915/209827952-bd4de3c8-fb4f-4b5f-bb6b-7a24168ad849.png)

Back to dff_const2.v:
There is sequential constant optimization, now we want to disable it by following command:  
> set compile_seqmap_propagate_constants false 

![image](https://user-images.githubusercontent.com/118953915/209828045-eed60ee1-204e-4fd2-9001-54ab38bf04fc.png)  

For dff_consr4.v:  
![image](https://user-images.githubusercontent.com/118953915/209896654-4eeca7ae-454c-4076-9fb2-368554b0dabd.png)

For dff_const5.v:  
![image](https://user-images.githubusercontent.com/118953915/209828116-c04c8feb-c203-4d29-a956-97e7e39c2554.png)
 
</details>   

<details><summary> ⚡ Lecture session: Special optimization </summary>  
 
**Special optimizations**  

Register retiming:
![image](https://user-images.githubusercontent.com/118953915/209842721-814884a8-435d-4e30-96a6-80b7e243141e.png)  
 
Boundary optimization  
![image](https://user-images.githubusercontent.com/118953915/209842747-331c4260-2313-47ad-a468-3f794742918f.png)  

If want preserve, use following command:  
>set_boundary_optimization <design> <true|false>
>Eg: set_boundary_optimization <module_sub> <true|false>
 
Multi-cycle paths  
![image](https://user-images.githubusercontent.com/118953915/209899444-5c4d537d-8b9c-462c-936e-cdcf6951f275.png)

False paths
>set_false_path –from <> -to <>
>set_false_path –through <>
 
![image](https://user-images.githubusercontent.com/118953915/209915231-376b2a72-30f1-4c07-9523-61d6060234d2.png)  
 
External Load vs Internal Loads  
>set_isolated_ports -type buffer [get_potrs Out_Y]
 
![image](https://user-images.githubusercontent.com/118953915/209915279-359f0e86-e108-4795-814a-20668eaf72ca.png)
 
</details>    

<details><summary> ⚡ Lecture session: How path are timed MCP </summary>  
 
**How path are timed MCP** 

![image](https://user-images.githubusercontent.com/118953915/210151529-04b364ed-7ef8-414a-b9fc-243c6f7aea50.png)
Another situation:  
![image](https://user-images.githubusercontent.com/118953915/210151539-10f309e6-ad0b-4242-8d5e-fc1e8b215f70.png)

For multicycle path:  
![image](https://user-images.githubusercontent.com/118953915/210151547-09e565ff-7c6f-45e9-a41b-dec00addb958.png)  
>set_multicycle_path –setup 2 –from [all_inputs] –to (PROD_REG[*]/D) <- endpoint edge moved forward  
>set_multicycle_path –hold 1 –from [all_inputs] –to (PROD_REG[*]/D) <- launch edge moved forward

![image](https://user-images.githubusercontent.com/118953915/210151553-c291bd39-8a3f-445a-aacc-768f84c8d55b.png)
     
</details> 
 
<details><summary> Lab Session->Lab18: Boundary Optimization</summary> 

 ✏️Recap:  
 ![image](https://user-images.githubusercontent.com/118953915/210151623-f7304e91-3b4a-41ea-b397-51a70d0d750d.png)  
For check_boundary.v:  
![image](https://user-images.githubusercontent.com/118953915/210151628-4904485e-927e-492b-9e60-fd45fb586a72.png)

>reset_design  
>read_verilog DC_WORKSHOP/verilog_files/check_boundary.v  
>link  
>compile_ultra  
>write -f ddc -out boundary.ddc  
>read_ddc boundary.ddc <- in design_vision  

![image](https://user-images.githubusercontent.com/118953915/210151634-d91c4365-83a4-4eba-a4ce-4325ea43cca4.png)
> set_boundary_optimization u_im false  
 
![image](https://user-images.githubusercontent.com/118953915/210151647-b76c635c-c2b5-48ab-87fe-94f6250788b1.png) 
 
💡 Advantage: Optimized logic
Disadvantage: If at latest stage need to perform function ECO, difficult to trace out the error, need consume more time to rerun the design too
                      
</details> 
 
<details><summary> Lab Session->Lab19: Register retiming</summary> 

![image](https://user-images.githubusercontent.com/118953915/210151664-ddcb72c3-d848-4bfc-96a0-ec696b3eb5e8.png)

Set constraints:  
![image](https://user-images.githubusercontent.com/118953915/210151681-789356b8-08f7-430b-af41-d64ba954f756.png)  

Enable retiming-Partition huge combo logic – register retiming  
>compile_ultra -retime
 
![image](https://user-images.githubusercontent.com/118953915/210151688-3eaf28c8-f192-4a8c-b45a-6d9c8dd11866.png)  

 > report_timing -from [all_inputs] -trans -cap -nosplit 
 
![image](https://user-images.githubusercontent.com/118953915/210151693-10660168-260c-4b43-b6da-b0b3415169c3.png)
 
</details> 
 
<details><summary> Lab Session->Lab20: Isolating output ports</summary> 
 
✏️Recap:  
Purpose: To prevent internal paths to fail because of external load by isolate the port by using buffer
Buffer drives external load, internal paths are decoupled from output paths
![image](https://user-images.githubusercontent.com/118953915/210151706-42ddf3b1-fab6-482a-bf8c-d70131f6a4c9.png)  
 
Use back this check_boundary.v:  
![image](https://user-images.githubusercontent.com/118953915/210151714-165748db-38c4-40a3-9737-c3e3ddaab75f.png)

Here is the detail of schematic:  
![image](https://user-images.githubusercontent.com/118953915/210151719-b5c3e3c3-436a-43a0-9244-aeaafc59ce5b.png)
 
>set_isolate_ports -type buffer [all_outputs]
 
![image](https://user-images.githubusercontent.com/118953915/210151728-6f9c3285-bc55-4f0a-b676-56b459df6f3d.png)
 
Set constraints:  
>![image](https://user-images.githubusercontent.com/118953915/210151734-078a5e7f-420a-43a1-8142-0225631becde.png)

Checking timing reports:  
Before isolating output ports:  
![image](https://user-images.githubusercontent.com/118953915/210151740-2b45b147-9bbd-4883-89f3-26b26453acfb.png)  

After isolating output ports:  
![image](https://user-images.githubusercontent.com/118953915/210151747-1f256964-74ef-4c5b-8497-fdc1a7105a64.png)
![image](https://user-images.githubusercontent.com/118953915/210151758-1ea8ea29-d294-428d-acb9-d9d30006f971.png)

Set constraints:   
>![image](https://user-images.githubusercontent.com/118953915/210151768-45aba9ee-be89-4cb4-9238-da52ca57ff88.png)

![image](https://user-images.githubusercontent.com/118953915/210151772-aa550e7a-b6e2-46c9-8010-6a329edaf9c4.png)

> set_multicycle_path -setup 2 -to prod_reg[*]/D -from [all_inputs]  

![image](https://user-images.githubusercontent.com/118953915/210151780-8c7e8aa1-ac1d-494a-ba6a-423779a02499.png)

Need to reconstraints:  
![image](https://user-images.githubusercontent.com/118953915/210151786-3219e145-9c5b-4dc2-9cce-62f13ef0f08d.png)
![image](https://user-images.githubusercontent.com/118953915/210151793-b87d912d-afdf-4148-a69b-31fbe280aaff.png)

Check for hold check timing:  
![image](https://user-images.githubusercontent.com/118953915/210151802-b5099574-8577-4f8a-b45c-221a05ae4140.png)

✏️Recap for hold check in MCP:
![image](https://user-images.githubusercontent.com/118953915/210151809-0d7b0351-0039-4a97-88b5-28a152616d09.png)

Need to constraints for hold path too, else will single cycle hold check:  
>set_multicycle_path -hold 1 -from [all_inputs] -to prod_reg[*]/D <- * multiple bit register
                                                                     
![image](https://user-images.githubusercontent.com/118953915/210151815-9b98a043-3d9f-48f0-ae0a-e3a4cb2007e5.png)
![image](https://user-images.githubusercontent.com/118953915/210151818-00a5208e-d2d6-4b82-9495-987ad7c56b19.png)

</details> 

#
# Day_10 
**⭐QOR**

<details><summary> ⚡ Lecture Session: Introduction to course live session</summary>

**Checking Netlist Quality and Generating Reports**

1.Generating Timing Reports  
-The delays associated with timing parameters are modelled on semiconductor device physics principles  
-Transistor sizing, their type, and how they are connected to each other contributes to different cells, and in turn different cell delays  
-Similarly, wires can be modelled in terms of Resistance and Capacitance, which in turn adds to the path delay. The path with the worst delay is the critical path  
Generate timing report command and flags:  
->report_timing  
 
Flag/Switch | Details |  
---|---|   
-to {list of signals} | Inputs/flipflop outputs to these signals|  
-from {list of signals} | Flip-flop outputs/inputs to these signals|  
-through {list of pins} | Paths that go through these pins|    
-max_paths N | Specifies the number of paths to be reported per path group |  
-n_worst paths_per_endpoint| Specifies the number of paths to be reported per endpoint per path group|    
  
-DC makes a note of all paths (unateness: fall to rise, rise to fall, ...) and uses hat for timing path calculations, apart from the provided constraints    
 
2.The difference between the clock signal’s arrival time (called data required time in the report) and the data signal’s arrival time (data arrival time) is called the slack:  
> Slack = data required time - data arrival time  

Timing Check | Details | Comments | Formula |  
----|---|---|---|  
Setup Check | For your circuit to work at the specified cycle time, the clock signal’s rising edge should always arrive later (or at the same time) than your data signal |  slack should be non-negative| Slack = data required time - data arrival time  |      
Hold Check | You want your data to change (data arrival time) a hold-time after the clock signal’s rising edge (data required time) | slack to be non-negative| Slack = -(setup slack) = -(data required time - data arrival time) = data arrival time - data required time |    
 
3.Command:  
(i)check_design   
->Checks for design consistency. E.g.: Will report a feedthrough, as we take out_clk in some of our examples directly from the defined clock ->list out warning/error  
(ii)check_timing  
->Checks for the specification of constraints, and also let us know if the provided constraints are enough. It might not specify proper endpoints to be constrained, that we need to justify  
(iii)report_constraints  
->provides us with a glimpse as to how our design is feasible in terms of electrical parameters such as power and capacitance <-power.area,timing 
                                                   
4.In digital electronics, the fan-out is the number of gate inputs driven by the output of another single logic gate  
-Generally clock nets, reset, scan, enable nets are High Fanout Nets -> high capacitance causing delay  
-A high fan-out corresponds to a very high capacitance load, which in turn translates to timing violation, because of a high transition time which adds up in the delay calculation  
-set_max_capacitance helps in breaking or buffering the High fanout net  
-> Eg: If there is 16 fanouts, can having 4 buffer where each of them drive 4 fanouts  

✏️ Summary  
-Constraints: clock, genclk (if any), vclk (if any), practicalities of the clock (Uncertainty and Latency), input, output delay, transition, load, set_max_capacitance, transition, etc  
->Pre-CTS=jitter+skew, Post-CTS=jitter  
-Synthesis Optimization Parameters: Boundary Optimization, Retiming, Constant propagation, unused flop removal, isolating ports, etc. <- can switch off  
-Flow: read_verilog, provide dbs, source constraints, check_design, check_timing, compile or compile_ultra, report_constraints, report_area and report_timing, write  
-QOR: Quality of Results, if you are meeting all your design constraints with good margins, the QOR is good  

5.Synopsys DC User Guide Flow:                                      
![image](https://user-images.githubusercontent.com/118953915/210175540-f79c9c19-e6de-4f47-b6f9-a1a01c4cb87e.png)  
Some command details:  
-set_wire_load_model- Sets  the  wire_load_attach_name  attribute  on  designs, ports, hierarchical cells of current design, for selecting a wire  load model to use in calculating wire capacitance
-set_propagated_clock- Specifies  propagated  (rather  than  ideal)  clock  latency for listed objects

</details>

<details><summary> Findings on QTM/ETM </summary>

**Findings on QTM/ETM:**     
 
1.Timing Models:  
-If we want to perform static timing analysis on a chip using PrimeTime, every leaf cell must have a timing model  
For static timing purposes, a leaf cell can be a simple macro cell (NAND, flops,...) or a complex block (RAM, microprocessor,...)  
-In Flat full chip timing analysis we need to read gate level netlist along with SPEF/SDF, timing libraries and constraints.Using this approach designers should wait till all blocks completion prior to performing full chip timing  
-Hierarchical STA flow allows you to partition different blocks using timing models which should completely model the full input/output timing characteristics without requiring the complete netlist of the block and Do not model every path in the block  
-Internal register to register paths are generally discarded, as these paths can be analyzed at the block level using the complete gate-level netlist  
->Hierarchical STA flow has several benefits. Hierarchical STA reduces runtime and memory usage compared to flat STA. The actual run time savings depend on the design complexity  

Types of Timing Model:  
(i)ETM Extracted Timing Models  
(ii)ILM Interface Logic Models  
(iii)QTM Quick Timing Model  

2.ETM (Extracted Timing Models)  
-The Extracted Timing Model (ETM) is an abstraction of the block using sequential and combinational timing arcs. NLDM lookup tables are extracted for each of the timing arcs whose delay is a function of input transitions and output loads, which makes the ETM usable with different input transition times and different output loads  
-Using ETMs to abstract the timing model of a complex block or IP hides the detailed design implementation information  
This usage model is ideal for IP providers  
(i) Block based model (lib)  
(ii) Contents of block are hidden 
(iii) Original netlist replaced by model containing timing arcs for block interfaces  
(iv) NLDM lookup tables are extracted for each of the timing arcs  
(v) These arcs whose delay are a function of input transition and output load. This makes ETM usable with different input transition times and different output loads  
(vi) Multiple modes per model  
(vii) Single PVT per model  

-Used for implementation (not sign-off) of IP models. Here the content are protected because the model contains abstracted timing information, without any netlist information  
 
Here is the ETM model Illustration:
![image](https://user-images.githubusercontent.com/118953915/210175632-13706b44-e4e1-43cd-8abc-52e2cdc450c6.png)  
 
3.QTM (Quick Timing Models)  
In the early stages of the design cycle, if a block not yet have a netlist, we can use a quick timing model to describe its initial timing. Later in the cycle, we can replace each quick timing model with a netlist block to obtain more accurate timing  

>Can refer here for more detials: http://mantravlsi.blogspot.com/2014/06/timing-models-etm-qtm-ilm.html
 
</details> 

<details><summary> ⚡ Lecture Session: Report timing</summary>

**Report timing**  
 
1.Generating Timing reports  
>report_timing -from DDF_A/clk  
>report_timing -from DDF_A/clk -to DDF_A/d  
>report_timing -fall_from DDF_A/clk  
>report_timing -rise_from DDF_b/clk  

For report_timing-The default setting for delay_type is max  
>report_timing -delay_type min -to DDF_C/d  
>report_timing -delay_type min -through INV/a  
>report_timing -delay_type max -through AND/b  
>report_timing -rise_from DDF_b/clk -delay_type max -nets -cap -trans -sig 4  
 
2.Propagation delay  
For INV:  
![image](https://user-images.githubusercontent.com/118953915/210175697-54a7febc-93ac-44e2-8cb1-1b27ef7e2dc4.png)  
 
For NAND:   
![image](https://user-images.githubusercontent.com/118953915/210175705-0a49567b-3664-4f29-8c47-94536e9a344c.png)

Here is the examples:   
![image](https://user-images.githubusercontent.com/118953915/210175710-e759d269-ee32-4806-9fad-64825a2de3f4.png)  
 
![image](https://user-images.githubusercontent.com/118953915/210175721-51aa668f-654d-4bbe-893e-20edc432fdc9.png)  

![image](https://user-images.githubusercontent.com/118953915/210175727-66f04e67-2d2b-475e-9730-400f64279709.png)

</details> 
 
<details><summary> Lab Session->Lab21: Report timing ports</summary> 

For lab8_circuit_modified:  
![image](https://user-images.githubusercontent.com/118953915/210176177-7bc75567-783a-4bc5-93a5-fe5b4c936589.png)  
![image](https://user-images.githubusercontent.com/118953915/210193109-756f983c-41d4-4f99-a474-389dc67fa593.png)
![image](https://user-images.githubusercontent.com/118953915/210176192-04eeb015-fbcf-4f92-9022-d18576035862.png)
Now compare both situation:   
![image](https://user-images.githubusercontent.com/118953915/210176198-ff8c0c5c-6d4d-4979-b8d6-df075c8f6820.png)
![image](https://user-images.githubusercontent.com/118953915/210176201-36a8d368-feae-4e62-8240-a828413e897c.png)  
![image](https://user-images.githubusercontent.com/118953915/210176216-934b2d19-1604-4791-96f5-b83a3482a1e3.png)
![image](https://user-images.githubusercontent.com/118953915/210176220-bbb12ceb-95f0-43c4-98b3-16c2d5e200a5.png)
![image](https://user-images.githubusercontent.com/118953915/210176223-7c59ffcc-aaf8-418b-9b49-7e661d8036a0.png)
 
</details> 

<details><summary> Lab Session->Lab22: Lab check_timing, check_design, set_max_capacitance, HFN </summary> 
 
No look for utility inside DC tool to check whether we load design correctly and set constraints correctly  
>read_verilog DC_WORKSHOP/verilog_files/lab8_circuit_modified.v  
>link  
>check_design  

![image](https://user-images.githubusercontent.com/118953915/210192723-d058ffd9-7ede-4ce7-ab95-7c8f8469537b.png)  

Next. without source in constraints  
>compilte_ultra  
>check_timing <-check design whether have proper constraints or not 
                     
![image](https://user-images.githubusercontent.com/118953915/210192747-05d13bac-595b-4892-9d2d-8b06c824f4c3.png)  

Another command:  
>report_constraints  

![image](https://user-images.githubusercontent.com/118953915/210192758-740f6add-a861-4d3c-a05b-c04eb4b0d5b5.png)

Now source in constraints and recheck  
> source lab8_cons.tcl  
> check_timing  

![image](https://user-images.githubusercontent.com/118953915/210192777-140ca4c8-8173-4658-a45a-49f785d9dd4f.png)

>report_constraints  

![image](https://user-images.githubusercontent.com/118953915/210192786-1f2f2b2c-48de-46ba-8ac6-bd935bd6965c.png)

For mux_generate.v:  
![image](https://user-images.githubusercontent.com/118953915/210192909-711fc80a-e211-462c-931d-303180c6c692.png)
![image](https://user-images.githubusercontent.com/118953915/210192914-53833a13-1682-471b-9962-8f4f4f747d37.png)
![image](https://user-images.githubusercontent.com/118953915/210192917-8c21b68d-ba27-47ca-954b-c95d4040383b.png)

Reduce capacitance:  
> set_max_capacitance 0.025 [current_design]  
To check which constraint are violating:  
> report_constraints -all_violators  

![image](https://user-images.githubusercontent.com/118953915/210192924-892e4891-a99a-4ede-8798-315b42d8f5ea.png)
![image](https://user-images.githubusercontent.com/118953915/210192929-8042352a-88bb-4102-b24d-9e074aff8a4c.png)
![image](https://user-images.githubusercontent.com/118953915/210192932-bef04735-1c6f-40d6-a22c-1284c0195b97.png)

High fanout net (HFN)- Huge fanout==net huge loaded  
Here is the example:  
![image](https://user-images.githubusercontent.com/118953915/210192943-5431086d-96ee-4c71-bebe-633f827f8778.png)
![image](https://user-images.githubusercontent.com/118953915/210192944-56025912-73e7-4e38-a069-fb917128960f.png)

Here is the schematic:  
![image](https://user-images.githubusercontent.com/118953915/210192956-6bf1f6f8-7026-43fc-8f9c-9afad46a26b8.png)  
![image](https://user-images.githubusercontent.com/118953915/210192962-13423fdf-7dbe-4b07-828f-f8b84cbb1a08.png)
![image](https://user-images.githubusercontent.com/118953915/210192967-27061082-5616-480a-ae97-3c045a104b5e.png)
![image](https://user-images.githubusercontent.com/118953915/210192973-a167d3e6-ddb6-4018-99b0-eda2bb35fe10.png)
![image](https://user-images.githubusercontent.com/118953915/210192977-aee9b1a6-b1eb-4555-be80-7a5751d98b84.png)
💡 Use this 2 commands to break/buffer the high fanout net (HFN): set_max_capacitance & set_max_transition
-> else DC tool will take from lib limit, the value is set to around 1.5 which is huge (will not violate, sub-optimal)

✏️ Summarizing:

![image](https://user-images.githubusercontent.com/118953915/210193022-05e1ec3f-25fb-4442-ba5d-610c685d5dde.png)

</details> 

#
# Day_11 
**⭐ Introduction to the BabySoC**

<details><summary> ⚡ Lecture Session: Introduction to the BabySoC </summary>

### *__Lecture Session__*

$\textcolor{blue}{\text{SoC}}$: A system on a chip or system-on-chip is an integrated circuit that integrates most or all components of a computer or other electronic system  

1. What is SoC and Why SoC?  
- SoC is a single-die chip that has some different IP cores on it. These IPs could vary from microprocessors (completely digital) to 5G broadband modems (completely analog)  
- The design of a system on chip usually includes a central processing unit, memory, ports for input and outputs, secondary storage devices, and peripheral interfaces such as Timers, etc  
- Depending upon the requirement it can also consist of a digital or analog signal processing system or a floating-point unit  
- SoC with equivalent functionality will have increased performance and reduced power consumption as well as a smaller semiconductor die area  

2. Typical structure of Snapdragon SoC  
![image](https://user-images.githubusercontent.com/118953915/210402865-7f35f2d6-b2d4-4ec3-8f24-d6c95a8c8ea8.png)  
- A Central Processing Unit (CPU) is electronic machinery that carries out instructions from programs that allows a computer or other device to perform its tasks  
- The graphics processing unit (GPU) in your device helps handle graphics-related work like graphics, effects, and videos  
- Digital Signal Processors (DSP) take real-world signals like voice, audio, video, temperature, pressure, or position that have been digitized and then mathematically manipulate them  

 3. Types of SoC  
(i) SoCs built around a microcontroller   
(ii)SoCs built around a microprocessor, often found in cell phones (Oppo Reno: snapdragon)    
(iii)Specialized application-specific integrated circuit SoCs designed for specific applications that do not fit into the above two categories    
 
4. SoC Structure  
- An SoC consists of hardware functional units, including microprocessors that run software code, as well as a communications subsystem to connect, control, direct and interface between these functional modules  
- Functional components: Processor Cores (multi core), Memory(RAM,ROM), Interfaces, Digital Signal Processor (decoding images), decoder and encoder (interacting information, converting into code), others  
- Intermodule communication: Bus-Based Communication, Network on a chip  

Additional: 
- A peripheral is any computing device or equipment that is part of the computer but doesn't perform any core computing process. It is an externally or internally connected device that adds up or complements the host computer's capabilities or functionality in some form (keyboard, mouse)  
- A universal asynchronous receiver-transmitter ( $\textcolor{blue}{\text{UART}}$ ) is a computer hardware device for asynchronous serial communication in which the data format and transmission speeds are configurable. It sends data bits one by one, from the least significant to the most significant, framed by start and stop bits so that precise timing is handled by the communication channel  

5. SoC Design Flow  
![image](https://user-images.githubusercontent.com/118953915/210402906-616d374c-3345-401b-8344-c0ea1d29546f.png)  
 
6. How are Microchips made?
- The microchip manufacturing process involves hundreds of steps and can take up to four months from design to mass production  
- Silicon is a semiconductor. This means that it can conduct electricity and also act as an insulator. To allow it to become conductive, small quantities of specific atoms are added as impurities to the wafer. These impurity atoms must have a number of outer electrons that is either one more or one less than that of silicon  
- Steps: Making wafers->Masking->Etching->Doping->Testing->Packaging  
  
>Can refer for more details: https://www.infineon.com/cms/en/product/promopages/how-a-chip-is-made-video/  
>Can refer for more details: https://www.youtube.com/watch?v=bor0qLifjz4  

7. Introduction to BabySoC & BabySoC Components  
- $\textcolor{blue}{\text{VSDBabySoC}}$ is a small chip yet powerful RISCV-based SoC   
- The main purpose of designing such a small SoC is to test three open-source IP cores together for the first time and calibrate the analog part of it   
- VSDBabySoC contains one RVMYTH microprocessor, an 8x-PLL to generate a stable clock, and a 10-bit DAC to communicate with other analog devices  

Figure from training video:  
![image](https://user-images.githubusercontent.com/118953915/210402959-aeb6bb29-8e92-4e2e-b3e3-23ebdd5a342a.png)  
>Can refer this github for more details: https://github.com/manili/VSDBabySoC/blob/main/README.md#introduction-to-the-vsdbabysoc   

- $\textcolor{blue}{\text{RVMYTH}}$: RVMYTH core is a simple RISCV-based CPU  
  - $\textcolor{blue}{\text{RISC-V}}$ is an instruction set architecture (ISA) rooted in reduced instruction set computer (RISC) principles  
  - An Instruction Set Architecture (ISA) is part of the abstract model of a computer that defines how the CPU is controlled by the software  
  - A reduced instruction set computer (RISC) is a computer designed to simplify the individual instructions given to the computer to accomplish tasks  

$\textcolor{blue}{\text{RISC}}$  
- RISC processor has ‘instruction sets’ that are simple and have simple ‘addressing modes’. A RISC style instruction engages “one word” in memory. Execution of the RISC instructions are faster and take one clock cycle per instruction  
- RISC processor is implemented using the hardwired control unit. The hardwired control unit produces control signals which regulate the working of processors hardware. RISC architecture emphasizes on using the registers rather than memory  
![image](https://user-images.githubusercontent.com/118953915/210403010-0beaf654-99a9-4d3a-875c-2f166ce3f91f.png)  
  
RISC Instruction Sets  
- RISC instructions are simple and are of fixed size. Each RISC instruction engages a single memory word   
- RISC instructions operate on processor registers only  
- The instructions that have arithmetic and logic operation should have their operand either in the processor register or should be given directly in the instruction. This is because the registers are the ‘fastest’ available memory source  
- The registers are physically small and are placed on the same chip where the ALU and the control unit are placed on the processor  
>Example of RISC instruction sets:   
>The Load instruction loads the operand present in memory to the processor register  
>Load R2, A // load the operand present at memory location A to the processor register R2  
 
>Can refer here for more details on ISA: https://binaryterms.com/risc-processor.html  
 
 $\textcolor{blue}{\text{PLL}}$  
- A phase-locked loop (PLL) is a control system that generates an output signal whose phase is related to the phase of an input signal   
- PLL are widely used for synchronization purposes, including clock generation and distribution   
- PLL is an electronic circuit with a voltage or voltage-driven oscillator that constantly adjusts to match the frequency of an input signal  
- PLLs are used to generate, stabilize, modulate, demodulate, filter or recover a signal from a "noisy" communications channel where data has been interrupted  
- The main goal of a PLL is to synchronize the output oscillator signal with a reference signal. Even if the two signals have the same frequency, their peaks and troughs may not occur in the same place. Simply put, they do not reach the same point on the waveform at the same time  
- Phase difference-this is measured as the angle between the signals. For signals with varying frequencies, the phase difference between them will always vary, which means that one signal will lag or lead the other by a varying amount   
>Can refer here for more information: https://github.com/bharath19-gs/avsdpll28nm/#pll    

 $\textcolor{blue}{\text{DAC}}$
- A digital-to-analog converter or DAC is a system that converts a digital signal into an analog signal. Converts a digital input signal into an analog output signal from a number of binary inputs into a single output). In general, the number of binary inputs of a DAC will be a power of two  
- DACs are widely used in modern communication systems enabling the generation of digitally-defined transmission signals
- There are two types of DACs: Weighted Resistor DAC & R-2R Ladder DAC:  
  - A weighted resistor DAC produces an analog output, which is almost equal to the digital (binary) input by using binary weighted resistors in the inverting adder circuit. In short, a binary weighted resistor DAC is called as weighted resistor DAC  
  - The R-2R ladder DAC constructed as a binary-weighted DAC that uses a repeating cascaded structure of resistor values R and 2R. This improves the precision due to the relative ease of producing equal valued-matched resistors (or current sources)  

>Can refer here for more information: https://github.com/Devipriya1921/avsddac28nm#introduction    

8. Introduction to Modelling  
- Some initial input signals will be fed into BabySoC module that make the pll start generating the proper CLK for the circuit
- The clock signal will make the rvmyth to execute instructions in its imem. As a result, the register r17 will be filled with some values cycle by cycle  
- These values are used by dac core to provide the final output signal named OUT  
- So, we have got 3 main elements (IP cores) and a wrapper as an SoC and of-course there would be also a testbench module out there  
- -> Complete Physical Design Flow of VSDBabySoC [consisting of RVMYTH (Digital block), PLL & DAC(Analog blocks) ] 

>Refer this github for modelling details: https://github.com/manili/VSDBabySoC/blob/main/README.md#vsdbabysoc-modeling  
 
</details>

#
# Day_12 
**⭐BabySoC Modelling**

<details><summary> ⚡ Lecture Session: BabySoC Modelling - Live session </summary>

### *__Lecture Session__*  
✏️ Recap on SoC  
- SoC is a single-die chip that has some different IP cores on it. These IPs could vary from microprocessors (completely digital) to 5G broadband modems (completely analog)  
- SoC with equivalent functionality will have increased performance and reduced power consumption as well as a smaller semiconductor die area  

1. What does modelling mean?  
- $\textcolor{blue}{\text{Modelling and simulation}}$ is the use of a physical or logical representation of a given system to generate data and help determine decisions or make predictions about the system  
  - Models are representations that can aid in defining, analyzing, and communicating a set of concepts  
  - Modelling and simulation is widely used in the VLSI domain <- prevent lost  

- $\textcolor{blue}{\text{Purpose of modelling}}$ :  
- System models are specifically developed to  
  -support analysis, specification <- meet spec  
  - design <- make sense  
  - verification <- functionality  
  - validation of a system <-dft  
  - to communicate certain information <- ensure no glitch   

2. Modelling of the VSDBaby SoC  
- Going to model and simulate the VSDBabySoC, model the 3 main IP cores: RVMYTH modelling, PLL modelling, DAC modelling  
- Some initial input signals will be fed into VSDBabySoC module,that will get the PLL start generating the proper CLK for the circuit  
- The clock signal will make the rvmyth (RISCV based processor) to execute instructions and some values are generated, these values are used by DAC core to provide the final output signal named OUT  
- So we have 3 main elements (IP cores) and a wrapper as an SoC and of-course there would be also a testbench module out there  
- RVMYTH (Digital block), PLL & DAC(Analog blocks)  

$\textcolor{blue}{\text{RVMYTH}}$ - Risc-V based MYTH (Microprocessor for You in Thirty Hours)  
- RISC stands for Reduced instruction set computer  
- RISC-V(pronounced “risk-five”) ISA is defined as a base integer ISA, which must be present in any implementation, plus optional extensions to the base ISA  
- Each base integer instruction set is characterized by the width of the integer registers and the corresponding size of the address space and by the number of integer registers. There are two primary base integer variants, RV32I and RV64I  

Additional:  
- A program counter (PC) is a register in a computer processor that contains the address (location) of the instruction being executed at the current time. As each instruction gets fetched, the program counter increases its stored value by 1  
- An arithmetic logic unit (ALU) is a combinational digital circuit that performs arithmetic and bitwise operations on integer binary numbers  

To improve the performance of a CPU we have two options:   
(i) Improve the hardware by introducing faster circuits   
(ii) Arrange the hardware such that more than one operation can be performed at the same time   
Since there is a limit on the speed of hardware and the cost of faster circuits is quite high, we have to adopt the 2nd option   

$\textcolor{blue}{\text{Pipelined}}$  
- Pipelining is a process of arrangement of hardware elements of the CPU such that its overall performance is increased. Simultaneous execution of more than one instruction takes place in a pipelined processor  

->6 Cycle Pipeline Stages RISC processor has 6 stage instruction pipeline to execute all the instructions in the RISC instruction set   
Following are the stages of the RISC pipeline with their respective operations:  
Stage | Step | Detail |  
--- | --- | --- |   
1 | Program counter | A register in a computer processor that contains the address (location) of the instruction being executed at the current time |  
2 | Instruction Fetch | The CPU reads instructions from the address in the memory whose value is present in the program counter|  
3 | Instruction Decode | Instruction is decoded and the register file is accessed to get the values from the registers used in the instruction|  
4 | Memory Access | In this stage, memory operands are read and written from/to the memory that is present in the instruction|  
5 | Instruction Execute | ALU operations are performed |  
6 | Write Back | In this stage, computed/fetched value is written back to the register present in the instructions or internal memory |  

A $\textcolor{blue}{\text{phase-locked loop (PLL)}}$  is an electronic circuit with a voltage or voltage-driven oscillator that constantly adjusts to match the frequency of an input signal   PLLs are used to generate, stabilize, modulate, demodulate etc  
Why do we need a PLL for our SoC?  
Clock generated-Quartz crystal oscillator (off chip oscillator for 100Mhz and below)  

Why off-chip clocks can’t be used all the time?  
-The clock will be a supply for a lot of blocks on the chip, it will have delays due to long wires caused by RC (if used only one clock source) - also reasons like clock jitter  
-Some blocks/IP might need 200Mhzs and some might need 100Mhz (each point is different frequencies just on one small chip)  
-A concept of ppm(clock accuracy) comes in, whenever quartz is acquired, it comes with a x ppm error  
>What is this parts per million (ppm) error?   
>For example:  20ppm quartz used in watches, this translates as 20/1e6 (2e-5) which  gives an error over a day of 86400 * 2e-5 = 1.73 seconds delay per day, so in a month it loses 30 x1.72 = 51 seconds or 1 minute a month  
>So in terms of a chip, the mishap cause due to very small error for microseconds, but when the processor works at nanoseconds it can be a huge problem  
>So we need PLL used on SoC’s  

-Main components: Phase detector, Loop filter, Voltage controlled oscillator (change based on voltage), Frequency divider (make sure we can use multiple frequency from each IPs)  

![image](https://user-images.githubusercontent.com/118953915/210840409-fd848fdb-d540-4f56-9692-989ea9fe141f.png)  
 The main goal of a PLL is to synchronize the output oscillator signal with a reference signal  
->It will lock the phase (angle difference among 2 signals), then will decide the frequency and given to all the blocks on the chip   

$\textcolor{blue}{\text{Digital-to-Analog Converter}}$  
- A Digital to Analog Converter (DAC) converts a digital input signal into an analog output signal. 
- The digital signal is represented with a binary code, which is a combination of bits 0 and 1. 
DAC consists of a number of binary inputs and a single output.
- In general, the number of binary inputs of a DAC will be a power of two.

There are two types of DACs :
$\textcolor{blue}{\text{Weighted Resistor DAC}}$   
A weighted resistor DAC produces an analog output, which is almost equal to the digital (binary) input by using binary weighted resistors in the inverting adder circuit. In short, a binary weighted resistor DAC is called as weighted resistor DAC  
-> Disadvantage: Will have a lot register on ship, more power consumption causing temperature increase then silicon can’t operate properly  

$\textcolor{blue}{\text{R-2R Ladder DAC}}$   
The R-2R Ladder DAC overcomes the disadvantages of a binary weighted resistor DAC. As the name suggests, R-2R Ladder DAC produces an analog output, which is almost equal to the digital (binary) input by using a R-2R ladder network in the inverting adder circuit  
-> For VSDBabySoC will having 10-Bit DAC  
>Can refer here for calculation details: https://www.electronics-tutorials.ws/combination/r-2r-dac.html  

3. Basic introduction to Synopsys VCS  
- RVMYTH is a digital block, will use Verilog(HDL) for designing and checking functionality using a testbench  
- Verilog can’t synthesis analog design We are going to simulate it using verilog itself, we will be using data-types such real
- Goal is to be able to simulate “functionality” - to verify its logical correctness  
- Will use verilog to model and use VCS to simulate  
- VCS is a high-performance, high-capacity Verilog simulator that incorporates advanced, high-level abstraction verification technologies into a single open native platform  

4. Modelling and simulating on VCS involves 2 main steps, namely:  
(i) Compilation - VCS builds the instance hierarchy and generates a binary executable simv. This binary executable is later used for simulation  
(ii) Simulation - During compilation, VCS generates a binary executable, simv. We can use simv to run the simulation  
->There are 2 types mainly - Interactive mode and batch mode  

- For modelling and simulation interactive mode is preferred
- In interactive mode, we mean to say debug the design and so on. 
- One down side is - the compilation will not be “optimized” 

VCS has the following compile-time options for debug mode:   
mode | details |  
--- | --- |  
-debug_pp| Gives best performance with the ability to generate the VPD/VCD file for post-process debug. It is the recommended option for postprocess debug|  
-debug | Gives average performance and debug visibility/control i.e more visibility/control than –debug_pp and better performance than – debug_all |  
-debug_access+all | Enable all debug capability|  
-debug_all | Gives the most visibility/control and you can use this option typically for debugging with interactive simulation|  
-debug_region=()(+) | Have better control over the performance of -debug_access. This option enables you to apply debugging capabilities to the desired portion of a design (DUT, cell, testbench (TB), standard package (OVM, UVM, VMM, and RAL), or encrypted instances (modules, programs, packages, interfaces))|  
 
We will be debugging using tools like DVE: Discovery Visualization Environment  
>Can refer this manual: https://classes.engineering.wustl.edu/ese461/Tutorial/synopsys_vcs_tutorial.pdf  

Tips on modelling your design  
(i) Avoid race Conditions - can use VCS race detection tool  
(ii) Use an optimized Testbench for debugging your design  
(iii) Creating models that simulate faster  
(iv) Case statement behaviour ->Don’t use 3-to-1 mux need lots of power , can use case statement  

</details>

<details><summary> Lab Session-> BabySoC Modeling </summary>  
 
(A) For modelling RVMYTH(RISC-V):  
>git clone https://github.com/kunalg123/rvmyth/    
>cd rvmyth  
>vcs mythcore_test.v tb_mythcore_test.v  
>./simv  
>dve  -full64 &  <- must use -full64
>In order to open waveform:  
>Go to file/File/Open Database” and select the “.vcd” file from the project folder  
>Drag the required signal and select "Add to waves"    

>gvim mythcore_test.v tb_mythcore_test.v -o 
 
![image](https://user-images.githubusercontent.com/118953915/210846014-a8721ee6-1c50-4d22-aa1a-64ff64e43af8.png)    

Here is the run:  
![image](https://user-images.githubusercontent.com/118953915/210846157-9bd1d84f-4fb2-41f9-8d42-b75d239a9d2a.png)
  
Here is the waveform:
10-bit digital codes observed at the output of rvmyth   
![image](https://user-images.githubusercontent.com/118953915/210846231-02564977-6319-44a6-86bd-eff21c7cc696.png)   
 
(B) For modelling DAC(analog):      
> csh  
> vcs avsddac.v avsddac_tb_test.v -sverilog <- required -sverilog  
> ./simv  
> dve -full64 &  
>File copy from: https://github.com/vsdip/rvmyth_avsddac_interface/tree/main/iverilog/Pre-synthesis  

- In both of the .v file having data type: real  
![image](https://user-images.githubusercontent.com/118953915/210855614-15839cd1-ba53-49e5-9694-f852e8fa12f2.png)  
A real data type is a data type used in a computer program to represent an approximation of a real number. Because the real numbers are not countable, computers cannot represent them exactly using a finite amount of information. Most often, a computer will use a rational approximation to a real number.  
![image](https://user-images.githubusercontent.com/118953915/210846453-ae262ecb-de0b-46bd-9f3c-b6e85036c142.png)  
-Both file using for DAC is picking from pre_synthesis, both file is not synthesizable since consists mixture of analog   

must use -sverilog  
![image](https://user-images.githubusercontent.com/118953915/210846596-d143c8dd-a376-421c-b0f9-b07eaefe9b5f.png)

Here is the waveform:  
![image](https://user-images.githubusercontent.com/118953915/210846638-3eae8ab3-5bc6-4d39-99ec-08e75f31f982.png)
In another form:  
<img width="780" alt="image" src="https://user-images.githubusercontent.com/118953915/210847250-abc40467-52d4-410f-8fb2-3ececab117ca.png">

Validate result:  
<img width="394" alt="image" src="https://user-images.githubusercontent.com/118953915/211198023-2fa228c8-2311-4720-b107-11d84b820e87.png">
<img width="290" alt="image" src="https://user-images.githubusercontent.com/118953915/211197981-eeb1c31a-9dc5-4c88-b7ea-f19b88e3662f.png">  
>Hex to Binary Converter: https://www.rapidtables.com/convert/number/hex-to-binary.html  
>DAC Calculator: https://www.rfwireless-world.com/calculators/8-bit-and-10-bit-DAC-calculator.html  

(C) For modelling PLL (analog):   
![image](https://user-images.githubusercontent.com/118953915/210847374-86a83d33-4ba8-4c1f-87b8-62f6b03ec3e8.png) 
From reference github:   
![image](https://user-images.githubusercontent.com/118953915/210856650-80f9570a-7e0c-4a61-a8f3-ea11686fce4b.png)  
>Can refer this github for more deatils: https://github.com/vsdip/rvmyth_avsdpll_interface  

<img width="554" alt="image" src="https://user-images.githubusercontent.com/118953915/210857236-a39b70d2-7e5d-42a9-bc0b-8052a64b58de.png">  
 
Here is the waveform:  
![image](https://user-images.githubusercontent.com/118953915/210847407-48136ca5-5911-462a-b215-760d4d572fa4.png)  

(D) For DAC and RVMYTH:
-> Again required to remove “wire” infront of real  
![image](https://user-images.githubusercontent.com/118953915/210847617-2af19b57-1583-4347-83e5-d4f4097dffc1.png)
After modified:  
<img width="581" alt="image" src="https://user-images.githubusercontent.com/118953915/210858533-8c4e69a6-ff5f-4de0-81f2-297f65a816c1.png">  

Here is the run:  
![image](https://user-images.githubusercontent.com/118953915/210848237-cff3610e-b712-40c2-933e-3d32e6616642.png)  

Here is the waveform:  
->The clock signal will make the rvmyth (RISCV based processor) to execute instructions and some values are generated, these values are used by DAC core to provide the final output signal named OUT  
![image](https://user-images.githubusercontent.com/118953915/210849719-9b9e603f-fb55-4a29-83a5-b685bdf2eb1f.png)
In another form:  
![image](https://user-images.githubusercontent.com/118953915/210849760-6a067b68-4ffe-47c0-81ee-8bbfe61d8561.png)   

(E) For PLL and RVMYTH:  
<img width="786" alt="image" src="https://user-images.githubusercontent.com/118953915/211161562-49059e7a-7665-42b7-8f17-16fc4d945c83.png">

Here is the waveform:    
<img width="786" alt="image" src="https://user-images.githubusercontent.com/118953915/211161611-f8f29244-f2eb-4852-8eb1-948bbde00ec3.png">  

(F) For vsdbabysoc.v  
>Can use this command to trace which port not defined
>vcs vsdbabysoc.v testbench.v -sverilog +lint=TFIPC-L  
![image](https://user-images.githubusercontent.com/118953915/210848508-3b1e80bc-4cd0-4689-b815-f31c0fe687a1.png)

Here is both the .v:  
![image](https://user-images.githubusercontent.com/118953915/210860045-05fd6e4a-e565-4506-87dc-f9eb44afbe03.png)  

Here is the waveform:  
![image](https://user-images.githubusercontent.com/118953915/210860675-0fe20132-af5a-44e7-9a06-50a1f90a1920.png)  

 
✏️ Recap introduction from Day-11:  
VSDBabySoC contains one RVMYTH microprocessor, an 8x-PLL to generate a stable clock, and a 10-bit DAC to communicate with other analog devices  
Some initial input signals will be fed into BabySoC module that make the pll start generating the proper CLK for the circuit  
- The clock signal will make the rvmyth to execute instructions in its imem. As a result, the register r17 will be filled with some values cycle by cycle  
- These values are used by dac core to provide the final output signal named OUT  
- So, we have got 3 main elements (IP cores) and a wrapper as an SoC and a testbench module  

For debug in interactuve mode:   
> vcs -lca -debug_access+all -full64 mythcore_test.v tb_mythcore_test.v
> ./simv -gui &

![image](https://user-images.githubusercontent.com/118953915/210861208-ff26a42f-bb29-41be-b7c6-544612eebade.png)  

</details>

<details><summary> Lab Session-> Assignment: Simulation of basic circuit using VCS </summary>  

 
**Design Half Adder**  
-> The Half Adder is a type of combinational logic circuit that adds two of the 1-bit binary digits. It generates carry and sum of both the inputs.  
 
In order to dump out .vcd file, must add in these 2 lines in testbench file:  
![image](https://user-images.githubusercontent.com/118953915/210861666-647eaf7a-62b3-4231-aef6-70fd30e477aa.png)

Here is the details:  
<img width="800" alt="image" src="https://user-images.githubusercontent.com/118953915/210864005-705a79c1-e3b7-4534-a7c2-ee517e99400f.png">

Here is the run:  
<img width="375" alt="image" src="https://user-images.githubusercontent.com/118953915/210866640-5770f7ba-f195-4904-8b54-bc4ed5e3ddd7.png">  
 
Here is the waveform:  
<img width="424" alt="image" src="https://user-images.githubusercontent.com/118953915/210917368-4fb9c8c5-61c5-4d7a-8815-9ed2b0bbd872.png">


<Need further debug to extend the scale, currently only able to generate out 3 set of outputs>

</details>

#
# Day_13 
**⭐Post-synthesis simulation**

<details><summary> ⚡ Lecture Session: Post-synthesis simulation - Live session </summary>

### *__Lecture Session__*

✏️Recap on Pre-synthesis
-> Modelled and simulated the IP cores in VSDBabySoC (for checking its functionality, not checking timing…)

 
1. Here is synthesizable and non- synthesizable constructs in verilog:
 
Verilog Constructs | Used for | Synthesizable Construct |
---|---|---|
module|The code inside the module and the endmodule consists of the declarations and functionality of the design | Yes |
Instantiation| If the module is synthesizable then the instantiation is also synthesizable | Yes|
initial| Used in the test benches| No|
always| Procedural block with the reg type assignment on LHS side. The block is sensitive to the events| Yes|
assign| Continuous assignment with wire data type for modeling the combinational logic| Yes|
primitives| UDP's are non-synthesizable whereas other Verilog primitives are synthesizable | Yes|
force and release| These are used in test benches and non-synthesizable | No|
delays| Used in the test benches and synthesis tool ignores the delays | No|
fork and join| Used during simulation| No |
ports| Used to indicate the direction input, output and inout. The input is used at the top module | Yes|
parameter| Used to make the design more generic| Yes|
time| Not supported for the synthesis| No|  
 
 
2. Pre-synthesis vs post-synthesis  
- Pre-synthesis simulation is done according to the logic you have designed for and written -> $\textcolor{blue}{\text{only functionality}}$  
- Post synthesis simulation / ‘gate level simulation’ is done after synthesis considering each and every gate delays into account. reports the violations in $\textcolor{blue}{\text{both functionality and timing}}$    
- This also show’s the mismatches we are likely to get due to wrong usage of operators and inference of latches  
- Eg: using ‘X’(simulator terms/ synthesizer terms) - ‘Unknown’/“Don’t care”<- not a good practice  

                                                                               
3. Post-synthesis 
-> GLS(Gate Level Simulations)
- The term "gate level" refers to the netlist view of a circuit, usually produced by logic synthesis. 
- So while RTL simulation is pre-synthesis, GLS is post-synthesis. 
- The netlist view is a complete connection list consisting of gates and IP models with full functional and timing behavior. 
- RTL simulation is a zero delay environment and events generally occur on the active clock edge. GLS can be zero delay also, but is more often used in unit delay or full timing mode. 
- GLS is used to boost the confidence regarding implementation of a design and can help verify dynamic circuit behaviour, which cannot be verified accurately by static methods. It is a significant step in the verification process.

4. We will be using synopsys’s DC shell(Design Compiler) to synthesize the netlist  
-Design Compiler® RTL synthesis solution enables users to meet today's design challenges with concurrent $\textcolor{orange}{\text{optimization of timing, area, power and test}}$  
 
</details>

<details><summary> Lab Session-> Synthesize using DC </summary>    

**1. Convert .lib-> .db**  
Tools only able to read in .db files, use this tool: synopsys’s lc_shell (Library Compiler) to convert .lib to .db  
-> Purpose of .lib (liberty) - provide timing of whole design

(i) Convert avsddac.lib:      
> Invoke lc_shell:  lc_shell  
> Read library: read_lib avsddac.lib   
>Write into .db format: write_lib avsddac -f db -o avsddac.db    
>If the program is successfully reading your commend, it will returns 1  
  
 ![image](https://user-images.githubusercontent.com/118953915/211348132-45be070a-034c-4535-8c46-4632a657986b.png)  

(ii) Convert avsdpll.lib:  
> lc_shell  
> read_lib avsdpll.lib  
> write_lib avsdpll -format db -output avsdpll.db  

<img width="1000" alt="image" src="https://user-images.githubusercontent.com/118953915/211352416-aa93a065-81a9-4763-ab2e-72c28da283d6.png">


> All libs and verilog codes taken from several training github: https://github.com/manili/VSDBabySoC/tree/main/src/lib   
> git clone https://github.com/vsdip/rvmyth_avsddac_interface.git  

(iii) After done convert:
> gvim ~/.synopsys_dc.setup

![image](https://user-images.githubusercontent.com/118953915/211348284-5e7689b0-5414-4d93-aba1-4766de091d4b.png)  

 Exit and reenter dc_shell to double comfirm:    
![image](https://user-images.githubusercontent.com/118953915/211348441-4713500e-ec6b-475d-bed8-853150d0b0ea.png)  
<img width="600" alt="image" src="https://user-images.githubusercontent.com/118953915/211351474-b25346b5-1cc9-490b-a55d-e518c67fd06d.png">


 #
 
**2. Pre-synthsis:**  

(A) For rvmyth_avsddac.v (Combination of mythcore_test.v, avsddac.v and etc):     
Here is the content on part of the .v:
![image](https://user-images.githubusercontent.com/118953915/211384188-21b506e3-46b1-4208-a3a7-b5ad932b30f7.png)
Error during read in $itor, need to remove since dc synthesis only read in digital value, same for "real" also need to remove 

> read_verilog mod_rvmyth_avsddac.v <- default command  
 
If using above command, the clk_gate will become top module                                   
![image](https://user-images.githubusercontent.com/118953915/211384718-b220ec0b-045f-4184-b2fc-9975784ab42a.png)

So we need to use following command:  
>read_file {mod_rvmyth_avsddac.v mod_avsddac.v mod_mythcore_test.v clk_gate.v} -autoread -format verilog -top rvmyth_avsddac <- must mentioned top  

-The read_file command has more options than the read_verilog command    
-The -autoread option is required for the files to be compiled in the correct order. In addition, the top module of the design is specified  
                                                                                                                               
                                                                                                                                
Must make sure there is no error  
![image](https://user-images.githubusercontent.com/118953915/211384785-cef84fdf-cc1b-4355-86a3-5a3c8ac2f2ab.png)

Check current_design:     
![image](https://user-images.githubusercontent.com/118953915/211384819-a21dde47-b377-4ed3-9a34-960464fc6ad9.png)

> Linking to the library:  link   
 
![image](https://user-images.githubusercontent.com/118953915/211384845-58d0fdbc-c3db-4f70-9041-967f476220ab.png)

 > Let the tool to compile the design: compile 
 
![image](https://user-images.githubusercontent.com/118953915/211384883-10839ec7-5c2d-4849-9b6c-383a65e8dc6c.png)

 Done compile:  
![image](https://user-images.githubusercontent.com/118953915/211384948-6e79c524-cf96-4ec1-8d81-2974a41dda92.png)

**Checking design** -- before constraints  
 <img width="900" alt="image" src="https://user-images.githubusercontent.com/118953915/211385551-f757dc4b-c3bd-4438-888b-5892a4c31aee.png">

**Need to apply constraints to resolve above violations** - will constraints later on in vsdbabysoc.v  
 
> Write out netlist: write -f verilog -out  mod_rvmyth_avsddac_net1.v  
 
![image](https://user-images.githubusercontent.com/118953915/211385615-5176c31d-865f-478c-a003-ab7101a09ebb.png)  

 #
 
 (B) For rvmyth_pll.v (Combination of mythcore_test.v, avsd_pll_1v8.v and etc)  
Here is the content on part of the .v:  
![image](https://user-images.githubusercontent.com/118953915/211385664-0b9231ab-7b21-4369-9430-5753152c63e7.png)  
There is error on $realtime, need to change to $time  
->If time scale is 10ns, $realtime returns 1.6 and $time has to return an integer, so that gets rounded up to 2  
>Can refer here for more information on real_time vs time: https://verificationacademy.com/forums/systemverilog/time-vs-realtime  

After modified can proceed read_verilog:  
>read_file {mod_avsd_pll_1v8.v mod_mythcore_test.v clk_gate.v mod_rvmyth_pll.v } -autoread -format verilog -top rvmyth_pll_interface  
![image](https://user-images.githubusercontent.com/118953915/211385806-3fb1d410-f143-44f3-b7ce-04630de38e68.png)
 
Checking current_design:   
![image](https://user-images.githubusercontent.com/118953915/211385837-2a253350-b464-4478-816c-64ddfa6cc2cb.png)

**Need to apply constraints to resolve above violations** - will constraints later on in vsdbabysoc.v  

> Write out netlist: write -f verilog -out  mod_rvmyth_pll__net.v -hierarchy  
![image](https://user-images.githubusercontent.com/118953915/211385978-1b6cf095-fac7-429c-bdba-2cbeed7085a6.png)  


 #
 
(C) $\textcolor{purple}{\text{For vsdbabysoc.v}}$ (Combination of mythcore_test.v, avsd_pll_1v8.v, avsddac.v and etc)  

Here is part of the detials in .v:  

![image](https://user-images.githubusercontent.com/118953915/211386078-6bd41f18-6937-4914-accb-709c8963b793.png)

> read_file { mod_mythcore_test.v mod_avsd_pll_1v8.v mod_avsddac.v clk_gate.v  mod_vsdbabysoc.v} -autoread -format verilog -top vsdbabysoc  
 
![image](https://user-images.githubusercontent.com/118953915/211386130-a8eb78d9-634a-4a4a-acbd-8049b60ea452.png)
 
> link  
> compile  
 
![image](https://user-images.githubusercontent.com/118953915/211386168-f3531b8a-16fb-4b91-aa8c-c24009ff75de.png)

**Checking design** -- Before constraints  
<img width="1000" alt="image" src="https://user-images.githubusercontent.com/118953915/211816144-5cf3c40b-2a49-4f0d-bf4e-1ea1320cc685.png">

🛠️ Need to apply constraints for tool to read in  

**Checking design** -- After apply constraints and compile_ultra  
<img width="1000" alt="image" src="https://user-images.githubusercontent.com/118953915/211816455-7526f594-722f-4fad-944f-b8c0722a5f1d.png">
 
Here is the details on constraints:  
<img width="1000" alt="image" src="https://user-images.githubusercontent.com/118953915/211826450-e73e0241-e132-4ec0-9dee-636e18c8fb58.png">

Save netlist: 
> write -f verilog -out mod_vsdbabysoc_net.v -hierarchy <- need to include in hierarchy

<img width="600" alt="image" src="https://user-images.githubusercontent.com/118953915/211854971-4e000827-5967-401b-a3f4-4ef207b63af0.png">
<img width="600" alt="image" src="https://user-images.githubusercontent.com/118953915/211857045-c4ea55f2-7ed0-4767-ac9e-804aafbf30f2.png">

</details>

 
#
# Day_14 
**⭐Synopsys DC and timing analysis**

<details><summary> ⚡ Lecture Session: Synopsys DC and timing analysis - Live session </summary>

### *__Lecture Session__*

$\textcolor{blue}{\text{PVT}}$ (Process, Voltage and Temperature)  
- Integrated circuits are designed in such a way that they can function in a wide variety of temperatures and voltages, rather than a single temperature and voltage   
- In order to make our chip to work after fabrication in all the possible conditions, we simulate it at different corners of process, voltage and temperature  
- These conditions are called corners. All these three parameters directly affect the delay of the cell  

Details on PVT:  
- Process: There are millions of transistors on the single-chipas we are going to lower nodes and all the transistors in a chipcannot havethesame properties. Process variation is the deviation inparametersofthe transistor during the fabrication. (Eg of factors: UV lights, manufacturing defect)
- Voltage: As we are going to the lower nodes the supply voltage for a chip is also going to less. Let’s say the chip is operating at 1.2V. So, there are chances that at certain instances of time this voltage may vary. (Eg of factors: IR drop caused by the current flow over power grid network, suuply noise caused by parasitic inductance in combination with resistance and capacitance)
- Temperature: When a chip is operating, the temperature can vary throughout the chip. This is due to the power dissipation in the MOS-transistors. (Eg of factors: transistor density & switching)

PVT Graphs  
![image](https://user-images.githubusercontent.com/118953915/211713906-9b607536-3fdf-4bc9-b529-f6f9cfc2f3cd.png)  
💡  Best case scenario (quick process): High voltage & low temperature  
      Worst case scenario (slow process):  Low voltage & high temperature  

>Can refer this link for more detail: https://www.physicaldesign4u.com/2020/07/pvt-process-voltage-temperature.html  

</details>

<details><summary> Lab Session-> PVT coners </summary>

📝 Details:   

Terms| Full name | Details|   
---|---|---|  
WNS | Worst Negative Slack | Difference between the clock period and the delay between a pair of registers. A positive worst case setup time slack means the constraint is met and a negative slack means that the longest path has a path delay longer than the clock period of the circuit.|   
TNS | Total Negative Slack = Sum of the negative slack paths  | Sum of the (real) negative slack in your design. If 0, then the design meets timing. If it is a positive number, then it means that there is negative slack in the design (hence your design fails). It cannot be negative.|  
WHS | Worst Hold Slack  | Worst hold slack in the design. Like WNS if positive, it means the path passes, if negative it fails. |  
THS | Total Hold Slack = Sum of the negative hold slack path  | Sum of the (real) negative hold slack. If zero, your design passes, if positive, your design fails. |  

 
1. Converting .lib into .db for tool to pick up:  
> read_lib ; write_lib  
 
Facing some error during read_lib, need to temporary remove those lines  
<img width="621" alt="image" src="https://user-images.githubusercontent.com/118953915/211892499-2f3455d7-c6c6-49f9-a83b-43706587f08c.png">

2. After done converting into .db, required to set them separately in target_library and link_library
> Eg: sky130_fd_sc_hd__ff_100C_1v65.db
set target_library { /nfs/site/disks/png_mip_gen6p9ddr_0042/chiannio/trainning/rvmyth/day14/timing_libs/sky130_fd_sc_hd__ff_100C_1v65.db /nfs/site/disks/png_mip_gen6p9ddr_0042/chiannio/trainning/rvmyth/day14/timing_libs/avsdpll.db /nfs/site/disks/png_mip_gen6p9ddr_0042/chiannio/trainning/rvmyth/day14/timing_libs/avsddac.db }  
set link_library { * /nfs/site/disks/png_mip_gen6p9ddr_0042/chiannio/trainning/rvmyth/day14/timing_libs/sky130_fd_sc_hd__ff_100C_1v65.db /nfs/site/disks/png_mip_gen6p9ddr_0042/chiannio/trainning/rvmyth/day14/timing_libs/avsdpll.db /nfs/site/disks/png_mip_gen6p9ddr_0042/chiannio/trainning/rvmyth/day14/timing_libs/avsddac.db }  

3. After that, start read in design and link with the library
> read_verilog ; link ; source in constraints 
 
Here is the results:  
> Command: report_qor  
 
Different PVT corners WNS, WHS, TNS & THS values:    
<img width="900" alt="image" src="https://user-images.githubusercontent.com/118953915/211889414-dba22892-0238-4ea5-912c-b9c02128842e.png">  
<img width="900" alt="image" src="https://user-images.githubusercontent.com/118953915/211890175-d4d49255-004f-4786-be3b-9ca3ff15e7c7.png">  

 🕵️ The best PVT -> ff, 100C, 1v95  
 
<img width="900" alt="image" src="https://user-images.githubusercontent.com/118953915/211901269-c404f3bf-954f-49f7-a350-4e6cbeea7d5d.png">


 </details> 
