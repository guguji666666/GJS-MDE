# MDE FAQ

## Onboarding

### 1. Check the channel used by MDE extension (MDE integration with MDC)
https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/linux-install-manually?view=o365-worldwide#configure-the-linux-software-repository
```
Defender for Endpoint on Linux can be deployed from one of the following channels (denoted below as [channel]): 
* insiders-fast
* insiders-slow
* prod
Each of these channels corresponds to a Linux software repository.
```

Once the VM is onboared to MDE, We can confirm the current repository using the command
```cmd
mdatp health --field release_ring
```

Sample <br>
`prod` channel is used while onboarding the machines via MDE extension:

![image](https://user-images.githubusercontent.com/96930989/210290330-5e804277-fc49-4d7b-a8d0-198bbafa5026.png)


### 2. Switch the `repository` after the initial installation 

To switch the product channel: https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/linux-install-manually?view=o365-worldwide#how-to-migrate-from-insiders-fast-to-production-channel

Sample <br>
![image](https://user-images.githubusercontent.com/96930989/210193993-d5ffd9dd-e606-4794-adc2-dac388fd6bad.png)

### 3. Default workspace used by MDE
![image](https://github.com/guguji666666/GJS-MDE/assets/96930989/3e504608-e3d1-4b7c-8704-3e938a1b087e)


