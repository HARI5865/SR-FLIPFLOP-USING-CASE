# SR-FLIPFLOP-USING-CASE

**AIM:**

To implement  SR flipflop using verilog and validating their functionality using their functional tables

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

SR Flip-Flop SR flip-flop operates with only positive clock transitions or negative clock transitions. Whereas, SR latch operates with enable signal. The circuit diagram of SR flip-flop is shown in the following figure.

![image](https://github.com/naavaneetha/SR-FLIPFLOP-USING-CASE/assets/154305477/0f710028-ad52-4d3e-9276-8714cf023a25)

 
This circuit has two inputs S & R and two outputs Qtt & Qtt’. The operation of SR flipflop is similar to SR Latch. But, this flip-flop affects the outputs only when positive transition of the clock signal is applied instead of active enable. The following table shows the state table of SR flip-flop.

![image](https://github.com/naavaneetha/SR-FLIPFLOP-USING-CASE/assets/154305477/dabfc4f4-87e3-4cbc-9472-f89ee1b5ed30)

 
Here, Qtt & Qt+1t+1 are present state & next state respectively. So, SR flip-flop can be used for one of these three functions such as Hold, Reset & Set based on the input conditions, when positive transition of clock signal is applied. The following table shows the characteristic table of SR flip-flop. Present Inputs Present State Next State

![image](https://github.com/naavaneetha/SR-FLIPFLOP-USING-CASE/assets/154305477/dd90d16c-aec5-4290-a586-e2346b1e9eb5)

 
By using three variable K-Map, we can get the simplified expression for next state, Qt+1t+1. The three variable K-Map for next state, Qt+1t+1 is shown in the following figure.

![image](https://github.com/naavaneetha/SR-FLIPFLOP-USING-CASE/assets/154305477/473efad6-d70b-4ca7-aeb7-898bbfca319f)

 
The maximum possible groupings of adjacent ones are already shown in the figure. Therefore, the simplified expression for next state Qt+1t+1 is Q(t+1)=S+R′Q(t)Q(t+1)=S+R′Q(t)

**Procedure**

/* write all the steps invloved */

**PROGRAM**<br>
always @(posedge clk) begin<br>
    case ({S, R})<br>
        2'b00: begin<br>
            Q <= Q;<br>
            Qn <= Qn;<br>
        end<br>
        2'b01: begin<br>
            Q <= 0;<br>
            Qn <= 1;<br>
        end<br>
        2'b10: begin<br>
            Q <= 1;<br>
            Qn <= 0;<br>
        end<br>
        2'b11: begin<br>
            Q <= 1'bx;<br>
            Qn <= 1'bx;<br>
        end<br>
    endcase<br>
end<br>
endmodule<br>

module SR_FlipFlop_tb; reg S; reg R; reg clk; wire Q; wire Qn;<br>

SR_FlipFlop uut (<br>
    .S(S),<br>
    .R(R),<br>
    .clk(clk),<br>
    .Q(Q),<br>
    .Qn(Qn)<br>
);<br>

initial begin<br>
    clk = 0;<br>
    forever #5 clk = ~clk;<br>
end<br>

initial begin<br>
    $monitor("Time=%0t | S=%b, R=%b, Q=%b, Qn=%b", $time, S, R, Q, Qn);<br>

    S = 0; R = 0; #10;
    S = 0; R = 1; #10;
    S = 1; R = 0; #10;
    S = 1; R = 1; #10;

    $finish;
end<br>
endmodule<br>

/* Program for flipflops and verify its truth table in quartus using Verilog programming. Developed by:HARIHARASUDHAN N RegisterNumber:24900208
*/

**RTL LOGIC FOR FLIPFLOPS**<br>
![391840737-e057c28a-bdb2-4b87-aa73-041198aa45ea](https://github.com/user-attachments/assets/a81b18ca-7254-4426-b755-b9e363c8ac28)


**TIMING DIGRAMS FOR FLIP FLOPS**<br>
![391840647-057b2d99-5dda-4a94-b479-d9d856dc24dc](https://github.com/user-attachments/assets/2de88158-1f18-4817-be5b-5c2ea28b3aaa)


**RESULTS**<br>
Encoder implemented successfully SR-FLIPFLOP-USING-CASE verified.
