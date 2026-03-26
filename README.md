 SSH Honeypot
A lightweight Python-based SSH honeypot that listens for incoming SSH connections, logs all connection attempts, and automatically detects brute-force attacks.
Honeypot RunningBrute Force DetectionSSH Connection AttemptsListening on port 2222Alerts after 5 attemptsRepeated SSH connections

🔍 What It Does

Mimics an SSH server by sending a fake SSH-2.0-OpenSSH_8.2 banner
Logs every connection with timestamp and source IP
Detects brute-force attacks and triggers an alert after a configurable threshold
Captures initial SSH handshake data sent by connecting clients
Runs multi-threaded to handle multiple simultaneous connections


📋 Requirements

Python 3.x
No external libraries required (uses only Python standard library)


🚀 Getting Started
1. Clone the repository
bashgit clone https://github.com/your-username/ssh-honeypot.git
cd ssh-honeypot
2. Run the honeypot
bashpython3 honeypot.py

Note: Port 2222 does not require root privileges. If you want to use port 22, run with sudo.

3. Test it
bashssh test@localhost -p 2222
You should see connection logs appear in the terminal and in honeypot.log.

⚙️ Configuration
Edit the top of honeypot.py to change defaults:
VariableDefaultDescriptionHOST0.0.0.0Interface to listen onPORT2222Port to bind toLOG_FILEhoneypot.logLog file pathBRUTE_FORCE_THRESHOLD5Attempts before brute-force alert

📄 Log Format
All events are written to honeypot.log with timestamps:
2026-03-03 14:10:46.643735 - Connection from 127.0.0.1
2026-03-03 14:10:46.644026 - Data from 127.0.0.1: SSH-2.0-OpenSSH_8.9p1 Ubuntu-3ubuntu0.13
2026-03-03 14:10:47.427395 - ⚠ BRUTE FORCE ALERT: 127.0.0.1 has 5 attempts

🛡️ How Brute Force Detection Works
Each unique IP address is tracked in memory. Once the number of connections from a single IP reaches BRUTE_FORCE_THRESHOLD (default: 5), a brute-force alert is printed to the console and written to the log file. The counter persists for the lifetime of the process.

📁 Project Structure
ssh-honeypot/
├── honeypot.py       # Main honeypot script
├── honeypot.log      # Auto-generated log file (created at runtime)
└── README.md

⚠️ Disclaimer
This tool is intended for educational purposes and authorized network security research only. Do not deploy this on networks or systems you do not own or have explicit permission to monitor. Unauthorized interception of network traffic may violate local laws.

🤝 Contributing
Pull requests are welcome! For major changes, please open an issue first to discuss what you'd like to change.

📜 License
This project is licensed under the MIT License.
