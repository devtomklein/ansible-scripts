AD-auth
=========

This role installs needed dependencies for authentication/authorization against AD in CentOS 7 using Winbind+Samba+Kerberos. There's still a couple of missing steps, such as getting the Ticket Granting Ticket (TGT) from Kerberos, making sure the net join is active and well, ...

Requirements
------------

None.

Role Variables
--------------

from vars/main.yml : 

	#We need the time delta between AD's clock and the linux machine to be < 5min for this to work
	ntp_srv: ntp.example.com

	krb_realm: REALM.LOCAL

	#You can pass several servers to use as failovers
	krb_kdc: ad.srv.local ad1.srv.local

	#Essentially the primary one (that will also grant the TGT ticket)
	krb_admin_svr: ad.srv.local

	#Your windows workgroup
	smb_workgroup: ORG
	smb_password_server: {{ krb_kdc }}
	smb_realm: {{ krb_realm }}


Dependencies
------------
None.

Example Playbook
----------------

License
-------

Author Information
------------------

Not for suitable for production, basically an outdated snapshot of some script I was working on at my previous position.