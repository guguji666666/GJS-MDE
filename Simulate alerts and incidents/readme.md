# Simulate MDE alerts and incidents

## 1. Multi-stage incident involving Defense evasion & Discovery on one endpoint

### Download `MTP_Fileless_Recon.txt` to `C:\Temp\MTP_Fileless_Recon.txt` from url below
```
https://wcdstaticfilesprdeus.blob.core.windows.net/wcdstaticfiles/MTP_Fileless_Recon.txt
```

```powershell
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12;

# Define the URL and the destination path
$url = "https://wcdstaticfilesprdeus.blob.core.windows.net/wcdstaticfiles/MTP_Fileless_Recon.txt"
$destination = "C:\Temp\MTP_Fileless_Recon.txt"

# Download the file
Invoke-WebRequest -Uri $url -OutFile $destination

$xor = [System.Text.Encoding]::UTF8.GetBytes('WinATP-Intro-Injection')

$base64String = Get-Content -Path "C:\Temp\MTP_Fileless_Recon.txt"

Try {
    $contentBytes = [System.Convert]::FromBase64String($base64String)
} Catch {
    $contentBytes = [System.Convert]::FromBase64String($base64String.Substring(3))
}


$i = 0

$decryptedBytes = @()

$contentBytes.ForEach{
    $decryptedBytes += $_ -bxor $xor[$i]
    $i++
    if ($i -eq $xor.Length) {
        $i = 0
    }
}

Invoke-Expression ([System.Text.Encoding]::UTF8.GetString($decryptedBytes))
 
```


### This script now includes a check to see if the directory C:\Temp exists, and if it doesn't, it creates the directory before downloading the file.
```powershell
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12;

# Define the URL and the destination path
$url = "https://wcdstaticfilesprdeus.blob.core.windows.net/wcdstaticfiles/MTP_Fileless_Recon.txt"
$destination = "C:\Temp\MTP_Fileless_Recon.txt"
$destinationDir = [System.IO.Path]::GetDirectoryName($destination)

# Create the directory if it doesn't exist
If (-Not (Test-Path -Path $destinationDir)) {
    New-Item -ItemType Directory -Path $destinationDir
}

# Download the file
Invoke-WebRequest -Uri $url -OutFile $destination

$xor = [System.Text.Encoding]::UTF8.GetBytes('WinATP-Intro-Injection')

$base64String = Get-Content -Path "C:\Temp\MTP_Fileless_Recon.txt"

Try {
    $contentBytes = [System.Convert]::FromBase64String($base64String)
} Catch {
    $contentBytes = [System.Convert]::FromBase64String($base64String.Substring(3))
}

$i = 0

$decryptedBytes = @()

$contentBytes.ForEach{
    $decryptedBytes += $_ -bxor $xor[$i]
    $i++
    if ($i -eq $xor.Length) {
        $i = 0
    }
}

Invoke-Expression ([System.Text.Encoding]::UTF8.GetString($decryptedBytes))
```


Alerts <br>
<img width="2130" alt="image" src="https://github.com/guguji666666/GJS-MDE/assets/96930989/8acbaa10-d61b-4e1a-9f1e-d4163a6deb33">

Incidents <br>
<img width="2142" alt="image" src="https://github.com/guguji666666/GJS-MDE/assets/96930989/d9af45ce-b65d-4ac0-a411-f750ed22d03f">

## 2. EDR alert 

[Generate EDR alert](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/run-detection-test?view=o365-worldwide#verify-microsoft-defender-for-endpoint-onboarding-of-a-device-using-a-powershell-detection-test)

```cmd
powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
```

## 3. Suspicious powershell script
```powershell
# Set the security protocol to TLS 1.2
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12

# Define the XOR key as a byte array encoded in UTF-8
$xor = [System.Text.Encoding]::UTF8.GetBytes('WinATP-Intro-Injection')

# Fetch the base64 encoded string from the specified URL
$base64String = (Invoke-WebRequest -URI https://winatpmanagement.windows.com/client/management/static/MTP_Fileless_Recon.txt -UseBasicParsing).Content

# Try to convert the base64 string to byte array, handle potential errors
Try {
    $contentBytes = [System.Convert]::FromBase64String($base64String)
} Catch {
    # If there's an error, attempt to convert the base64 string after removing the first 3 characters
    $contentBytes = [System.Convert]::FromBase64String($base64String.Substring(3))
}

# Initialize a counter and an array to store the decrypted bytes
$i = 0
$decryptedBytes = @()

# Decrypt the content using XOR operation
$contentBytes.ForEach {
    $decryptedBytes += $_ -bxor $xor[$i]
    $i++
    if ($i -eq $xor.Length) {
        $i = 0
    }
}

# Execute the decrypted content as a PowerShell expression
Invoke-Expression ([System.Text.Encoding]::UTF8.GetString($decryptedBytes))
```

```powershell
Invoke-WebRequest  "https://www.eicar.org/download/eicar_com-zip/?wpdmdl=8847&refresh=65d4b58cc7e0e1708438924" -OutFile C:\project\ps.zip
```
