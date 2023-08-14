## Check Antivirus and realtime protection on server 2008R2

### 1. Launch cmd as administrator, then run the commands below

```sh
cd C:\Program Files\Microsoft Security Client
```

```sh
MpCmdRun.exe -getfiles
```


### 2. Collect logs

![img](https://guguimage.aceultraman.com/i/2023/08/14/j4ztl4-1.jpg)

 

Once the logs are generated, navigate to the path

```
C:\ProgramData\Microsoft\Microsoft Antimalware\support
```

![img](https://guguimage.aceultraman.com/i/2023/08/14/j4zp2m-1.jpg)

 

Then open `MPSupportFiles.cab`

 

#### 1. Check MPStateInfo.txt

The results below show that realtime monitor is enabled and threats suspicious detected

![img](https://guguimage.aceultraman.com/i/2023/08/14/j4zst0-1.jpg)

#### 2. Check MPSystemEvents.txt

Search for 1150, if you can find the results like below, then it means the endpoint protection is working

![img](https://guguimage.aceultraman.com/i/2023/08/14/j4ztfu-1.jpg)

 

#### 3. Check MPLog-xxxxx-235042xxxx.log 

![img](https://guguimage.aceultraman.com/i/2023/08/14/j4znr6-1.jpg)

Check if you can find the keyword `RTP start` in the file

Scroll down to the bottom, check if you can see `RTP Perf Log`

![img](https://guguimage.aceultraman.com/i/2023/08/14/j4zvlm-1.jpg)

If you can find them, then it means RTP is working well on the server.
