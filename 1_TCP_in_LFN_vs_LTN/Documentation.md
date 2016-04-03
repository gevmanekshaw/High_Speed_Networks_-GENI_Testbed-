
Lab 2: Flow and Congestion Control/Experiment Design
=====================================================

Please fill in your name and net ID in the table below.

Lab Assignment | 2 - Flow and Congestion Control
-------------- | --------------------------------
Name           | Gev Manekshaw
Net ID         | gkm240
Report due     | Sunday, 22 February 11:59PM


Please answer the following questions:

1) Describe (as specifically as possible) the *goal* of your
experiment. What makes this a good goal? Do not just repeat
all of the indicators of a "good" goal described in the lecture;
explain *how* your selected goal embodies those indicators.

The goal of this experiment is to compare the throughput obtained
using TCP Hybla with other TCP variants such as TCP Vegas and TCP Reno
in a networking simulating lossy terrestrial to satellite links and 
wireless networks.
The goal above is well defined in terms of that it aptly states the 
specific information and the result expected. It gives a clear
indication of the kind of environment the experiment will be run inside. 
The goal addresses a very specific domain and is a good header as to
what the implementation of the project is.

---------------------------------------------------------------------

2) What is the TCP congestion control variant you have selected
as the main subject of your study? Describe briefly (1 paragraph)
what characterizes this TCP congestion control, and how it works.
Cite your sources.

The TCP congestion control variant selected for this experiment
is TCP Hybla. This TCP variant finds its application in satellite 
and wireless links. Terrestrial to Satellite links are characterized
by a longer round trip time and high bandwidth. This is a characteristic 
of a Long Fat Network (LFN). The typical delay is 200ms - 400ms, the 
bandwidth is approximately 400Mbps and hence a bandwidth- delay product
greater than 10^5 bits.Wireless links are characterized by a longer round 
trip time and low bandwidth. This is a characteristic of a Long Thin 
Network (LTN). The typical delay is 100ms - 200ms, the bandwidth is 
approximately 500kbps and hence a bandwidth- delay product less than
10^5 bits. TCP Hybla is used to achieve the same instantaneous 
bandwidth as that of a wired link, by eliminating RTT as a factor.
This variant also uses SACK as quicker loss recovery mechanism.[1][2]
-----------------------------------------------------------------------

3) What is the other LFN TCP you have selected to use in your
experiment? What is the non-LFN TCP you have selected to use
in your experiment? Be brief (1 paragraph each), and cite your
sources. Why did you choose these specifically?

The LFN TCP variant chosen for this experiment is TCP Vegas.
TCP Vegas used packet delay for evaluating the link quality.
This is done using the measurement of RTT. The reason behind
evaluating performance of this variant is that although
positive results are obtained in wireless links, it does
not address the poor performance in very larger RTT networks.

The Non-LFN TCP variant chosen for this experiment is TCP Reno.
TCP Reno implements slow start, fast retransmit and fast 
recovery mechanisms. This variant relies on packet loss
for congestion detection. The reason for evaluating this 
variant is that in TCP Reno the transmission link errors 
are erroneously attributed to congestion, which activates
the congestion avoidance mechanism. Satellite and wireless 
links have an inherent property of being lossy. Hence 
performance evaluation for these settings is justified.[1][2]
----------------------------------------------------------------------

4) Describe the parameters you have chosen to vary in your
experiment. Why did you choose these? How does this selection help further your stated goal?

The parameters that have selected to be varied during this experiment are:

a. Link Capacity:
The link capacity between the client and server is the maximum rate at 
which data can be transmitted. The goal of this experiment is to test
the TCP variants on different network settings. Varying the link
capacity essentially gives the different network environments. The 
satellite link (an LFN) is characterized by a high link capacity and
a wireless link (Non-LFN) is characterized by a lower link capacity. 

b. Link Latency:
Link Latency is the inherent delay present in the link. A two way
measurement of latency yields the RTT. Both wireless and satellite
links have a characteristically high latency. For satellite links,
this parameter varies significantly. Hence, an evaluation of the 
TCP variants for different values of this parameter is imperative.
----------------------------------------------------------------------


5) What metrics are you going to measure in your experiment?
Why did you choose these? How does this selection help further your stated goal?

The metric measured in the experiment is the throughput. Throughput is the 
successful transfer rate from the client to the server. The main aim of all
congestion avoidance mechanisms of TCP is to maximize the channel usage and 
exploit the network capacity to the maximum extent. Throughput is an indicator 
of such utilization. It indicates the number of successfully transmitted and
acknowledged packets. Hence, throughput is the most apt metric to be 
measured. This metric is measured using the Linux tool iperf.
---------------------------------------------------------------------------

6) For each **experimental unit** in your experiment, describe:

* The specific parameters with which this experimental unit ran
* The names of all the data files which give results from this experimental unit. Include all of these files in this `submit` folder.
* The specific values of the metrics you have chosen to measure.

The experiment was run in two settings, i.e. to simulate both a satellite 
link (LFN) and wireless link (Non-LFN). Packet loss of 1% was induced in both cases.

