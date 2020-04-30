# PS-VPN
Configure a Virtual Private Network (VPN) using Windows PowerShell

== Planning:
Resources: https://

 * Gather Facts
   - ISP Address
   - Networking Environment
   - Server Resources
   - Accounts
   - EncryptionLevel (Optional/Required)
   - Use case (Full/Split)
 * PowerShell Syntax
   - Server: Create Radius Server
   - Server: Users and Groups
   - Server: Shared Secret
   - Client: Create Connection
   - Client: Create Routes
 * Security Considerations
   - Use MS-Chapv2
   - Always on VPN


== Execution:
Resources: https://

=== Gather Facts (Client)
    $ api.ipify.org
	$ netsh interface ipv4 show route

=== Create Connection (Client)
    $ set-VpnConnection -Name ">NAME<" -ServerAddress ">ADDRESS<" -TunnelType L2tp -AllUserConnection -L2tpPsk ">SHAREDKEY<" -AuthenticationMethod MSCHAPv2 -Encryption Optional -SplitTunneling $True -Force

=== Route Edits for Split (Client)
    $ netsh interface ipv4 add route 192.168.1.0/24 ">NAME<"
