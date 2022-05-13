# Final Project 
This is the official manual for your final project.  
Please follow the guidelines below.   
Keep your eyes on updates as there may be some changes in specification / scoring policy in future.

---
## Updates 
- No updates yet

---

## Due date
Due for Baseline : 8th June  
Due for Opimizations : 11st June  
We will not accept any delayed submission.

---

## Optimizing your work
We suggest three different ways to optimize your work: **Quantization**, **Zero-Skipping**, and **DMA**(Direct Memory Access).  
Relevant materials will be uploaded on eTL soon. 


|              | Videos |  Files  |
|--------------|--------|---------|
| Baseline     |        |         |
| Quantization |        |         |
| Zero-skpping |        |         |
| DMA          |        |         |


---
## 1. Prepare your bitstream file
You need a bitstream file that you have generated with the block design that includes your IP.  
You just have to replace the custom IP of the block design in lab10 with your MM(Matrix-Matrix) PE controller.  
How the PE controller should be designed is explained [here.](preview)  


## 2. Boot your device with the bitstream file
Once you are prepared with the bistream file, rename it to "zynq.bit", and move it to the sdcard.  
Insert the sdcard to the device and boot it.  
How you can boot your device via minicom is explained [here.](week8)

  
## 3. (Optional) Download the repository 
※ This is optional since the source files are totally same as in lab09, except benchmark.sh.  
You can therefore skip 3~6 and extend your work on lab09.  
  
You need to download this repository to start your final project.  
```
$ git clone https://github.com/resurgo97/hsd22_project  
```
Note that this command can be run on the terminal on your device if connected to the network.  

## 4. (Optional) Check dependencies 
Check if all the dependencies for running the codes have been installed.
```
$ sudo apt-get update -y
$ sudo apt-get install -y libprotobuf-dev protobuf-compiler python python-numpy
```
These would have already been installed on your device if you have successfully done your lab09.

## 5. (Optional) Download the dataset 
Run the command below to download the dataset.
```
$ bash download.sh
```

## 6. (Optional) Modify the codes
You will see three functions (LargeMV & LargeMM & ConvLowering) that have not been implemented in the fpga_api.cpp & fpga_api_cpu.cpp.  
Complete the codes for those functions as you did it in the lab09.  
Modify fpga_api.cpp & fpga_api_cpu.cpp based on your previous works.  

## 7. Run it
Run the validation code as below.
```
sh benchmark.sh
```
Hopefully you will get 100% accuracy on the classfication task!

---
## Specifications
1. Accuracy on the classification task with CNN should be 100%.   
  (Acceptable amount of degradation by quantization or zero-skipping will be allowed.)
2. The PE controller should consist of (at most) 8x8 (=64) PEs.
3. The FSM should consist of 5 states: **IDLE** - **LOAD** - **CALC** - **HARV** - **DONE**  
4. During HARV(harvest) state, the PE controller should write back the computed data to BRAM.  
You are not bound to this approach for optimizing baseline. That means, you can also exploit pipelining.
5. Latency of your floating point MAC must be set as 16 cycles.

---
## Scoring Policy
Well explained in the videos.

1. Baseline 70% + Optimizations 30% (10% for each)
  - For each, Implementation 70% + Performance 30%

2. Implementation 
  - If you fail to implement or lose accuracy due to logical error in your code, you may not get the whole points.
  - We accept small amount of accuracy loss by zero-skipping or quantization.

3. Performance 
  - **Total computation time spent by HW** for baseline, quantization, zero-skipping
  - **Total data transfer time** for DMA
  - You will be given some code snippets to estimate computation latency of your work
  
4. Report 


---
**Please use the Q&A board on eTL if you have questions or want more information about the project.**
