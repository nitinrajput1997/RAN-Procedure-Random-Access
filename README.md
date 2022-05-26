# RAN-Procedure-Random-Access

Through initial access, the device was able to find out the cell. Now with random access procedure, the device will be able to access the cell. It was triggered in some different scenarios such as  

i) whenever the UE goes from RRC idle to RRC connected mode (may be due to device get switched-ON or entering the new coverage area after a while or first time). 

ii) if there are some uplink data to be send so it needs to request the resources to proceed then this procedure is used

iii) if somehow the synchronization is lost maybe due to inactivity from a device over a long time then this procedure is used

iv) when the synchronization is to be established with a new cell during handover process then this procedure can be used.

Random access procedure can be accept in two distinctive way, such as 

### 1) Contention Based Random Access
	
**Step 1:** The UE has to select the preamble randomly from the pool of resources which was shared with other UE and transmit the preamble. Now, there are some designated slot where, the UE was only able to send the random access preamble known as PRACH. Now, the UE is synchronized and also have system information, it was able to locate this designated slots and after finding it, then transmit the random access preamble in the appropriate places.

Now all the transmission are controlled by network with respect to timing adjustment command and power control. Whenever there was first uplink transmission, there is no such timing adjustment information available to the UE. So in that case, based on the timing received from the secondary synchronization block, the UE estimate the time for sending the preamble. If the timing estimate is correct which means that the preamble is transmitted successfully.

And somehow if there are some delay, then in such cases the preamble can interfere with other transmission because the timing of preamble has not been exactly with the given slot. To overcome this, guardtime is added in that slot to overcome the chances of having collision with the other transmission. If there is small cell then the guard time is also small and for the large cell, the guardtime is large. The UE can also estimate the transmission power based on the received power from the secondary synchronization block similary to the timing estimation.

But this is not the adequate power therefore there was a power ramping mechanism where the preamble may be repeated with the transmission power increasing during each retransmission. After the lots of predefined attempts has done, if there is no response, then the random access attempt is considered as failure. If one of the power is retransmission, the random access will move towards the further step.

**Step 2:** When the UE sends the random access preamble, it will wait for the random access response. This response will be given by network with the information like, it has received preamble or not and also it provides the temporary ID and the uplink resources to the UE for further communication. In brief random access response (RAR) includes information such as information about the preamble for which the response is valid, which was identified using random access preamble identifier.

When the lots of UE wants to perform random access at same time then using random access preamble identifier it was clear that response is actually for which UE. It also have timing correction due to which the UE can send for further communication with correct timing. RARG, it also includes scheduling grant through which the UE can understood that, what resource can we use while communicating with the next step message(step 3 message). It is also includes the temporary identity called TC- RNTI, which were used between the UE and the network for further communication. 

**Step 3:** Suppose there was a scenario where there was only one UE to perform random access procedure then no collision will occur. But in other scenario if there was lots of devices which wants to perform random access procedure then there is chance of collision while transmission. There are two scenarios. First, if number of you have different preamble, that means they will get different temporary ID i.e. TC-RNTI. So they will get differentiated and there will be no collision. 

Second, there will be a scenario, where the UE's wants to access the random access procedure at the same time and randomly select the same preamble, which means that the both UE have same temporary ID due to which the collision will occur and in this case is known as contention based random access. In this step, the UE has a temporary ID, so it will send RRC connection setup request, which includes the UE Contention Resolution identity which is 48 bits long and there is no chance that the different UE can get the same preamble and resolution identity.

Since it was first time when UE connecting to the network then it will take UE Contention Resolution Identity and if it is not its first time, then UE will use C-RNTI. The message send in Step 3, will have the unique ID. The message is transmitted using uplink share channel resources to the radio access network, it will ready already assigned in the previous step. 

**Step 4:** To make sure that device does not use the identity of other device. This step is used the response message was sent to the UE that connection setup is completed with the particular unique ID. So the response message was sent with a specific identity. Since they have the same temporary ID. Then, a unique ID will be asked to every UE which is necessary for validation for connection to the network.

Then one of the UE will provide the unique ID and that device temporary ID will be converted from TC-RNTI to the C-RNT. This means the random access is successful and other device will recieve response message as random access failure. When the random access is successful that means the device are now in RRC connected mode or state. And this is the completion of random access procedure in contention based.

### 2) Contention Free Random Access

It was triggered when the UE is handed over do another service and then there is downlink data for the UE, when there is non standalone mode and new NR cell is established.

**Step1:** random access preamble assignment is done in this step. In contention based random access, preamble are selected from set of preambles. In which, it is possible that more device can have the same preamble. Now in CFRA, the RAN is triggered, so it will not select the same preamble for different UE. Then RAN selects the preamble and give it to the UE and suggest the UE to start the random access procedure. 

**Step 2:** the unique preamble is received. The random access request is made from UE to the RAN. 

**Step 3:** On recieving unique preamble request, RAN gives random access response which includes the timing adjustment and power control information same as in contention based random access and also includes the information like uplink grant which is used by the UE for uplink communication.
