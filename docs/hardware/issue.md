# Hardware Constrainsts 

This is the list of the operations on or with the Hardware where the user (during manual control) and the Software (During Automation process) need to take into account to protect the system from any accidental damages.

| Task | Critical Operation | Cannot Run Parallel with (Hard) | Hardware |
| -- | -- | -- | -- |
| Zoom/ AutoFocus | If The Microscope is moving in Z axis | The Microscope cannot Go in X-Y Axis | Microscope |
|     | If the Microscope is moving in X-Y Axis | The Microscope cannot go in Z direction |     |
| SWAN Movement | To Move, First move the Attocube in the X-Y and then the Z position |     | AttoCube Motors |
|     | To Move-back, First move to the Z axis and then the X-Y axis |     |     |
|     | For ARUN motors, First move in the Z axis and then the X-Y axis |     | ARUN Motors |
|     | To Move-back, First move to the X-Y axis and then move to the Z axis |     |     |
| SMU Operations | Changes in Compliance Current/Voltage by different GUIs (eg. One can change Complicance current from both "Matrix Connections" and "ForkLift Control") | The "Matrix Connection" should have the highest priority.<br><br>Either way, The Compliance value reflected should be same in every GUI (The most recent changes should get updated everywhere) | SMU |
|     | SMU instrument's Channel Busy | No other application can use the Channel until its Busy. | The K2400 supports only one channel at a time. If the application reads from many sensors its best to treat each serial port independently. |
|     |     |     |     |


