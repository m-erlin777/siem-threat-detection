# Detection Scenarios

Includes the data source, scenarios that generate telemetry, and commands involved.

## Windows Endpoint Host

### runas
```
runas /user:fakeuser2 powershell
```
Attempted cmd.exe execution of ```runas``` command and ```powershell``` launch from terminal.

KQL query ```message : (*runas*)``` filters logs based on the message field.

![Query](https://i.ibb.co/YTdcXGJH/runas-query2.png)

### reg
```
reg add HKLM\Software\FakeVendor\TestKey /v TestValue /t REG_SZ /d "SOC_Test" /f
```
Simulating registry access and manipulation via ```reg add``` and the following input.

KQL query ```message : ("*HKLM*")``` filters logs based on any sequence of HKLM in the message field.

![Query](https://i.ibb.co/0VKNftVP/hklm-query.png)

### whoami
```
whoami
```
Common host reconnaissance command typically present after initial intrusion.

KQL query ```message : (*whoami*)``` filters logs based on the message field.

![Query](https://i.ibb.co/KzKgC5Jc/whoami-query2.png)

### nslookup
```
nslookup
```
Common DNS reconnaissance command typically present after initial intrusion.

KQL query ```message : (*nslookup*)``` filters logs based on the message field.

![Query](https://i.ibb.co/mrMyMBrN/nslookup-query.png)