1.	For LFN (Satellite Links):
The link capacity was set to 450,000 kbps and the throughput was measured for 
TCP Hybla, TCP Vegas and TCP Reno at different values of delay:
Delay         -                Hybla                 Vegas            Reno      
250ms  	                      1.89Mbps              699kbps          408kbps
300ms                         919kbps               403kbps          365kbps
350ms                         692kbps               390kbps          229kbps
400ms                         471kbps               275kbps          166kbps

2.	For  Non-LFN (Wireless Links):
The link capacity was set to 450 kbps and the throughput was measured for TCP 
Hybla, TCP Vegas and TCP Reno at different values of delay:
Delay         -                Hybla                  Vegas           Reno      
100ms  	                      789kbps               633kbps          599kbps
150ms                         729kbps               496kbps          486kbps
200ms                         679kbps               486kbps          403kbps
250ms                         648kbps               471kbps          329kbps
-----------------------------------------------------------------------------------

7) Describe any evidence of *interactions* you can see in the results of your experiment.

If an interaction graph is plotted between the independent variables: capacity and delay, 
it is possible that there is a small difference in slope, due to which interaction will be possible.

If an approximation is used, then the slopes can be considered equal (parallel plots), and hence
there are no interactions.
------------------------------------------------------------------------------------

8) Briefly describe the results of your experiment (1-2 paragraphs). You may include images by putting them on an online
image hosting service, then putting the image URL in this file
using the syntax
![](http://link/to/image.png)

According to the experimental results, the TCP variant studied, i.e. Hybla, has 
shown better performance in all the cases presented. Delay (hence RTT) has 
been a critical parameter in both satellite and wireless links, that sets it
apart from other networks. Former versions of TCP have not been able to provide
an efficient way to make TCP connections more efficient. This is evident from the 
results above which show that TCP Hybla has proven to provide better throughput
than TCP Vegas and TCP Reno in both cases.

TCP Vegas is one of the variants designed for LFNs and TCP Reno is a general
purpose variant. TCP Hybla provides better throughput than both in LFNs as well 
as Non-LFNs. This is because the bandwidth calculation eliminates the dependence 
on RTT, which is critical in these networks. 
-----------------------------------------------------------------------------------


9) Find a published paper that studies the same TCP congestion
control variant you have chosen (it may study others as well).
Identify the paper you have chosen with a full citation, and
briefly answer the following questions about it:
The paper which is on the same lines as the experiment performed is:
“TCP Hybla: a TCP enhancement for heterogeneous networks”, Carlo Caini and Rosario Firrincieli.


 * What research question does this study seek to answer?
 
 The research question that this study seeks to answer is whether TCP Hybla, 
 which is intended for implementation in heterogenous networks, is a
 successful enhancement to standard TCP versions.
 
 * What kind of network environment was this study conducted in?
 
 The network environment that was simulated in ns-2 was characterized by 3 distinct cases:
1.	Performance in presence of congestion
2.	Performance in presence of link losses
3.	Performance of both congestion and link losses
 
 * How representative is the above network environment of the network setting this TCP variant is designed for?
 
 The network setting that was simulated on ns-2 is well suited for the network
 environment, i.e. terrestrial and satellite links. The essential parameters
 like delay, congestion and packet loss were successfully varied.
 
 * Does this study make some comparison to another TCP congestion
 control algorithm? If so, which, and does the author explain why these were selected?
 
 In this study, TCP Hybla is compared to 3 other standard TCP versions:
1.	Hybla without SACK 
2.	Vegas 
3.	NewReno/SACK 
The purpose of these comparisons is to evaluate whether TCP Hybla has 
proven to be an enhancement to these TCP variants. These TCP variants
work efficiently in standard (wired) links. The aim is to compare
them for heterogeneous network settings. 

 * What parameters does the author of this study consider? Does the
 author explain why?
 
 In the performance evaluation section, the study considers the following parameters:
1.	RTT
2.	Link Loss
3.	Congestion due to presence of shared wired link.
According to the author, the three parameters mentioned above are critical 
in heterogeneous links and a proper evaluation of the TCP variant will require
all three parameters.

 * What metrics does the author of this study consider? Does the author explain why?
 
 The metric that is measured is Goodput. 
 
 * Critique the experiment(s) in the paper. Does it make any of
 the common mistakes described in the lab lecture? Explain.
 
 The paper gives a very good blend of the theoretical as well as experimental 
 analysis of the variants being compared. The parameters set and varied in the 
 experiment are suitable to simulate heterogeneous networks.
 
However, the goal of the experiment is not specifically mentioned initially. 
The manner in which the goal will be proved remains generalized and ambiguous. 
Also, a general assumption is made on the superiority of the specific variant
without considering all the TCP variants that are suitable for this network setting. 


References:
[1] “TCP Hybla: a TCP enhancement for heterogeneous networks”, Carlo Caini and Rosario Firrincieli.
[2]  http://interstream.com/node/1084 
