# Linux Clients

This repo contains the ansible configuration to deploy a linux client.

## Usage

Tasks that have to be done before ansible can manage the workstation:

- Install the system using fedora
  - Use german keyboard layout and language
  - Set the hostname: `fablab-wsXX.lab.fablab.uni-erlangen.de`
  - Create a user `sysadmin` and make him an admin (member of `wheel`) (Password should be well known to admins)
  - Set the hostname to `fablab-ws%d.lab.fablab.fau.de`
  - Make sure this hostname is correctly configured on `ws01` in `/etc/dhcp/dhcpd.conf` (TODO provision ws01, too and automate this step)
- (Install and) start `sshd`: `systemctl start sshd`
- Edit `/etc/sudoers` and allow members of group `wheel` to gain root without password: `sudo visudo`
- You have to do an `dnf upgrade` and accept the PGP keys before the playbook is working completely

### Deploy ansible playbook

- `ansible-playbook site.yml [--diff]`
Test and simulate playbook with `--check`
Get debug output with `-vvv`

## TODO:

- configure printers
- install VisiCut

## License

[GPLv3](https://www.gnu.org/licenses/gpl.html)
