Download Link: https://assignmentchef.com/product/solved-mips-hw5-pipeline-cpu-i
<br>
In this lab, please modify the single cycle processor designed in lab4 to a pipelined processor. And you <strong>don’t</strong> have to consider the hazard issue.

<h1>2.       Demands</h1>

<ol>

 <li>Please use <strong>iverilog</strong> as your HDL simulator.</li>

 <li>Submit all *.v source files and report(pdf) on new e3.</li>

</ol>

The type of compressed file must be “zip” (Ex. Lab5_0816000.zip)

Other form of file will get -10%.

<ol>

 <li>Reg_file(negative-edge triggered), Program_Counter, and TestBench are supplied.</li>

</ol>

Please use these modules and modules in Lab 3 to accomplish the design of your CPU.

<strong>Remember to change the “`include” region in “TestBench.v”</strong>

<ol>

 <li>For each pipeline register, it should contain the fields for <strong>data</strong> and <strong>control signals</strong>.</li>

 <li>Instruction set: we will test part of the instructions which have been implemented in previous lab : add, sub, and, or, nor, slt, sll, srl, addi, lw, sw, beq, bne.</li>

</ol>

We will <strong>NOT</strong> test “jump”, “jal”, and “jr” instruction.

You may remove the circuits for jump, jr and jal in your design.




<strong>        </strong>

<h1>3.       Pipelined CPU</h1>

<ol>

 <li><strong>Architecture diagram </strong></li>

</ol>




According to the above diagram, in this lab you should implement a five stage pipelined processor with IF, ID, EX, MEM, and WB stages.

You should insert a pipeline register between each two stages.

Each pipeline register should contain the fields for <strong>data</strong> and <strong>control signals</strong>. The pipeline registers are written when the positive clock edge occurs.

<strong>             </strong>

<ol>

 <li><strong>The description of pipeline stage </strong>The function of each stage is described as follows:</li>

</ol>

<ul>

 <li><strong>IF stage:</strong></li>

</ul>

In this stage, the processor fetches an instruction from the instruction memory and performs PC + 4.




<ul>

 <li><strong>ID stage:</strong></li>

</ul>

In this stage, the processor decodes the instruction to generate the control signals, reads two source registers, and generates the sign extended immediate value.




<ul>

 <li><strong>EX stage: </strong></li>

</ul>

In this stage, ALU_Ctrl generates control signals for function units according to ALUOp. At the same time, Register Write ID and branch target are also determined in this stage.




<ul>

 <li><strong>MEM stage:</strong></li>

</ul>

In this stage, the processor accesses data memory according to the control signals. The modification of PC from branch taken instruction is also performed in this stage.




<ul>

 <li><strong>WB stage:</strong></li>

</ul>

In this stage, the processor will write the value into register file according to the control signal when negative clock edge occurs.




<ol>

 <li><strong>Description of pipeline register</strong></li>

</ol>

Please design four pipeline registers. Each pipeline register must be “positiveedge triggered”, has default value 0.

Then, insert these pipeline registers into your single-cycle CPU designed in Lab4 to accomplish the pipelined CPU required in this lab.




<strong>DO NOT</strong> set any delay time for the sequential circuits of the pipelined registers designed by you.




<strong>           </strong>

<h1>4.       Test</h1>

Modify line 43 of TestBench.v to read different test data.

There are 2 test files, CO_P5_test_data1.txt and CO_P5_test_data2.txt. Corresponding instructions and output answer are in data1_result.txt and data2_result.txt