# Windows Subsystem for Linux (WSL) Setup Guide

This guide provides step-by-step instructions for installing and setting up **Windows Subsystem for Linux (WSL)** on a Windows machine.

---

## **1. Enable WSL**
Open **PowerShell** as Administrator and run:

```powershell
wsl --install
```
This command installs WSL and sets up **Ubuntu** as the default Linux distribution.

If WSL is already installed, update it using:

```powershell
wsl --update
```

---

## **2. Install a Specific Linux Distribution (Optional)**
To see available distributions:

```powershell
wsl --list --online
```

To install a specific distribution (e.g., Debian):

```powershell
wsl --install -d Debian
```

---

## **3. Set WSL Version (WSL 1 or WSL 2)**
Check your installed distributions and their versions:

```powershell
wsl --list --verbose
```

To set **WSL 2** as the default version:

```powershell
wsl --set-default-version 2
```

To change a specific distribution’s version:

```powershell
wsl --set-version <DistroName> 2
```
Replace `<DistroName>` with your installed distribution, e.g., `Ubuntu`.

---

## **4. Launch & Configure WSL**
Open **Ubuntu** (or your installed distro) from the Start Menu.

Follow the on-screen instructions to create a username and password.

---

## **5. Update & Install Essential Packages**
Once inside WSL, update the package list and install essential utilities:

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y build-essential
```

---

## **6. Set WSL Default Distribution (Optional)**
If you have multiple distributions and want to set a default:

```powershell
wsl --set-default <DistroName>
```

---

## **7. Integrate WSL with Windows Terminal (Optional)**
1. Install **Windows Terminal** from the Microsoft Store.
2. Open Windows Terminal → Click the dropdown (⌄) → **Settings**.
3. Add a new profile for WSL.

---

## **8. Access Windows Files in WSL**
Your Windows files are accessible inside WSL at:

```bash
cd /mnt/c
```

---

## **9. Install WSLg for GUI Applications (Optional)**
To run Linux GUI applications on Windows:

```powershell
wsl --install
```

Then, install GUI apps inside WSL and launch them normally.

---

## **10. Uninstall WSL (If Needed)**
To uninstall WSL completely:

```powershell
wsl --unregister <DistroName>
```

To remove the WSL feature:

```powershell
wsl --uninstall
```

---

## **Conclusion**
You have successfully set up WSL on Windows! 🚀 Now you can run Linux commands and development tools directly on your Windows machine.

For more details, refer to the official [Microsoft WSL documentation](https://learn.microsoft.com/en-us/windows/wsl/).

