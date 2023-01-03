# MDE FAQ

## Onborading

### 1. Check the channel used by MDE extension (MDE integration with MDC)

Once the VM is onboared to MDE, We can confirm the current repository using the command
```cmd
mdatp health --field release_ring
```

*Sample*

`prod` channel is used while onboarding the machines via MDE extension:

![image](https://user-images.githubusercontent.com/96930989/210289839-3d7e43f4-cc14-4d51-8acb-7a4178a0b438.png)


### 2. Switch the `repository` after the initial installation 

To switch the product channel: https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/linux-install-manually?view=o365-worldwide#how-to-migrate-from-insiders-fast-to-production-channel

*Sample*

![image](https://user-images.githubusercontent.com/96930989/210193993-d5ffd9dd-e606-4794-adc2-dac388fd6bad.png)
