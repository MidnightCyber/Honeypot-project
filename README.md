# Cowrie Honeypot on Akamai (formerly Linode)

Welcome to the Cowrie honeypot setup on Akamai (formerly Linode) README file. This document provides instructions and information on setting up and using the Cowrie honeypot on the Akamai cloud platform.

## Introduction
Cowrie is an open-source SSH and Telnet honeypot designed to simulate vulnerable systems, attracting attackers and capturing their activities for analysis. By deploying Cowrie, you can gather valuable insights into emerging threats and enhance your cybersecurity defenses.

## Prerequisites
Before deploying Cowrie on Akamai, ensure you have the following:
- An Akamai (formerly Linode) account
- Basic understanding of Linux system administration
- Access to the Akamai Cloud Manager or CLI tools

## Deployment Steps
Follow these steps to deploy Cowrie honeypot on Akamai:

--------------------------------------------------------------
COMMANDS
--------------------------------------------------------------
0. Change ssh port
sudo nano /etc/ssh/sshd_config

sudo systemctl restart ssh

sudo systemctl status ssh

1. Install python dependencies
 sudo apt update

 sudo apt upgrade

sudo apt-get install git python3-virtualenv libssl-dev libffi-dev build-essential libpython3-dev python3-minimal authbind virtualenv

2. Create user account
sudo adduser --disabled-password cowrie

su - cowrie

3. Download cowrie
git clone http ://github.com/cowrie/cowri

4. Setup virtual environment
 virtualenv cowrie-env

 source cowrie-env/bin/activate

 pip install --upgrade pip

 pip install --upgrade -r requirements.txt

5. Enable telnet
 cp /etc/cowrie.cfg.dist cowrie.cfg

6.Iptables
sudo iptables -t nat -A PREROUTING -p tcp --dport 22 -j REDIRECT --to-port 2222

sudo iptables -t nat -A PREROUTING -p tcp --dport 23 -j REDIRECT --to-port 2223

6. Start cowrie
bin/cowrie start

7.live logs
tail -f ./var/log/cowrie/cowrie.log


6. **Monitoring and Analysis:**
   - Monitor the Cowrie logs and captured data for suspicious activities.
   - Analyze attacker behavior and use the insights to enhance cybersecurity defenses.

## Contributing
Contributions to the Cowrie project are welcome! If you encounter issues or have suggestions for improvements, please open an issue or submit a pull request on the [Cowrie GitHub repository](https://github.com/cowrie/cowrie).

## License
Cowrie is licensed under the GNU General Public License v2.0. See the [LICENSE](https://github.com/cowrie/cowrie/blob/master/LICENSE) file for details.

## Acknowledgements
We would like to thank the contributors to the Cowrie project for their valuable contributions and ongoing support.

## Contact
For questions or assistance, feel free to contact the maintainers of this repository.

