# GPG Setup for Git Commit Signing

This guide will help you set up GPG key signing for Git on **Windows (WSL)** and **Ubuntu**.

---

## 📌 Step 1: Install GPG

### Windows (Git Bash)
1. Download and install **GPG for Windows** ([Gpg4win](https://gpg4win.org/download.html)).
2. Verify installation:
   ```sh
   gpg --version
   ```

### Ubuntu (WSL or Native)
1. Install GPG:
   ```sh
   sudo apt update && sudo apt install -y gnupg
   ```
2. Verify installation:
   ```sh
   gpg --version
   ```

---

## 🔑 Step 2: Generate a New GPG Key

Run the following command:
```sh
gpg --full-generate-key
```

1. Select **RSA (option 1)**.
2. Choose **4096-bit key** for better security.
3. Set expiration (**1 year recommended**).
4. Enter your **name and email** (should match your GitHub email).
5. Set a **strong passphrase**.

### List Your Keys
```sh
gpg --list-secret-keys --keyid-format=long
```

Example output:
```sh
sec   rsa4096/6F287C44A60BF48C 2025-02-01 [SC]
      56130AEF91648964CFE1E5A26F287C44A60BF48C
uid                 [ultimate] Your Name <your-email@example.com>
ssb   rsa4096/0921B0199B5482FC 2025-02-01 [E]
```
**Copy your GPG key ID** (the long hex after `rsa4096/`).

---

## 📌 Step 3: Export & Import GPG Keys (For Windows & WSL Users)

### Export GPG Keys on Windows
```sh
gpg --export-secret-keys --armor 6F287C44A60BF48C > secret-key.asc
gpg --export --armor 6F287C44A60BF48C > public-key.asc
```

### Move These Files to WSL
```sh
mv /mnt/c/Users/YourUsername/secret-key.asc ~/
mv /mnt/c/Users/YourUsername/public-key.asc ~/
```

### Import GPG Keys in WSL
```sh
gpg --import ~/secret-key.asc
gpg --import ~/public-key.asc
```

### Set Ultimate Trust
```sh
gpg --edit-key 6F287C44A60BF48C
trust
# Enter "5" for ultimate trust, then type "quit"
```

---

## 🔗 Step 4: Configure Git to Sign Commits

### Set GPG Key for Git
```sh
git config --global user.signingkey 6F287C44A60BF48C
git config --global commit.gpgsign true
git config --global gpg.program $(which gpg)
```

---

## 📌 Step 5: Add GPG Key to GitHub

### Get Your Public GPG Key
```sh
gpg --armor --export 6F287C44A60BF48C
```
Copy the output and add it to **GitHub → Settings → SSH & GPG Keys → New GPG Key**.

---

## 🚀 Step 6: Test Signed Commits

### Create a Signed Commit
```sh
git commit -S -m "chore: Signed commit"
```

### Verify Signature
```sh
git log --show-signature
```

---

## 🛠 Troubleshooting

### If You Get "No Secret Key" Error
```sh
gpg --list-secret-keys --keyid-format=long
```
If the key is missing, **re-import it**.

### If You Get "GPG Failed to Sign Data" Error
Make sure **pinentry** is installed:
```sh
sudo apt install pinentry-curses
```
Then configure GPG:
```sh
echo "use-agent" >> ~/.gnupg/gpg.conf
echo "pinentry-mode loopback" >> ~/.gnupg/gpg-agent.conf
gpgconf --kill gpg-agent
```

### If "mv" Command Fails in Windows
Use **PowerShell**:
```powershell
Move-Item -Path "C:\Users\YourUsername\secret-key.asc" -Destination "\\wsl$\Ubuntu\home\yourusername"
```

---

🎉 **You're all set!** Now all your Git commits will be **signed with GPG**.

