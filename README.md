# MDE FAQ

## If the Azure VM is onboarded to MDE via MDE extension, can we change the channel before/after onboarding?

* Once the VM is onboared to MDE, We can confirm the current repository using the command
```cmd
mdatp health --field release_ring
```
![image](https://user-images.githubusercontent.com/96930989/210193924-93e3cf58-f459-42f2-adaa-fd436308c76f.png)

* If we want to switch the repository after the initial installation, it requires the product to be reinstalled. 

To switch the product channel: https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/linux-install-manually?view=o365-worldwide#how-to-migrate-from-insiders-fast-to-production-channel

Sample

![image](https://user-images.githubusercontent.com/96930989/210193993-d5ffd9dd-e606-4794-adc2-dac388fd6bad.png)
