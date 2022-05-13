# Splunk_TA_Netscout_AED
Splunk Technical Add-On for Netscout Arbor Edge Defense


There was an existing TA from Arbor on https://github.com/arbor/TA_netscout_aed from 2019, but that did not match any of the traffic when sending events to a Syslog server. Wrote a new TA to CIM all the appropaite fields to the Intrusion Detection Datamodel and CIM it accordingly.

 The regular expressions will match on similar events that are formed according to this structure:
 
2022-05-13T15:32:31.000000+02:00 HOSTNAME arbor-networks-aps:Blocked Host: Blocked host 1.111.111.111 at 15:32 by Invalid Packets using TCP/22 (SSH) destination 222.22.22.22 source port 54900,EPOCH: 1652448750,PGID: 69,PGNAME: pg_yourpgname,URL: https://HOSTNAME/summary/
