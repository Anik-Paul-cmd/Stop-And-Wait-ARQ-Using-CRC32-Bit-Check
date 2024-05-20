Project Statement:
We are given a project on sending and receiving data frames in data layer protocol and find if there is any error in the data frames or not. Stop and Wait ARQ is used to send and receive data and CRC-32 to check if there is any error or not. 

Introduction:
In our project we have implemented the data link layer protocols, with Stop and Wait ARQ. Stop and Wait ARQ is based on the stop-and-wait flow control technique. It is a method used in telecommunications to send information between two connected devices. It is the simplest kind of automatic repeat-request (ARQ) method. A stop-and-wait ARQ sender sends one frame at a time. After sending each frame, the sender doesn't send any further frames until it receives an acknowledgement (ACK) signal. The receiver uses the redundancy check number to check for possible damage. If the receiver sees that the frame is good, it sends an ACK.
Now to check, if there is any damaged frame while transmitting data we will use CRC-32. CRC32 is Cyclic Redundancy Check with 16 bit character length that is an error-detecting code commonly used in digital networks and storage devices to detect accidental changes to raw data. Blocks of data entering these systems get a short check value attached, based on the remainder of a polynomial division of their contents. On retrieval, the calculation is repeated and, in the event the check values do not match, corrective action can be taken against data corruption. CRC-32 is a polynomial function generator error checking technique where the value of parity is fixed. Therefore we need to calculate the checksum for the packet data but we do not have to consider the frame header information. Our checksum routine should be able to deal with packets of different sizes.

Working Procedure
![image](https://github.com/Anik-Paul-cmd/Stop-And-Wait-ARQ-Using-CRC32-Bit-Check/assets/57853726/1d036e9a-dd62-4924-a361-15eb6c8777d1)

Stop and Wait ARQ Description
Damaged frame:
A frame that arrives at its destination is experiencing damage or missing. When the receiver detects the presence of damage to the frame, the receiver will send a negative reply to the damaged frame and the transmitter will transmit the frame. For the case of missing frames in the middle of the transmission, the source computer equipped with a timer. Once the frame is transmitted, the source computer is waiting for a reply. If no reply is received until the time specified timer expires, the source computer will send back the same frame.

![image](https://github.com/Anik-Paul-cmd/Stop-And-Wait-ARQ-Using-CRC32-Bit-Check/assets/57853726/3da2fda3-d7fa-49d9-be0c-3d5bf04971ec)

Lost Frame:
The sender is equipped with a timer that starts every time a data frame is transmitted. If the frame lost in transmission the receiver can never acknowledge it. The sending device waits for an ACK or NAK frame until its timer goes off, then it tries again. It retransmits the last data frame.

![image](https://github.com/Anik-Paul-cmd/Stop-And-Wait-ARQ-Using-CRC32-Bit-Check/assets/57853726/ce21604d-ec61-49d5-a366-f395600cbfc2)

Damaged Acknowledgment:
The data frame was received by the receiver but the acknowledgement was lost in transmission. The sender waits until the timer goes off, then it retransmits the data frame. The receiver gets a duplicated copy of the data frame. So it knows the acknowledgement was lost so it discards the second copy.

![image](https://github.com/Anik-Paul-cmd/Stop-And-Wait-ARQ-Using-CRC32-Bit-Check/assets/57853726/420989db-c0ae-4ab2-9ebe-5b0076c3290b)

Stop and Wait ARQ Implementation
▪ First of all, we take data input from the file which will be transferred.
▪ Then we have calculated the required frame number needed for transfer the data.
▪ We have fixed the data field to 64 bits.
▪ We have store the predetermined divisor into a string by using 32-bit polynomial
equation.
▪ Then we generate the FCS code by using CRC function and attached it into the frame.
▪ Before transmitting the frame we have to choose error randomly and the number of error
will not more than 3 times.
▪ We checked the frame only for error in data and for others we just resend that frame
again to the receiver. 

CRC – 32:
1. As the value of divisor is fixed so we have to divide the frame first.
2. Then if Frame Check Sequence is not 0, then the data is corrupted. Error is present.
3. Now it will follow the Go Back n Sliding Window method to procced in the next step.
4. But if Frame Check sequence is 0, then the data is error free. So receiver will send an
ACK to the sender.

Conclusion:
The Stop-and-Wait method is an excellent technique to apply in checking errors in data
transmission with a small frame shape. Stop-and-Wait flow control function to transmit data by
the number of frames were broken up into smaller frames. By sending a frame per frame, the
delivery process will be faster. If a larger frame sent damaged, it would take a long time to resend
the data frame and the acknowledgment. 




