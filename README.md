
# How_to_hack_an_IEC_61850_system

Smart  grid - IEC 61850 protocol ATTACKS

![image](https://github.com/Esamgold/How_to_hack_an_IEC_61850_system/assets/76063102/8d47c96b-ee5f-433c-881b-d40687af26b2)

IEC 61850 COMMUNICATION PROTOCOL ![image](https://github.com/Esamgold/How_to_hack_an_IEC_61850_system/assets/76063102/544bfacd-f725-44ab-96c3-73d68b2308a3)

![image](https://github.com/Esamgold/How_to_hack_an_IEC_61850_system/assets/76063102/6177eaf4-859d-4983-b700-5d534013b6c9)

![image](https://github.com/Esamgold/How_to_hack_an_IEC_61850_system/assets/76063102/dd1c75db-6fd2-4546-a49b-ae4058fec3bc)

Single line diagram - substation![image](https://github.com/Esamgold/How_to_hack_an_IEC_61850_system/assets/76063102/c2358fab-f65b-4d0c-adee-2b64763e4351)

![image](https://github.com/Esamgold/How_to_hack_an_IEC_61850_system/assets/76063102/53b4699f-acbf-44fd-906b-6abef0b76b0a)

Attack Scenarios![image](https://github.com/Esamgold/How_to_hack_an_IEC_61850_system/assets/76063102/b482bde2-4a83-4703-94ef-3312b28ce4c7)
![image](https://github.com/Esamgold/How_to_hack_an_IEC_61850_system/assets/76063102/dd632de3-e9c1-4d4e-ab66-2d0b1ef996b0)

Data Manipulation (DM)
Name: AS1.pcapng
Attack scenario 1: Inject false current measurements to bias the power system state estimation process without being detected.

LIED10 injects a GOOSE frame (No. 588) containing a value of 380 to the current magnitude of phase A at time= 11.9 sec.-
LIED10 injects a GOOSE frame (No. 1175) containing a value of 270 to the current magnitude of phase B at time= 22.5 sec.
LIED10 injects a GOOSE frame (No. 1771) containing a value of 360 to the current magnitude of phase C at time= 33.1 sec.

Name: AS2.pcapng
Attack scenario 2: Inject a malicious GOOSE frame to control the state of the circuit breaker
LIED11 injects a malicious GOOSE frame (No. 597) by toggling the status of the circuit breaker from FALSE to TRUE ('tripped') at time= 12.3 sec

Name: AS3.pcapng
Attack scenario 3: Replay an old GOOSE payload containing circuit breaker 'trip' status and other measurements messages
LIED11 replays previously valid GOOSE frames (No. 2734 and No. 2764) containing "open" circuit breaker information at time= 53.8 sec and 54.8 sec
 LIED22 replays previously captured fault current measurements (No. 7847, No. 7901, No. 7955, No. 8009, and No. 8063) between time= 155.8 sec and 159.88 sec
![image](https://github.com/Esamgold/How_to_hack_an_IEC_61850_system/assets/76063102/3641f9ab-6c08-43b8-88f2-205322060db2)

Denial of Service (DoS)
Name: AS1.pcapng
Attack scenario 1: Flood GOOSE messages to congest the substation network

LIED10 injects 5000 GOOSE frames between time= 12.5 sec and time= 22.1 sec
 LIED12 injects 5000 GOOSE frames between time= 54.7 sec and time= 68.3 sec
![image](https://github.com/Esamgold/How_to_hack_an_IEC_61850_system/assets/76063102/a582e3dd-3045-484d-9002-e718c805ad5a)

Message Suppression (MS)
Name: AS1.pcapng
Attack scenario 1: Inject a high stNum value or slightly higher than the previously recorded stNum, where sqNum≠0.

LIED10 injects a GOOSE frame (No. 542) with stNum=9999 and sqNum=10 at time= 13.9 sec.
 LIED12 injects a GOOSE frame (No. 784) with stNum=5 and sqNum=15 at time= 18.9 sec.

Name: AS2.pcapng
Attack scenario 2: Replay a previously valid GOOSE frame containing high stNum, sqNum =0 but stale timestamp
LIED10 replays a GOOSE frame (No. 534) with stNum=9999 and sqNum=0 at time= 10.4 sec.
LIED12 replays a GOOSE frame (No. 774) with stNum=5 and sqNum=0 at time= 15.5 sec.

Name: AS3.pcapng
Attack scenario 3: Inject a high stNum frame with sqNum = 0 and a valid timestamp.

LIED10 injects a GOOSE frame (No. 534) with stNum=9999 and sqNum=0 at time= 10.4 sec, where the timestamp of the injected GOOSE frame > previously received GOOSE frames.- LIED12 injects a GOOSE frame (No. 774) with stNum=5 and sqNum=0 at time=15.5 sec, where the timestamp of the injected GOOSE frame > previously received GOOSE frames.

Name: AS4.pcapng
Attack scenario 4: Inject a high sqNum frame to cause GOOSE frames to arrive at the receiver out-of-sequence i.e., not matching the order of transmission at the sender.

 LIED10 injects a GOOSE frame (No. 556) with sqNum=9999 at time= 12.7 sec
![image](https://github.com/Esamgold/How_to_hack_an_IEC_61850_system/assets/76063102/ee3784b0-9699-4b0c-8e26-4aee5c3c6b49)

Others
Name: CompositeAttack.pcapng
Attack scenario: Inject high stNum attack followed by modifying the circuit breaker status associated with CB-11.
 LIED11 injects a GOOSE frame (No. 542) with stNum=9999 and sqNum=0 at time=11.3 sec
 LIED11 modifies the Boolean value of CB-11 from ‘1’ to ‘0’ and injects the modified GOOSE frame (No. 792) at time=16.3 sec.
![image](https://github.com/Esamgold/How_to_hack_an_IEC_61850_system/assets/76063102/dbe4ac76-8129-4e9d-aeb2-3c64c9af1a5e)
