import socket

# Target IP or domain
target = input("Enter IP address or domain (e.g. scanme.nmap.org): ")

print(f"\n[INFO] Scanning {target}...\n")

# Ports to scan
open_ports = []
for port in range(20, 1025):
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    s.settimeout(0.5)
    result = s.connect_ex((target, port))
    if result == 0:
        print(f"✅ Port {port} is OPEN")
        open_ports.append(port)
    s.close()

if not open_ports:
    print("❌ No open ports found.")
else:
    print(f"\n✅ Open ports: {open_ports}")

# -PORT-SCANNER
code
example

