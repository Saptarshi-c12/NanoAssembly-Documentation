---
<script src="https://cdn.rawgit.com/knsv/mermaid/6.0.0/dist/mermaid.min.js"></script>
<link href="https://cdn.rawgit.com/knsv/mermaid/6.0.0/dist/mermaid.css" rel="stylesheet" />
---
# Visual Flowchart 

This is the visual representation of the entire Staple Assembly process 

## Traditional Staple Operation

```mermaid
 graph TD


            a1[Close Valve]
            a1-1[Turn on Rough Pumping]
            a1-2[Pressure is less than 1e-1 mbar]
            a1-3[Stop Roughing: Connect to the Pump]
            %% a2[Start Pump <br> CC:❌ M:✅]

            a3[Coarse Alighment using Stepper Motor <br> CC:✅ M:✅]
            a4[Move Microscope to the top of the sample <br> CC:✅ M:❌]
            a5[Focus on the Chip with Maximum Magnification <br> CC:✅ M:✅]
            a6[Align the Microscope on the Chip <br> CC:✅ M:✅]
            a7[Focus on the CAD <br> CC:✅ M:✅]
            a8[Aligh the CAD Roughly <br> CC:✅ M:✅]
            a9[Move the Microscoper to 200 microns above the chip <br> CC:✅ M:✅]
            a10[lower the cad until they will reach 200 microns above the chip and in the focus of the microscope <br>
            CC:✅ M:✅]
            a11[Start the Stapling <br> CC:✅ M:✅]
            a12[TouchDown <br> CC:✅ M:❌]
            a13[Chip Health <br> CC:✅ M:❌]
            a14[Cut the Source Side <br> CC:✅ M:✅]
            a15[Cut the Drain Side <br> CC:✅ M:✅]
            a16[I-V Curve of Source- Drain <br> CC:✅ M:❌]
            a17[Gate Dependense <br> CC:✅ M:❌]
            a18[Remove the CAD <br> CC:✅ M:✅]

            subgraph Valve
            a1
            a1-1
            a1-2
            a1-3
            end
            class Valve sand

            subgraph Stepper-Motor
            a3
            end
            class Stepper-Motor lavender

            subgraph ZABER-Motor
            a4
            a6
            end
            class ZABER-Motor mint

            subgraph PiezoMotor
            a8
            a10
            end
            class PiezoMotor ocean


            subgraph Microscope
            a5
            a7
            a9
            end
            class Microscope rose


            subgraph Piezo/SMU1
            a11
            a12
            end
            class Piezo/SMU1 blush

            subgraph SMU1
            a13
            a14
            a15
            a16
            end
            class SMU1 denim


            subgraph SMU2
            a18
            end
            class SMU2 sand

            a1

            a1-3
            --> a3
            --> a4
            --> t2{Is this Operation Sussesful?}
            t2 --> |Yes| a5
            t2 --> |No| a4
            a5
            --> a6
            --> a7
            --> a8
            --> a9
            --> a10
            --> a11
            --> a12
            --> a13
            --> a14
            --> a15
            --> a16
            --> a17
            --> a18

            %% For SubGraph Coloring and Category %%
            
```
## Pick And Place Operation





