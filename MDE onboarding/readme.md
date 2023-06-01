# Onboarding to MDE

## Onboarding Linux VM using local script downloaded from MDE portal

### 1. Download the onboarding package from [Microsoft 365 Defender portal](security.microsoft.com)to the Linux machine you want to onboard.
![image](https://github.com/guguji666666/GJS-MDE/assets/96930989/1be863b9-3c31-4068-9909-ece5711ee900)


### 2. Extract the contents of the archive.
```sh
unzip WindowsDefenderATPOnboardingPackage.zip
```

### 3. Navigate to the path where the script locates and run the onboarding script.
```sh
cd <path of the script>
```
```sh
sudo python MicrosoftDefenderATPOnboardingLinuxServer.py
```

### 4. Verify the device is now associated with your organization and it’s healthy.
```sh
mdatp health
```

### 5. If this device stays unhealthy after the onboarding, please collect the XMDEClientAnalyzer results:
```sh
wget --quiet -O XMDEClientAnalyzer.zip  https://aka.ms/XMDEClientAnalyzer
```
```sh
unzip -q XMDEClientAnalyzer.zip
```
```sh
cd XMDEClientAnalyzer
```
```sh
chmod +x mde_support_tool.sh
```

Run as `non-root` user to install required pip and lxml which components: 
```sh
sudo <user you want to switch>
```
```sh
./mde_support_tool.sh
```

To collect actual diagnostic package and generate the result archive file run again as root: 
```sh
sudo -i
```
```sh
./mde_support_tool.sh -d
```

Upload the generated zip file.

### Please also share the output of the following commands on this device:
```sh
cat /etc/opt/microsoft/mdatp/mdatp_onboard.json
```
```sh
ll /etc/opt/microsoft/mdatp/
```
```sh
ll /etc/opt/microsoft/
```
