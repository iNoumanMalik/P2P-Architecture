# 📡 Java Peer-to-Peer Encrypted Messaging

This project demonstrates how two Java programs (`Peer` and `Receiver`) can securely exchange messages using **AES encryption**. It includes two use cases:

- 🖥️ **Same Device Communication**
- 🌐 **Different Devices Communication** (e.g., across LAN)

Both programs use **AES encryption** to secure messages in transit.

---

## 📁 Folder Structure

- `SameDevice/` — Code for running Peer and Receiver on the **same computer**
- `DifferentDevices/` — Code for sending messages **between two computers on the same network**

---

## 🚀 How to Run This Project

### 🧠 Prerequisites

- Java installed (JDK 8+)
- Either:
  - **NetBeans** (recommended for beginners)
  - **VS Code** with Java extension

---

## ✅ Using NetBeans

### 🔄 Common Setup for Both Folders

1. **Open NetBeans**
2. **Create a new Java project** (e.g., `MessagingApp`)
3. Inside the `src` folder, **create two Java classes**:
   - `Peer.java`
   - `Receiver.java`
4. **Copy the respective code** from `SameDevice/` or `DifferentDevices/` into the matching files.

---

### 🖥️ Same Device Flow (NetBeans)

- File Peer1.java is sender while File Peer2.java is receiver

- You can **open two terminals** in NetBeans:
  - One for `Receiver`
  - One for `Peer`
- In one terminal, run:  
  `Receiver`  
  _(It starts listening on port 5000)_

- In the second terminal, run:  
  `Peer`  
  _(It asks you to enter a message. Just hit Enter after writing it)_

- Messages are sent to `localhost:5000` and appear decrypted in the `Receiver` terminal.

> 💡 No need to compile manually (`javac`) in NetBeans. Just run the files.

---

### 🌐 Different Devices Flow (NetBeans)

> Make sure both computers are on the same Wi-Fi or LAN.

- Copy the code from `DifferentDevices/` into your NetBeans project.
- On **Computer A** (the receiver):
  - Run `Receiver` (it listens on port `5000`)
- On **Computer B** (the sender):
  - Run `Peer`
  - Enter:
    - A message
    - The **IP address of Computer A**
    - The port `5000`

> To find Computer A’s IP:

- On Windows: `ipconfig`
- On Mac/Linux: `ifconfig` or `ip a`

---

## 🧑‍💻 Using VS Code

### Setup

1. Open VS Code in the folder (e.g., `SameDevice/`)
2. Make sure the Java Extension Pack is installed.
3. Open `Peer.java` and `Receiver.java`
4. Run one in Terminal 1, the other in Terminal 2.

#### Same Device Flow (VS Code)

- Run `Receiver.java` first
- Run `Peer.java` next
- Enter message → It will appear decrypted in the Receiver terminal

#### Different Devices Flow (VS Code)

- Same as NetBeans: run `Receiver` on one device, `Peer` on the other
- Enter the receiver’s **IP address** in the `Peer` terminal

---

## 🔒 Encryption

- AES (Advanced Encryption Standard) is used with a shared **16-character key**
- The same key must be used in both `Peer` and `Receiver`
- Messages are encrypted before sending and decrypted after receiving

---

## 🔁 Message Flow Overview

### 💻 Same Device (localhost)

1. `Receiver` listens on `localhost:5000`
2. `Peer` encrypts message → sends to `localhost:5000`
3. `Receiver` decrypts and prints the message

### 🌐 Different Devices (LAN)

1. `Receiver` on Device A listens on `port 5000`
2. `Peer` on Device B asks for:
   - Message
   - Device A's IP address
   - Port (5000)
3. Message is encrypted and sent over the network
4. `Receiver` on Device A decrypts and displays the message

---

## 🛠 Troubleshooting

- Ensure firewall allows Java or port 5000 on both devices
- Confirm both devices are on the same network for cross-device messaging
- Use consistent AES key in both files
