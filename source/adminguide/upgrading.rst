.. _upgrading:

******************
Upgrading Lizardfs
******************
.. auth-status-proof1/none

Upgrading to LizardFS 3.10.0
============================

    Direct upgrade is possible from LizardFS 2.6.0 - 3.9.4.

    * To upgrade from LizardFS 2.6.0, see upgrade notes for LizardFS 3.9.2

    * Upgrade shadow master servers before the master server; shadow master 
      will always refuse to connect to the master server in any newer version.
    
    * Upgrade the master/shadow servers before any chunkserver or client.
    
    * Chunkservers should be updated before clients, as they can still 
      understand legacy mount requests. Updating a client first will result 
      in being unable to read from/write to a 2.6.0 chunkserver.
    
    * Neither master servers nor chunkservers have hard coded connection 
      limits anymore.

    The previous value were 5000 for master server and 10000 for chunkserver.

    It is advisable to check if system limits are high enough for proper work 
    of LizardFS cluster.

    Mentioned values can be changed by modifying the /etc/security/
    limits.d/10-lizardfs.conf file or by using ulimit command.

Upgrading to LizardFS 3.9.4
===========================

    Direct upgrade is possible from LizardFS 3.9.2 and LizardFS 2.6.0.

    * 3.9.2 chunkservers need to be upgraded ASAP due to protocol changes

    * See upgrade notes for LizardFS 3.9.2

Upgrading to LizardFS 3.9.2
===========================

    Direct upgrade is possible from LizardFS 2.6.0.

    * Upgrade shadow master servers before the master server; shadow master 
      will always refuse to connect to the master server in any newer version.

 .. attention::
      It is recommended to perform metadata save before upgrading shadow 
      servers and refrain from using mfsmakesnapshot tool before upgrading 
      master.

      Not complying to this rule might cause potential checksum mismatches in 
      shadows.

      Metadata save can be triggered by the admin tool::

         $ lizardfs-admin save-metadata HOST PORT  
    
    * Upgrade the master/shadow servers before any chunkserver or client.
    
    * Chunkservers should be updated before clients, as they can still 
      understand legacy mount requests. Updating a client first will result 
      in being unable to read from/write to a 2.6.0 chunkserver.
    
    * Neither master servers nor chunkservers have hard coded connection 
      limits anymore.

    The previous values were 5000 for the master server and 10000 for the 
    chunkserver.
    
    It is advisable to check if system limits are high enough for proper work 
    of LizardFS cluster.
    
    Mentioned values can be changed by modifying ::

      /etc/security/limits.d/10-lizardfs.conf 

    or by using the ulimit command.

Upgrading to LizardFS 2.6.0
===========================

    Direct upgrade is possible from:

    * MooseFS  1.6.27 -- 1.6.27-5
    
    * LizardFS 1.6.28 -- 2.5.4.3

    When upgrading from LizardFS 2.5.4 or 2.5.4.\*

    * Upgrade shadow master servers before the master server; shadow master 
      will always refuse to connect to the master server in any newer version.
    
    * Upgrade the master server before any chunkserver or client.

    When upgrading from LizardFS 2.5.0 or 2.5.2
    
    * Proceed the same as in case of upgrade to LizardFS 2.5.4.

    When upgrading from other releases:
    
    * Proceed the same as in case of upgrade to LizardFS 2.5.2.

Upgrading to LizardFS 2.5.4
===========================

    Direct upgrade is possible from:
    
    * MooseFS  1.6.27 -- 1.6.27-5
    
    * LizardFS 1.6.28 -- 2.5.2

    When upgrading from LizardFS 2.5.0 or 2.5.2:
    
    * Upgrade shadow master servers before the master server; shadow master 
      will always refuse to connect to the master server in any newer version.
    
    * Upgrade the master server before any chunkserver or client.
    
    * Clients, chunkservers and the master server can be upgraded in any 
      order (all of them are compatible with each other), either one by one 
      or all at once.
    
    * CGI server 2.5.4 is compatible with all versions of the master server 
      (1.6.27 -- 2.5.2), so it can be upgraded at any time. Because of a bug 
      in older versions of the CGI serve it has to be stopped manually before 
      being upgraded (otherwise installation of the newer package may fail).

    When upgrading from other releases:
    
    * Proceed the same as in case of upgrade to LizardFS 2.5.2.

Upgrading to LizardFS 2.5.2
===========================

    Direct upgrade is possible from:

    * MooseFS  1.6.27 -- 1.6.27-5
    
    * LizardFS 1.6.28 -- 2.5.0

    When upgrading from LizardFS 2.5.0:

    * Upgrade shadow master servers before the master server; shadow master 
      will always refuse to connect to the master server in any newer version.
	  
    * Upgrade the master server
    
    * Clients, chunkservers and the master server can be upgraded in any 
      (all of them are compatible with each other), either one by one or all
      at once.

    When upgrading from previous releases:
    
    * There is no possibility to use shadow masters 2.5.2 before upgrading 
      the master server.
    
    * Upgrade the master server first, then all the chunkservers and then 
      clients (either all at once or one by one).

Upgrading to LizardFS 2.5.0
===========================

    Direct upgrade is possible from:

    * MooseFS  1.6.27 -- 1.6.27-5
    
    * LizardFS 1.6.28
    
    * Master server has to be upgraded before any client.
    
    * Chunkservers can be upgraded in any order (before the master server is 
      upgraded or after).

    * Shadow master server 2.5.0 is compatible with master server 1.6.27 and 
      newer.

Upgrading to LizardFS 1.6.28
============================

    Direct upgrade is possible from:

    * MooseFS 1.6.27 -- 1.6.27-5.

    All the servers and clients are compatible and can be upgraded in any 
    order.
