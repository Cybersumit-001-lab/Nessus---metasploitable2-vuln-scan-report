# Remediation notes (high level)

This file summarizes recommended mitigations for common Metasploitable2 findings (applies generically).

## For backdoors and RCE services (vsftpd, distcc, etc.)
- Immediately remove the vulnerable package or upgrade to a patched release.
- If compromised, rebuild the VM from a known-good image.
- Change any credentials and rotate any secrets.

## For default credentials (Tomcat, MySQL, PostgreSQL)
- Identify all default/weak accounts; change passwords to strong, unique ones.
- Disable remote admin consoles or restrict via firewall / VPN.
- Use multi-factor authentication where supported.

## For Samba / SMB
- Disable anonymous/guest access.
- Patch Samba; restrict service to internal networks only.
- Use SMB signing and modern protocols.

## For general hardening
- Apply security updates to OS and packages.
- Run only necessary services. Remove test/demo accounts.
- Use host-based firewall to limit access (ufw/iptables).
- Monitor logs and enable alerting for unusual activity.