```mermaid
graph TD
    a1[Close Value]
    a2[Turn on Rough Pumping]
    a3[Pressure is less than 1e-1 mbar]
    a4[Stop Roughing:Connect to the Pump]

    subgraph vc["Valves/Control"]
    a1
    a2
    a3
    a4
    end

subgraph m1["Microscope+Swan Calibaration (Colinarity) "]
        A1[Microscope Focus Z]
        -->A2[Microscope X/Y Adjustment]
        -->A3[Save Calibaration Points]
        -->A4[Generic Matrix]
        A3 --> A1
    end
    

subgraph m2["Microscope+Chip Calibaration (Colinarity)"]
      B1[Microscope Focus Z]
        -->B2[Microscope X/Y Adjustment]
        -->B3[Save Calibaration Points]
        -->B4[Generic Matrix]
        B3 --> B1 
    end
    

subgraph m3["Microscope + Growth Calibaration (Colinarity)"]
    c1[Microscope Focus Z]
        -->c2[Microscope X/Y Adjustment]
        -->c3[Save Calibaration Points]
        -->c4[Generic Matrix]
        c3 --> c1 
    end



subgraph pick["Pick Operation"]
p5[Cleaning]
p1[Course Alignment]
p2["Just Pick Tubes (Current vs Coordinates)"]
p3["Anneling (Current, Microscope vs Volatge)"]
p4{If there is a Tube?}


end



subgraph placing["Placing Operation"]

p1-1[Course Alignment for Assembly]
p1-2[Chip Health]
p1-3{"Any Signal from the Nanotube (Any Shorts)"}
p1-4["Nano-Assembly (Current vs Position)"]
p1-5{"TouchDown ?"}
p1-6["I-V Sweep (Anneling)"]
click p1-6 "http://www.github.com" "This is a link"
p1-7{"If Detected ?"}
p1-8["Chip Health (Refined)"]





end



subgraph loop["Loop for 2-3 times"]

l1[Cut the NanoTube]
l2[Chip Health]
l1-->l2
l2-->l1
end


vc 
--> vc1[Motor Calibaration]
vc .-> s1>"**Give the Information to the Software or uploading the position of the NanoTubes and Devices**
<br> - Upload Chip Board Map </br> <br> - Upload Device Map </br> <br> - Tube Map </br>"]

s1 .-> vc1
-->

m1 --> m2 --> m3

--> pick

%% Picking
p5--> p1-->p2
-->p3
-->p4
--> |No| p5
%%p5 --> p1
p4 --> placing

%%PLACING
p1-1-->p1-2
--> p1-3
--> | Yes| pick
p1-3 --> |No| p1-4
p1-4 --> p1-5
--> |No| p1-6
--> p1-7
--> |No| pick
p1-5 -->|Yes| p1-8
p1-7 --> |Yes| p1-8

p1-8-->
collapse{"Collased ?"}-->|No| doiv["Do I-V"]
-->
doiv2{Is the I-V OK ?}
--> |No| pimotor["Few Steps Down with the Piezo Motors"]

collapse -->|Yes| cp["Current vs Position"]
cp --> p1-1
pimotor --> p1-8

doiv2 -->|Yes| loop

loop --> char["Chracterisation"]
char --> pick

%% Comments
p4 ~~~|"💡 :<br> If the Tube Exists it will Glow and can be checked through the Microscope's Camera"| pick

loop ~~~~~ |"💾 <br> <br> <br> <p style="text-align: right;"> This value is saved in .jlog file & Pushed (saved) into database"| l2

pick ~~~ |" 📈: <br>  The Anneling in this Stage is handled by the Fingers of the FORK"| pick

placing ~~~ |"📉: <br> Anneling at this Stage is handled by the Source (S) and Drain (D) Terminals through the use of SMU "| placing

%% For SubGraph Coloring and Category %%
classDef ocean fill:#e0f7fa,stroke:#006064,color:#004d40;
classDef sunset fill:#ffe0b2,stroke:#ff9800,color:#e65100;
classDef lavender fill:#ede7f6,stroke:#512da8,color:#311b92;
classDef mint fill:#e8f5e9,stroke:#388e3c,color:#1b5e20;
classDef rose fill:#ffebee,stroke:#c62828,color:#ad1457;
classDef sand fill:#fff8e1,stroke:#ffb300,color:#6d4c41;
classDef slate fill:#eceff1,stroke:#607d8b,color:#263238;
classDef plum fill:#f3e5f5,stroke:#8e24aa,color:#4a148c;
classDef forest fill:#e8f0e3,stroke:#388e3c,color:#1b5e20;
classDef coral fill:#ffdde0,stroke:#ff5252,color:#c62828;
classDef sky fill:#e3f2fd,stroke:#1976d2,color:#0d47a1;
classDef gold fill:#fff9e1,stroke:#ffd600,color:#bfa000;
classDef steel fill:#e3eaf2,stroke:#607d8b,color:#263238;
classDef blush fill:#fce4ec,stroke:#d81b60,color:#880e4f;
classDef denim fill:#e3eafc,stroke:#1565c0,color:#283593;
classDef lime fill:#f9fbe7,stroke:#cddc39,color:#827717;
classDef cocoa fill:#efebe9,stroke:#6d4c41,color:#3e2723;

```