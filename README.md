# ccna-subnet-tool
As part of my CCNA journey, I wanted a better way to practice subnetting than staring at a static worksheet. So, I turned my classroom subnet cheat sheet into a fully interactive web app.

# 🌐 CCNA Subnet Reference Tool

An interactive, browser-based IPv4 subnetting tool built for CCNA students and network engineers. No installation required - open the HTML file and go.

---

## 📸 Overview

This tool digitizes the classic "subnet cheat sheet" used in CCNA coursework into a fully interactive web app. It covers:

- **Block Size / Subnet Mask reference grid** (color-coded just like the classroom sheet)
- **IP / CIDR Calculator** - instantly compute Network ID, Broadcast, First & Last Host, and usable hosts
- **VLAN Subnet Planner** - plan multi-VLAN networks with automatic VLSM allocation

---

## 🚀 Getting Started

### Option 1 - Open directly in your browser
1. Download or clone this repository
2. Open `subnet_tool.html` in any modern web browser (Chrome, Firefox, Edge, Safari)
3. No server, no install, no dependencies

```bash
git clone https://github.com/YOUR-USERNAME/ccna-subnet-tool.git
cd ccna-subnet-tool
open subnet_tool.html   # macOS
# or double-click subnet_tool.html in File Explorer (Windows)
```

### Option 2 — GitHub Pages
If you fork this repo, you can enable GitHub Pages under **Settings → Pages** to host it live at:
```
https://YOUR-USERNAME.github.io/ccna-subnet-tool/
```

---

## 🛠 Features

### 1. Reference Grid
A color-coded lookup table matching the CCNA classroom subnet sheet:
- 🟢 **Green row** - Block sizes and their corresponding subnet mask values (128/128, 64/192 ... 1/255)
- 🔴 **Red rows** - CIDR notation organized by octet (Octet 1 through Octet 4)
- `/31` and `/32` are marked **x** - not standard host subnets

**Key rules displayed:**
- Hosts = Block Size - 2
- Network ID: even multiple of the block size
- Broadcast = Network ID + Block Size − 1

### 2. IP / CIDR Calculator
Enter any IP address and CIDR prefix length to instantly calculate:

| Output | Description |
|---|---|
| Subnet Mask | Dotted-decimal mask (e.g. 255.255.255.192) |
| Block Size | Number of total addresses in the subnet |
| Network ID | First address - the network identifier |
| First Host | First usable host address |
| Last Host | Last usable host address |
| Broadcast | Last address - the broadcast identifier |
| Usable Hosts | Total assignable host addresses |

**Example:**
```
IP:   192.168.10.50
CIDR: /26

→ Mask:      255.255.255.192
→ Block:     64
→ Network:   192.168.10.0
→ First Host: 192.168.10.1
→ Last Host:  192.168.10.62
→ Broadcast: 192.168.10.63
→ Hosts:     62
```

### 3. VLAN Subnet Planner (VLSM)
Plan a multi-VLAN network from a single starting IP. Pre-loaded with a sample 7-VLAN layout:

| VLAN | Hosts Needed |
|---|---|
| Raleigh Clerical | 500 |
| Dallas Clerical | 200 |
| Raleigh Accounting | 31 |
| Dallas Accounting | 26 |
| Raleigh HR | 10 |
| Dallas HR | 6 |
| WAN | 2 |

The planner:
- **Auto-sorts VLANs largest-first** (VLSM best practice - most efficient address use)
- Calculates the smallest valid block for each VLAN
- Allocates subnets sequentially from your starting IP
- Shows: Block Size, Subnet Mask, Network IP, First Host, Last Host, Broadcast IP

You can edit existing rows or click **+ Add VLAN** to add your own.

---

## 📐 Subnetting Quick Reference

```
Block sizes:  128  64  32  16  8   4   2   1
Subnet mask:  128 192 224 240 248 252 254 255

Octet 1:  /1   /2   /3   /4   /5   /6   /7   /8
Octet 2:  /9  /10  /11  /12  /13  /14  /15  /16
Octet 3: /17  /18  /19  /20  /21  /22  /23  /24
Octet 4: /25  /26  /27  /28  /29  /30   x    x
```

**How to read a CIDR prefix:**
1. Find the prefix in the grid → identify the **octet** it falls in
2. The **column** tells you the block size and the last octet of the mask
3. Network ID = IP rounded **down** to the nearest multiple of the block size
4. Broadcast = Network ID + Block Size − 1

---

## 📁 File Structure

```
ccna-subnet-tool/
│
├── subnet_tool.html    # The entire application — single self-contained file
└── README.md           # This file
```

---

## 🎓 Who Is This For?

- **CCNA / CompTIA Network+ students** practicing subnetting
- **Network engineers** who want a fast reference without pulling up a calculator app
- **Instructors** who want a visual aid for teaching VLSM and subnet planning
- **Anyone** who just needs to quickly figure out a broadcast address

---

## 🤝 Contributing

Pull requests are welcome! Ideas for future features:

- [ ] Binary breakdown view (show each octet in binary)
- [ ] Subnet quiz / practice mode
- [ ] IPv6 support
- [ ] Export VLAN plan to CSV
- [ ] Dark/light theme toggle

---

## 📄 License

MIT License - free to use, share, and modify. Attribution appreciated but not required.

---

*Built with plain HTML, CSS, and JavaScript. No frameworks, no dependencies, no internet connection required.*
