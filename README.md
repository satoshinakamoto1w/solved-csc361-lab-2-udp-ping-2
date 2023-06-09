Download Link: https://assignmentchef.com/product/solved-csc361-lab-2-udp-ping-2
<br>
<table width="789">

 <tbody>

  <tr>

   <td width="789"> PROBLEM STATEMENTIn this lab, you will learn the basics of socket programming for UDP in Python. You will learn how to send and receive datagram packets using UDP sockets and also, how to set a proper socket timeout. Throughout the lab, you will gain familiarity with a Ping application and its usefulness in computing statistics such as packet loss rate.You will first study a simple Internet ping server written in Python, and implement a corresponding client. The functionality provided by these programs is similar to the functionality provided by standard ping programs available in modern operating systems. However, these programs use a simpler protocol, UDP, rather than the standard <strong>Internet Control Message Protocol</strong> ( ICMP ) to communicate with each other. The ping protocol allows a client machine to send a packet of data to a remote machine, and have the remote machine return the data back to the client unchanged (an action referred to as echoing). Among other uses, the ping protocol allows hosts to determine round-trip times to other machines.You are given the complete code for the Ping server pingserver.py . Your task is to write the Ping client ( pingclient.py ).SERVER CODEThe server code fully implements a ping server. You need to compile and run this code before running your client program. You do not need to modify this code.In this server code, 30% of the client’s packets are simulated to be lost. You should study this code carefully, as it will help you write your ping client.The server sits in an infinite loop listening for incoming UDP packets. When a packet comes in and if a randomized integer is greater than or equal to 4, the server simply capitalizes the encapsulated data and sends it back to the client.</td>

  </tr>

 </tbody>

</table>




<table width="789">

 <tbody>

  <tr>

   <td width="789">                                                                                     PACKET LOSSUDP provides applications with an unreliable transport service. Messages may get lost in the network due to router queue overflows, faulty hardware or some other reasons. Because packet loss is rare or even non-existent in typical campus networks, the server in this lab injects artificial loss to simulate the effects of network packet loss. The server creates a variable randomized integer which determines whether a particular incoming packet is lost or not.CLIENT CODEYou need to implement the following client program.The client should send 10 pings to the server. Because UDP is an unreliable protocol, a packet sent from the client to the server may be lost in the network, or vice versa. For this reason, the client cannot wait indefinitely for a reply to a ping message. You should get the client wait up to one second for a reply; if no reply is received within one second, your client program should assume that the packet was lost during transmission across the network. You will need to look up the Python documentation to find out how to set the timeout value on a datagram socket.Specifically, your client program should1.     send the ping message using UDP (Note: Unlike TCP, you do not need to establish a connection first, since UDP is a connectionless protocol.)2.     print the response message from server, if any3.     calculate and print the round trip time (RTT), in seconds, of each packet, if server responses4.     otherwise, print “Request timed out”During development, you should run the pingserver.py on your machine, and test your client by sending packets to localhost (or, 127.0.0.1). After you have fully debugged your code, you should see how your application communicates across the network with the ping server and ping client running inside the CSC361-VM with different IP addresses and port numbers.MESSAGE FORMATThe ping messages in this lab are formatted in a simple way. The client message is one line, consisting of ASCII characters in the following format:</td>

  </tr>

 </tbody>

</table>




<table width="789">

 <tbody>

  <tr>

   <td rowspan="2" width="75"> </td>

   <td width="639">    1          ping sequence_number time</td>

   <td rowspan="2" width="75">  </td>

  </tr>

  <tr>

   <td width="639">where sequence_number starts at 1 and progresses to 10 for each successive ping message sent by the client, and time is the time when the client sends the message.WHAT TO HAND INYou will hand in the complete client code and screenshots at the client verifying that your ping program works as required. Submit your solutions as attachments, including the Python code and a Wireshark screen capture.EVALUATIONYou must demonstrate your working code inside the CSC361-VM using Wireshark. Using

    <table width="109">

     <tbody>

      <tr>

       <td colspan="2" width="77">CSC361-VM</td>

       <td width="31"> </td>

      </tr>

      <tr>

       <td width="54">not just</td>

       <td colspan="2" width="54">127.0.0.x</td>

      </tr>

      <tr>

       <td width="54"></td>

       <td width="23"></td>

       <td width="31"></td>

      </tr>

     </tbody>

    </table>, the server and the client must use different IP addresses and port numbers, i.e.,. Your Wireshark demo must capture all related packets, including ARP and UDP .You are also required answer a few questions related to this lab during evaluation.Our evaluation scheme is:(50%) Correctness of Python code(20%) Wireshark demo(30%) Questions and Answers (at least 5 questions)</td>

  </tr>

 </tbody>

</table>


