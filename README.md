# Splunk_TA_Netscout_AED
Splunk Technical Add-On for Netscout Arbor Edge Defense


There was an existing TA from Arbor on hxxps://github.com/arbor/TA_netscout_aed from 2019, but that did not match any of the traffic when sending events to a Syslog server. So I wrote a new TA to CIM all the appropiate fields to the Intrusion Detection Datamodel and CIM it accordingly.

The regular expressions will match on similar events that are formed according to this structure:
  
eventtype=blocked_hosts:
2022-05-13T15:32:31.000000+02:00 HOSTNAME arbor-networks-aps:Blocked Host: Blocked host 1.111.111.111 at 15:32 by Invalid Packets using TCP/22 (SSH) destination 222.22.22.22 source port 54900,EPOCH: 1652448750,PGID: 69,PGNAME: pg_yourpgname,URL: hxxps://yourhostname/summary/

eventtype=change_log:
2022-05-16T10:49:19.000000+02:00 HOSTNAME arbor-networks-aps:Change Log: Username: system, Subsystem: ATLAS Intelligence Feed, Message: AIF Update requested: Rules: updated. Reputation Feed: updated.,URL: hxxps://yourhostname/administration/changelog/

eventtype=bandwidth:
2022-05-16T09:27:27.000000+02:00 HOSTNAME arbor-networks-aps:Bandwidth: Traffic for protection group 'pg_yourpgname' exceeded the threshold above the baseline.  The traffic level was 7.48 kpps.,URL: hxxps://yourhostname/groups/view/?time_interval=between&time_start=2022-05-16T09%3A20Z&timezone=Default&mode_state=between&unit_select=pps&id=141&time_end=2022-05-16T09%3A35Z

eventtype=cloud:
2022-05-16T02:40:08.000000+02:00 HOSTNAME arbor-networks-aps:Cloud Signaling: The Cloud Signaling provider does not manage the traffic for any  of the protected host prefixes in protection group 'Default Protection Group, pg_DEFAULT-PROTECTION-GROUP-IPV6, pg_TEST-COMCERT, pg_xx-01_xxx-1, pg_xx-02_xxxxxxxxxxxx, pg_xx-04_xxxxxxxxx, pg_xx-05_xxxxxxxxx, pg_ST-23_pg_xx-xx_xxx-Internet'.,URL: hxxps://yourhostname/summary/
