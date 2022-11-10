# COMP3331_9331_22T3
For M14B and F12A students


## Useful links:
 - [Course home page](https://webcms3.cse.unsw.edu.au/COMP3331/22T3/)
 - [Lab timetable and recordings](https://webcms3.cse.unsw.edu.au/COMP3331/22T3/resources/80663)
 - Forumn: https://edstem.org/au/courses/10008/ 
 - Monday 14:00 (M14B) lab link:  https://unsw.zoom.us/my/ruitut   
 - Friday 17:00 (F12A) lab link:  https://unsw.zoom.us/my/ruitut   
 - [MyRecordings](https://www.youtube.com/playlist?list=PL62Uy8LvT4FZjh1fCz9oeLAr9wmlfZJKD)  
 



## Assignment demo 
  I will have assignment demo session for python.  
  - Time:  
    - **week 5,7~9**: **Thursday and Friday 14:00~16:00** 
  - Link: https://unsw.zoom.us/my/ruitut   
  - Schedule:
    - W5: week assignment overview: How to start from 0. basic code demo.
      - What is the task?
      - Demo code for:
        - single login
        - block
        - multiple user login at the sametime
      - Recording link:  https://youtu.be/x3NzLFs61w4 
    - W7: assignment structure design 
      - app design / protocol design
      - data structure
      - basic python operations
        - how to create/delete/modify txt file
        - how to send/receive json object between server/clients
        - Demo code for:
          - EDG
          - UED
          - DTE
          - AED
        - Recording link: https://youtu.be/kPAz8w62wTI  
    - W8: assignment P2P key functions demo and discussion
        - program stucture for P2P (UDP) part
        - demo code for how to send file via UDP
        - recording: https://youtu.be/KZYclM8JHE8  

    - W9: How to do submission and testcase 
        - report content
        	- 1. how to run the script
        	- 2. what is your application protocol and data structre?
        	- 3. any bug or trade-off you made for your program? (for example, you have significant delay on UDP file transmission to make sure the reliable file transfer)
        	- ps: 1~2 pages is enough, make it simple and clear.
        - new credentials.txt and testcase
        - submission checklist

## Assignment Test Instructions
Note: Please try to run your application with the follwing commands, and check if you have expected output. This is not an official testcase, just for reference, please always follow the instructions of **[Assignment SPEC](https://webcms3.cse.unsw.edu.au/static/uploads/course/COMP3331/22T3/79918822df364c1ec515c3f83efd658bbb178433d8bec65b208c81ee7eb7da10/Assigment_22T3V1.pdf)**.

### login
 - login with correct password
 - login with incorrect password, for 3 times. -- the client terminal should shutdown and user should be blocked.
 - login with with a blocked username, from another client(new terminal).
 - login with a username that does not exist -- should print out the error
 - Check the page 16~17 in SPEC, make sure you have the same output as the examples.
 - try this new [credentials.txt](https://github.com/lrlrlrlr/COMP3331_9331_22t2/blob/main/credentials.txt)  
 
### EDG
login to Yoda, test the EDG with these commands:  
- Your code should work properly with:  
	- `EDG 1 5`
	- `EDG 2 1000`
	- `EDG 3 5`
- Then check you have `Yoda-1.txt`, `Yoda-2.txt`,`Yoda-3.txt` generated in the same folder.  
- Your code should report the error with:  
	`EDG 0.1 100` -- invalid fileID  
	`EDG 4 10.00` -- invalid dataAmount  
	`EDG 35` -- invalid msg format, no dataAmount provided  
	
	

### UED
 - Use Yoda to issue `UED  ` command, The client should display an error message.
 - Use Yoda to issue `UED 1` command, then check the logfile *uploadlog.txt*, make sure the format is following the page 5 SPEC:
 ```
edgeDeviceName; timestamp; fileID; dataAmount
Yoda; 10 November 2022 10:31:13; 1; 5
 ```  


### SCS
 - Make sure you are doing the computation in the Server side.
 - Use Yoda to issue `SCS 1 MAX` command, The client should display a proper max value for file 1.
 - try AVERAGE, MIN, SUM at the same way.
 - try to issue `SCS 1 UNKNOWACTION` command, your client should be able to report the error unknown action.
 - try to issue `SCS 10 MAX` command, your client should be able to report the error file not exist.

### DTE
 - Use Yoda to issue `DTE x` command, The client should display an error message invalid fileID.
 - Use Yoda to issue `DTE 2` command, then check the logfile *deletion-log.txt*, make sure the format is following the page 6 SPEC:
  ```
edgeDeviceName; timestamp; fileID; dataAmount
Yoda; 30 September 2022 10:33:13; 2; 1000
 ```  
 - Then check if the file-2 has been deleted in the server side.
 
### AED
 - login as Yoda, then issue `AED` command, you should get the response “no other active edge devices”;   
 - login to Hans (and Yoda is also runnning in another terminal), then issue `AED` command in Hans' terminal, then you should be able to see Yoda is online and the UDP port number. Do not show the information about Hans.
                    
### OUT
 - Login to Yoda, check the active user log, yoda should be in the logfile. 
 - Issue command EDG and UED to upload a file to the server, then issue `OUT`, check the active user log in the server, yoda should not be in the logfile now. Then check Yoda-1.txt, yoda's file should still remain in the server.
 
### P2P (UVF)
 - Check the code in *client.py*, make sure it is **UDP** instead of **TCP**; (very important)  
 - Download the video file [ski.mp4](https://github.com/lrlrlrlr/COMP3331_9331_22t2/blob/main/ski.mp4), put it in the same folder with *client.py*.
 - Login to Yoda only, then issue `UVF` and `UVF Hans Filenotexist.mp4` and `UPD Hans ski.mp4`, your client should prompt an error message. 
 - Login to Yoda and Hans, then try to run `UPD Hans ski.mp4` in Yoda's terminal, you should be able to find the *yoda_ski.mp4* in the folder, try to play the video, see if it is playable. Also check the size of the video is the same(any packet loss?).

### What's more
Please check the **[Assignment SPEC](https://webcms3.cse.unsw.edu.au/static/uploads/course/COMP3331/22T3/79918822df364c1ec515c3f83efd658bbb178433d8bec65b208c81ee7eb7da10/Assigment_22T3V1.pdf)**. Page 17~22, test your program with the examples and make sure you have exactly same output.


## Lab1：  
 - [week 1 slides](https://github.com/lrlrlrlr/COMP3331_9331_22T3_Labs/blob/main/week2-lab1.pdf)

## Lab2
 - [week 2 slides(with demo code inside)](https://github.com/lrlrlrlr/COMP3331_9331_22T3_Labs/blob/main/week3-lab2.pdf)
  - Recording clip(Short video): 
   - q3 https://youtu.be/eBnyq6_IQqE  
   - q4 https://youtu.be/Yg5IwiD2Ync   
   - q5 https://youtu.be/9ARKigLwJfM  

## Lab3
 -  [Lab recording(with demo code inside)](https://www.youtube.com/watch?v=QXD2J7Ih2Cg&list=PL62Uy8LvT4FZjh1fCz9oeLAr9wmlfZJKD&index=3)
 
 ## Tut01 / Midterm
 -  [review slides](https://github.com/lrlrlrlr/COMP3331_9331_21T3/blob/main/9331review/slides_midterm_rev.pdf)
 - some marterial from previous year (but useful):
   -  w1~w5 review recording: https://youtu.be/1wc6fVItUuE 
   -  [Midterm Useful info](https://github.com/lrlrlrlr/COMP3331_9331_21T3/tree/main/9331review)


## Lab6
 [NS2 101](https://webcms3.cse.unsw.edu.au/files/fca493169b20fcc647f5e83600e25ed624c7b47df376a9fe8e2965991aba40e8/attachment)

### Exercise 1. 
 - Create a simulator object: `set ns [new simulator]`
 - Open file: `set fx [open filename.tr w]`
 - Create nodes: `set n1 [$ns node]`
 - Create links between the nodes: `$ns duplex-link $n1 $n6 2.5Mb 40ms DropTail`
 - Set the correct orientation: `$ns duplex-link-op $n1 $n2 orient up`
 - Setup TCP and FTP:
 	```
	# Create TCP conn
 	set tcpX [new Agent/TCP]
	$ns attach-agent $nX $tcpX

	#Sink for traffic at Node nX
	set sinkX [new Agent/TCPSink]
	$ns attach-agent $nX $sinkX

	#Connect
	$ns connect $tcpX $sinkX
	$tcpX set fid_ X

	#Setup FTP over TCP connection
	set ftpX [new Application/FTP]
	$ftpX attach-agent $tcpX
	```

- the proc function
	```
	
	proc record {} {
	>>	**global ns sink1 sink2 f1 f2**
		
		#Get an instance of the simulator
		set ns [Simulator instance]
		#Set the time after which the procedure should be called again
		set time 0.1
		#How many bytes have been received by the traffic sinks at n5?
		set bw1 [$sink1 set bytes_]
	>>	set bw2 [$sink2 set bytes_]
		#Get the current time
		set now [$ns now]
		#Calculate the bandwidth (in MBit/s) and write it to the files
		puts $f1 "$now [expr $bw1/$time*8/1000000]"
		puts $f2 "$now [expr $bw2/$time*8/1000000]"
		#Reset the bytes_ values on the traffic sinks
	>>	$sink1 set bytes_ 0
	>>	$sink2 ...........

		#Re-schedule the procedure
		$ns at [expr $now+$time] "record"
	}
	```
 - start recording: `ns at 0.0 "record"`
 - start FTP sessions: `$ns at 0.5 "$ftp1 start"`
 - Stop FTP sessions:  `$ns at 8.5 "$ftp1 stop"`
 - Call the finish procedure after 10 seconds of simulation time: `$ns at 10.0 "finish"`
 - Run the simulation: `$ns run`
 
