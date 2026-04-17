# Monitoring using SNMP

GitHub Enterprise provides data on disk usage, CPU utilization, memory usage, and more over SNMP.

SNMP is a common standard for monitoring devices over a network. We strongly recommend enabling SNMP so you can monitor the health of your GitHub Enterprise Server instance and know when to add more memory, storage, or processor power to the host machine.

GitHub Enterprise has a standard SNMP installation, so you can take advantage of the [many plugins](https://nagios-plugins.org/doc/man/check_snmp.html) available for Nagios or for any other monitoring system.

## Configuring SNMP v2c

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.
1. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.
1. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.
1. In "Settings" sidebar, click **Monitoring**.
1. Under "Monitoring", select **Enable SNMP**.
1. In the **Community string** field, enter a new community string. If left blank, this defaults to `public`.
1. Under the "Settings" sidebar, click **Save settings**.

   > [!NOTE]
   > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

1. Wait for the configuration run to complete.
1. Test your SNMP configuration by running the following command on a separate workstation with SNMP support in your network:

   ```shell
   # community-string is your community string
   # hostname is the IP or domain of your Enterprise instance
   $ snmpget -v 2c -c COMMUNITY-STRING -O e HOSTNAME hrSystemDate.0
   ```

This should return the system time on your GitHub Enterprise Server instance host.

## User-based security

If you enable SNMP v3, you can take advantage of increased user based security through the User Security Model (USM). For each unique user, you can specify a security level:
* `noAuthNoPriv`: This security level provides no authentication and no privacy.
* `authNoPriv`: This security level provides authentication but no privacy. To query the appliance you'll need a username and password (that must be at least eight characters long). Information is sent without encryption, similar to SNMPv2. The authentication protocol can be either MD5 or SHA and defaults to SHA.
* `authPriv`: This security level provides authentication with privacy. Authentication, including a minimum eight-character authentication password, is required and responses are encrypted. A privacy password is not required, but if provided it must be at least eight characters long. If a privacy password isn't provided, the authentication password is used. The privacy protocol can be either DES or AES and defaults to AES.

## Configuring users for SNMP v3

1. From an administrative account on GitHub Enterprise Server, in the upper-right corner of any page, click <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="Site admin" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg>.
1. If you're not already on the "Site admin" page, in the upper-left corner, click **Site admin**.
1. In the "<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-rocket" aria-label="rocket" role="img"><path d="M14.064 0h.186C15.216 0 16 .784 16 1.75v.186a8.752 8.752 0 0 1-2.564 6.186l-.458.459c-.314.314-.641.616-.979.904v3.207c0 .608-.315 1.172-.833 1.49l-2.774 1.707a.749.749 0 0 1-1.11-.418l-.954-3.102a1.214 1.214 0 0 1-.145-.125L3.754 9.816a1.218 1.218 0 0 1-.124-.145L.528 8.717a.749.749 0 0 1-.418-1.11l1.71-2.774A1.748 1.748 0 0 1 3.31 4h3.204c.288-.338.59-.665.904-.979l.459-.458A8.749 8.749 0 0 1 14.064 0ZM8.938 3.623h-.002l-.458.458c-.76.76-1.437 1.598-2.02 2.5l-1.5 2.317 2.143 2.143 2.317-1.5c.902-.583 1.74-1.26 2.499-2.02l.459-.458a7.25 7.25 0 0 0 2.123-5.127V1.75a.25.25 0 0 0-.25-.25h-.186a7.249 7.249 0 0 0-5.125 2.123ZM3.56 14.56c-.732.732-2.334 1.045-3.005 1.148a.234.234 0 0 1-.201-.064.234.234 0 0 1-.064-.201c.103-.671.416-2.273 1.15-3.003a1.502 1.502 0 1 1 2.12 2.12Zm6.94-3.935c-.088.06-.177.118-.266.175l-2.35 1.521.548 1.783 1.949-1.2a.25.25 0 0 0 .119-.213ZM3.678 8.116 5.2 5.766c.058-.09.117-.178.176-.266H3.309a.25.25 0 0 0-.213.119l-1.2 1.95ZM12 5a1 1 0 1 1-2 0 1 1 0 0 1 2 0Z"></path></svg> Site admin" sidebar, click **Management Console**.
1. In "Settings" sidebar, click **Monitoring**.
1. Under "Monitoring", select **Enable SNMP**.
1. Select **SNMP v3**.
1. Under "Username", type the unique username of your SNMP v3 user.
1. Select the **Security Level** dropdown menu, then click the security level for your SNMP v3 user.
1. For SNMP v3 users with the `authnopriv` security level, configure authentication.
    * Under "Authentication password", type the authentication password.
    * Next to "Authentication password", select the **Protocol** dropdown menu, then click the authentication protocol you want to use.
    * If your external monitoring system requires the SHA algorithm, GitHub Enterprise Server currently uses SHA-1.
1. For SNMP v3 users with the `authpriv` security level, configure authentication.
    * Under "Authentication password", type the authentication password.
    * Next to "Authentication password", select the **Protocol** dropdown menu, then click the authentication protocol you want to use.
    * Optionally, under "Privacy password", type the privacy password.
    * Next to "Privacy password", select the **Protocol** dropdown menu, then click the privacy protocol method you want to use.
    * If your external monitoring system requires the AES algorithm, GitHub Enterprise Server currently uses AES-128.
1. Click **Add user**.
1. Under the "Settings" sidebar, click **Save settings**.

   > [!NOTE]
   > Saving settings in the Management Console restarts system services, which could result in user-visible downtime.

1. Wait for the configuration run to complete.

### Querying SNMP data

Both hardware and software-level information about your appliance is available with SNMP v3. Due to the lack of encryption and privacy for the `noAuthNoPriv` and `authNoPriv` security levels, we exclude the `hrSWRun` table (1.3.6.1.2.1.25.4) from the resulting SNMP reports. We include this table if you're using the `authPriv` security level. For more information, see the [MIB documentation](https://github.com/net-snmp/net-snmp-htdocs/blob/master/docs/mibs/HOST-RESOURCES-MIB.txt).

With SNMP v2c, only hardware-level information about your appliance is available. The applications and services within GitHub Enterprise do not have OIDs configured to report metrics. Several MIBs are available, which you can see by running `snmpwalk` on a separate workstation with SNMP support in your network:

```shell
# community-string is your community string
# hostname is the IP or domain of your Enterprise instance
$ snmpwalk -v 2c -c COMMUNITY-STRING -O e HOSTNAME
```

Of the available MIBs for SNMP, the most useful is `HOST-RESOURCES-MIB` (1.3.6.1.2.1.25). See the table below for some important objects in this MIB:

| Name | OID | Description |
| ---- | --- | ----------- |
| hrSystemDate.2 | 1.3.6.1.2.1.25.1.2 | The hosts notion of the local date and time of day. |
| hrSystemUptime.0 | 1.3.6.1.2.1.25.1.1.0 | How long it's been since the host was last initialized. |
| hrMemorySize.0 | 1.3.6.1.2.1.25.2.2.0 | The amount of RAM on the host. |
| hrSystemProcesses.0 | 1.3.6.1.2.1.25.1.6.0 | The number of process contexts currently loaded or running on the host. |
| hrStorageUsed.1 | 1.3.6.1.2.1.25.2.3.1.6.1 | The amount of storage space consumed on the host, in hrStorageAllocationUnits. |
| hrStorageAllocationUnits.1 | 1.3.6.1.2.1.25.2.3.1.4.1 | The size, in bytes, of an hrStorageAllocationUnit |

For example, to query for `hrMemorySize` with SNMP v3, run the following command on a separate workstation with SNMP support in your network:

```shell
# username is the unique username of your SNMP v3 user
# auth password is the authentication password
# privacy password is the privacy password
# hostname is the IP or domain of your Enterprise instance
$ snmpget -v 3 -u USERNAME -l authPriv \
  -A "AUTH PASSWORD" -a SHA \
  -X "PRIVACY PASSWORD" -x AES \
  -O e HOSTNAME HOST-RESOURCES-MIB::hrMemorySize.0
```

With SNMP v2c, to query for `hrMemorySize`, run the following command on a separate workstation with SNMP support in your network:

```shell
# community-string is your community string
# hostname is the IP or domain of your Enterprise instance
snmpget -v 2c -c COMMUNITY-STRING HOSTNAME HOST-RESOURCES-MIB::hrMemorySize.0
```

> [!NOTE]
> To prevent leaking information about services running on your appliance, we exclude the `hrSWRun` table (1.3.6.1.2.1.25.4) from the resulting SNMP reports unless you're using the `authPriv` security level with SNMP v3. If you're using the `authPriv` security level, we include the `hrSWRun` table.

For more information on OID mappings for common system attributes in SNMP, see [Linux SNMP OID’s for CPU, Memory and Disk Statistics](http://www.linux-admins.net/2012/02/linux-snmp-oids-for-cpumemory-and-disk.html).