# Simulate MDE alerts and incidents

## Multi-stage incident involving Defense evasion & Discovery on one endpoint

### Download `MTP_Fileless_Recon.txt` to `C:\Temp\MTP_Fileless_Recon.txt` from url below
```
https://wcdstaticfilesprdeus.blob.core.windows.net/wcdstaticfiles/MTP_Fileless_Recon.txt
```

```powershell
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12;

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
