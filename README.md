# Splunk_TA_Netscout_AED

Released on Splunkbase: https://splunkbase.splunk.com/app/6441

Splunk Technical Add-On for NETSCOUT Arbor Edge Defense (AED)

Basically there are 3 options for selection of export format of the logs:

- Legacy
- CEF
- LEEF

This app will match the <b>Legacy</b> format.

There was an existing TA from Arbor on hxxps://github.com/arbor/TA_netscout_aed from 2019, but that did not match any of the traffic when sending events to a Syslog server. That app expects the format to be CEF or LEEF. So I wrote a new TA to CIM all the appropiate fields to the Intrusion Detection Datamodel and CIM it accordingly.
This app is for Legacy mode data export to syslog.

The regular expressions will match on similar events that are formed according to this structure:
  
<b>eventtype=blocked_hosts</b><br>
2022-05-13T15:32:31.000000+02:00 HOSTNAME arbor-networks-aps:Blocked Host: Blocked host 1.111.111.111 at 15:32 by Invalid Packets using TCP/22 (SSH) destination 222.22.22.22 source port 54900,EPOCH: 1652448750,PGID: 69,PGNAME: pg_yourpgname,URL: hxxps://yourhostname/summary/

<b>eventtype=change_log</b><br>
2022-05-16T10:49:19.000000+02:00 HOSTNAME arbor-networks-aps:Change Log: Username: system, Subsystem: ATLAS Intelligence Feed, Message: AIF Update requested: Rules: updated. Reputation Feed: updated.,URL: hxxps://yourhostname/administration/changelog/

<b>eventtype=bandwidth</b><br>
2022-05-16T09:27:27.000000+02:00 HOSTNAME arbor-networks-aps:Bandwidth: Traffic for protection group 'pg_yourpgname' exceeded the threshold above the baseline.  The traffic level was 7.48 kpps.,URL: hxxps://yourhostname/groups/view/?time_interval=between&time_start=2022-05-16T09%3A20Z&timezone=Default&mode_state=between&unit_select=pps&id=141&time_end=2022-05-16T09%3A35Z

<b>eventtype=cloud</b><br>
2022-05-16T02:40:08.000000+02:00 HOSTNAME arbor-networks-aps:Cloud Signaling: The Cloud Signaling provider does not manage the traffic for any  of the protected host prefixes in protection group 'Default Protection Group, pg_DEFAULT-PROTECTION-GROUP-IPV6, pg_TEST-COMCERT, pg_xx-01_xxx-1, pg_xx-02_xxxxxxxxxxxx, pg_xx-04_xxxxxxxxx, pg_xx-05_xxxxxxxxx, pg_ST-23_pg_xx-xx_xxx-Internet'.,URL: hxxps://yourhostname/summary/

For support, questions or suggestions contact me @ andre.zeemering@gmail.com

Next version is currently in development. This will support all 3 logging formats.
