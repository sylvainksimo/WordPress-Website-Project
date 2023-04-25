# Requirements

#### Windows 7+ / Windows Server 2003+
#### PowerShell v2+ (Not PowerShell Core yet though)(minimum is v3 for install from this website due to TLS 1.2 requirement)
#### .NET Framework 4+ (the installation will attempt to install .NET 4.0 if you do not have it installed)(minimum is 4.5 for install from this website due to TLS 1.2 requirement)
#### That's it! All you need is choco.exe (that you get from the installation scripts) and you are good to go! No Visual Studio required.

# Installing Chocolatey

#### Chocolatey installs in seconds. You are just a few steps from running choco right now!

#### 1. First, ensure that you are using an administrative shell - you can also install as a non-admin, check out Non-Administrative Installation.
#### 2. Copy the text specific to your command shell - cmd.exe or powershell.exe.
#### 3. Paste the copied text into your shell and press Enter.
#### 4. Wait a few seconds for the command to complete.
#### 5. If you don't see any errors, you are ready to use Chocolatey! Type choco or choco -? now, or see Getting Started for usage instructions.


#### NOTE                                                                                                                                
- If you are behind a proxy, please see Installing behind a proxy.  
- Need completely offline solution? See Completely Offline Install. 
- Installing the licensed edition? See install licensed edition.    
- More Options / Troubleshooting                                    


## Install with cmd.exe                                              
 Run the following command:                                        

#### @"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "[System.Net.ServicePointManager]::SecurityProtocol = 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"


## Install with PowerShell.exe
With PowerShell, there is an additional step. You must ensure Get-ExecutionPolicy is not Restricted. We suggest using Bypass to bypass the policy to get things installed or AllSigned for quite a bit more security.

- Run Get-ExecutionPolicy. If it returns Restricted, then run Set-ExecutionPolicy AllSigned or Set-ExecutionPolicy Bypass -Scope Process.
- Now run the following command:
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

## Additional considerations
#### NOTE
Please inspect https://community.chocolatey.org/install.ps1 prior to running any of these scripts to ensure safety. We already know it's safe, but you should verify the security and contents of any script from the internet you are not familiar with. All of these scripts download a remote PowerShell script and execute it on your machine.

We take security very seriously. Learn more.

>>>"Why do I need to enable TLS 1.2 in PowerShell? Shouldn't it be on by default when I load PowerShell?"<<<

Unfortunately it's not always a default, and more of the time it is not. The low level is that it depends on .NET Framework and Windows.
- Explicitly set - Basically you need .NET Fx 4.5 at a minimum to be able to explicitly set TLS 1.2.
- Load by default - To have it load by default when you run PowerShell, you need at least .NET Fx 4.7 AND the Operating System's SystemDefault to have TLS 1.2 enabled.
The load by default is really hard to see, so you should check to ensure it is there. Assume it doesn't and set explicitly.

## Upgrading Chocolatey
Once installed, Chocolatey can be upgraded in exactly the same way as any other package that has been installed using Chocolatey. Simply use the command to upgrade to the latest stable release of Chocolatey:
choco upgrade chocolatey
