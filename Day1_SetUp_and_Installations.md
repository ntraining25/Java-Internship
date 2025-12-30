# Day 1 - Student Learning Guide
## Environment Setup & Introduction to Full-Stack Development

### 🎯 **What You'll Learn Today**
- What is full-stack development and why it's exciting
- The technologies we'll use and why they're important
- How to set up your development environment

---

## 📖 **Theory: Understanding Full-Stack Development**

### **What is Full-Stack Development?**

Think of building a mobile app like building a restaurant:

**Frontend (What customers see):**
- Restaurant's dining area, menu, decorations
- In apps: Buttons, forms, colors, animations
- **Technologies we'll learn:** Angular 19 + TypeScript

**Backend (What happens behind the scenes):**
- Restaurant's kitchen where food is prepared
- In apps: Processing data, business logic, calculations
- **Technologies we'll learn:** Java 21 + Spring Boot

**Database (Where everything is stored):**
- Restaurant's storage room and inventory
- In apps: User profiles, messages, posts, all data
- **Technologies we'll learn:** H2 Database + MySQL

**API (Communication between parts):**
- Restaurant's waiters taking orders and serving food
- In apps: How frontend talks to backend
- **Technologies we'll learn:** REST APIs

### **Real-World Examples:**

**WhatsApp Full-Stack:**
- **Frontend:** Chat interface, emoji picker, send button
- **Backend:** Message encryption, delivery confirmation
- **Database:** All your messages, contacts, media files
- **API:** Sending message from your phone to recipient's phone

**Instagram Full-Stack:**
- **Frontend:** Photo filters, like button, story viewer
- **Backend:** Photo processing, recommendation algorithm
- **Database:** Photos, user profiles, comments, likes
- **API:** Uploading photos, fetching feed content

---

## 🛠 **Technology Stack We'll Learn**

### **Java 21 - Backend Programming Language**
```
What: Modern programming language for building server applications
Why we chose it:
✅ Used by Netflix, Amazon, Google, LinkedIn
✅ Easy to learn and read
✅ Excellent job opportunities
✅ Strong community support

What you'll build with it:
- REST APIs for data processing
- Business logic for applications
- Database connections and operations
```

### **Spring Boot 3.x - Backend Framework**
```
What: Framework that makes Java development super easy
Why it's amazing:
✅ Auto-configures everything for you
✅ Industry standard (most companies use it)
✅ Reduces coding time by 70%
✅ Built-in security and testing features

What you'll build with it:
- Complete REST APIs in minutes
- Database connectivity
- Error handling and validation
```

### **Angular 19 - Frontend Framework**
```
What: Framework for building beautiful, interactive web applications
Why it's powerful:
✅ Used by Google, Microsoft, Samsung
✅ Creates professional-looking UIs
✅ Handles complex user interactions
✅ Mobile-friendly responsive design

What you'll build with it:
- Interactive forms and buttons
- Dynamic web pages
- Real-time data updates
- Professional user interfaces
```

### **Additional Tools:**

**H2 Database:** Simple database for learning and development
**MySQL:** Production database used by real applications
**Git & GitHub:** Save your code and showcase your work
**Postman:** Test your APIs before building frontend
**IntelliJ IDEA:** Smart coding environment with helpful features

---

## 💻 **Practice: Environment Setup**

### **Step 1: Install Java Development Kit (JDK) 21 - Complete Guide**

#### **🖥️ For Windows (Detailed Steps):**

**1. Download Java 21:**
- Go to: https://www.oracle.com/java/technologies/downloads/
- Scroll down to "Java SE Development Kit 21.x.x"
- Click "Windows" tab
- Download "x64 Installer" (approximately 150-200 MB)
- File will be named something like: `jdk-21.0.x_windows-x64_bin.exe`

**2. Install Java:**
- Double-click the downloaded installer
- Click "Next" on welcome screen
- **IMPORTANT:** Note the installation path (usually `C:\Program Files\Java\jdk-21.0.x\`)
- Click "Next" → "Next" → "Install"
- Wait for installation (2-3 minutes)
- Click "Close" when finished

**3. Set Environment Variables (Critical Step):**

**Set JAVA_HOME:**
- Right-click "This PC" or "My Computer" → Properties
- Click "Advanced system settings"
- Click "Environment Variables" button
- Under "System Variables" section, click "New"
- Variable name: `JAVA_HOME`
- Variable value: `C:\Program Files\Java\jdk-21.0.x` (your actual installation path)
- Click "OK"

**Update PATH Variable:**
- In "System Variables" section, find and select "Path"
- Click "Edit"
- Click "New"
- Add: `%JAVA_HOME%\bin`
- Click "OK" → "OK" → "OK"

**4. Verify Installation:**
- **Close all Command Prompt windows** (important!)
- Open new Command Prompt (Press `Win + R`, type `cmd`, press Enter)
- Type: `java -version`
- Expected output:
```
java version "21.0.x" 2024-xx-xx LTS
Java(TM) SE Runtime Environment (build 21.0.x+xx-LTS-xxx)
Java HotSpot(TM) 64-Bit Server VM (build 21.0.x+xx-LTS-xxx, mixed mode, sharing)
```
- Type: `javac -version`
- Expected output: `javac 21.0.x`

#### **🍎 For macOS (Detailed Steps):**

**Method 1: Official Oracle JDK (Recommended)**

**1. Download Java 21:**
- Go to: https://www.oracle.com/java/technologies/downloads/
- Click "macOS" tab
- For Apple Silicon Macs (M1, M2, M3): Download "Arm 64 DMG Installer"
- For Intel Macs: Download "x64 DMG Installer"
- File size: ~180 MB, named like `jdk-21.0.x_macos-aarch64_bin.dmg`

**2. Install Java:**
- Double-click the downloaded DMG file
- Double-click the package installer inside
- Follow installation prompts
- Enter your Mac password when requested
- Installation path will be: `/Library/Java/JavaVirtualMachines/jdk-21.0.x.jdk/Contents/Home`

**3. Set Environment Variables:**

**For Zsh (default on newer Macs):**
- Open Terminal (Cmd + Space, type "Terminal")
- Edit shell profile: `nano ~/.zshrc`
- Add these lines at the end:
```bash
# Java 21 Environment Variables
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-21.0.x.jdk/Contents/Home
export PATH=$JAVA_HOME/bin:$PATH
```
- Save: Press `Ctrl + X`, then `Y`, then Enter
- Reload configuration: `source ~/.zshrc`

**For Bash (older Macs):**
- Edit bash profile: `nano ~/.bash_profile`
- Add the same Java environment variables
- Reload: `source ~/.bash_profile`

**4. Verify Installation:**
- Close and reopen Terminal
- Type: `java -version`
- Type: `javac -version`
- Both should show version 21.0.x

**Method 2: Using Homebrew (Alternative)**
```bash
# Install Homebrew if not already installed
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install Java 21
brew install openjdk@21

# Add to PATH
echo 'export PATH="/opt/homebrew/opt/openjdk@21/bin:$PATH"' >> ~/.zshrc
echo 'export JAVA_HOME="/opt/homebrew/opt/openjdk@21"' >> ~/.zshrc
source ~/.zshrc
```

#### **🐧 For Linux (Ubuntu/Debian):**

**Method 1: Using Package Manager**
```bash
# Update package list
sudo apt update

# Install OpenJDK 21
sudo apt install openjdk-21-jdk

# Set JAVA_HOME
echo 'export JAVA_HOME=/usr/lib/jvm/java-21-openjdk-amd64' >> ~/.bashrc
echo 'export PATH=$JAVA_HOME/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```

**Method 2: Manual Installation (Like Windows/Mac)**
- Download Linux x64 tar.gz from Oracle
- Extract to `/opt/java/`
- Set environment variables in `~/.bashrc`

#### **🔧 Troubleshooting Common Issues:**

**Problem: "'java' is not recognized as an internal or external command"**

**Solution for Windows:**
1. Verify JAVA_HOME is set correctly:
   - Open Command Prompt
   - Type: `echo %JAVA_HOME%`
   - Should show: `C:\Program Files\Java\jdk-21.0.x`
2. Check PATH contains Java:
   - Type: `echo %PATH%`
   - Should contain: `C:\Program Files\Java\jdk-21.0.x\bin`
3. If not set, repeat environment variable setup
4. **Restart computer** after setting variables

**Solution for Mac/Linux:**
1. Check environment variables:
   ```bash
   echo $JAVA_HOME
   echo $PATH
   ```
2. If empty, re-add to shell profile
3. Make sure you're editing the correct file (`.zshrc` vs `.bash_profile`)

**Problem: "Error: JAVA_HOME is not defined correctly"**
- Verify JAVA_HOME points to JDK directory, not JRE
- Should end with `/jdk-21.0.x` not `/jdk-21.0.x/bin`

**Problem: Multiple Java Versions Installed**

**For Windows:**
- Use `where java` to see all Java installations
- Ensure correct version is first in PATH

**For Mac:**
- Use `/usr/libexec/java_home -V` to list all versions
- Set JAVA_HOME to specific version: `export JAVA_HOME=$(/usr/libexec/java_home -v 21)`

**For Linux:**
- Use `update-alternatives --config java` to select default version

### **Step 2: Install IntelliJ IDEA and WebStrom Community Edition - Complete Setup**

#### **📥 Download and Installation (Detailed Steps):**

Both IntelliJ IDEA and WebStrom follows almost same setup

**1. Download IntelliJ IDEA:**
- Go to: https://www.jetbrains.com/idea/download/
- **Choose "Community Edition"** (100% free, perfect for learning)
- Download for your operating system:
  - Windows: `.exe` installer (~500 MB)
  - Mac: `.dmg` file (~500 MB)
  - Linux: `.tar.gz` archive (~500 MB)

**2. Install IntelliJ IDEA:**

**For Windows:**
- Double-click the downloaded `.exe` file
- Click "Next" on welcome screen
- Choose installation location (default: `C:\Users\[Username]\AppData\Local\JetBrains\Toolbox\apps\IDEA-C`)
- **Important Options to Check:**
  - ✅ "Create Desktop Shortcut"
  - ✅ "Update PATH variable" (add launchers dir to PATH)
  - ✅ "Update context menu" (Add "Open Folder as IntelliJ IDEA Project")
  - ✅ "Create associations" for .java, .groovy, .kt files
- Click "Install" and wait (3-5 minutes)
- Choose "Run IntelliJ IDEA Community Edition"

**For Mac:**
- Double-click the downloaded `.dmg` file
- Drag "IntelliJ IDEA CE" to Applications folder
- Eject the DMG file
- Open Applications → IntelliJ IDEA CE
- **First time:** Right-click → Open → Open (to bypass security warning)

**For Linux:**
```bash
# Extract the downloaded archive
tar -xzf ideaIC-*.tar.gz

# Move to /opt directory (recommended)
sudo mv idea-IC-* /opt/idea

# Create desktop shortcut
sudo ln -s /opt/idea/bin/idea.sh /usr/local/bin/idea

# Create .desktop file for GUI launcher
cat > ~/.local/share/applications/intellij-idea-community.desktop << EOF
[Desktop Entry]
Name=IntelliJ IDEA Community Edition
Comment=Java IDE
Exec=/opt/idea/bin/idea.sh
Icon=/opt/idea/bin/idea.png
Terminal=false
Type=Application
Categories=Development;IDE;
EOF
```

#### **⚙️ First-Time Setup and Configuration:**

**1. Initial Welcome Screen:**
- **"Do not import settings"** (since this is first installation)
- Click "OK"

**2. Choose UI Theme:**
- **Light Theme:** Traditional white background
- **Dark Theme (Recommended):** Easier on eyes, popular among developers
- **High Contrast:** For accessibility needs
- You can change this later in Settings

**3. Install Additional Plugins (Recommended):**

Click "Plugins" in welcome screen and install:
- ✅ **GitToolBox** - Enhanced Git integration
- ✅ **SonarLint** - Code quality analysis
- ✅ **Rainbow Brackets** - Colorful bracket matching
- ✅ **Material Theme UI** - Beautiful themes
- ✅ **Key Promoter X** - Learn keyboard shortcuts

**4. Configure Essential Settings:**

**File → Settings (Windows/Linux) or IntelliJ IDEA → Preferences (Mac):**

**Build Tools:**
- Build, Execution, Deployment → Build Tools → Maven
  - Maven home path: (auto-detected or set manually)
  - User settings file: default
  - Local repository: default

**Java Configuration:**
- Build, Execution, Deployment → Build Tools → Gradle → JVM
  - Gradle JVM: Use Project SDK (Java 21)

**Editor Settings:**
- Editor → Font
  - Font: JetBrains Mono (recommended) or Consolas
  - Size: 14 (adjust for your screen)
  - Line height: 1.2

**Code Style:**
- Editor → Code Style → Java
  - Scheme: Default or Google Java Style
  - Tab size: 4
  - Indent: 4
  - Continuation indent: 8

#### **🔧 Environment Variables for IntelliJ IDEA:**

**For Windows:**

Add to PATH if not automatically added:
- `C:\Users\[Username]\AppData\Local\JetBrains\Toolbox\apps\IDEA-C\bin`

Set IntelliJ-specific environment variables (optional):
```cmd
set IDEA_JDK=%JAVA_HOME%
set IDEA_VM_OPTIONS="-Xmx2048m -Xms512m"
```

**For Mac:**

Add to shell profile (`~/.zshrc` or `~/.bash_profile`):
```bash
# IntelliJ IDEA Command Line Launcher
export PATH="/Applications/IntelliJ IDEA CE.app/Contents/MacOS:$PATH"

# Optional: Set IntelliJ JVM options
export IDEA_VM_OPTIONS="-Xmx2048m -Xms512m -XX:+UseG1GC"
```

**For Linux:**

Add to `~/.bashrc` or `~/.zshrc`:
```bash
# IntelliJ IDEA
export IDEA_HOME=/opt/idea
export PATH=$IDEA_HOME/bin:$PATH

# Set JVM options for IntelliJ
export IDEA_VM_OPTIONS="-Xmx2048m -Xms512m"
```

#### **🚀 Create Your First Java Project:**

**1. Create New Project:**
- Click "New Project" on welcome screen
- Select "Java" from left sidebar
- **Project SDK:** Choose Java 21 (if not visible, click "Add SDK" → "JDK")
- **Project template:** Select "Command Line App"
- Click "Next"

**2. Project Configuration:**
- **Project location:** Choose a folder like `C:\Users\[Username]\IdeaProjects\FirstJavaApp`
- **Project name:** `FirstJavaApp`
- **Base package:** `com.learning.firstapp`
- Click "Finish"

**3. Test Your Setup:**

IntelliJ will create a basic `Main.java` file. Replace its content with:
```java
package com.learning.firstapp;

public class Main {
    public static void main(String[] args) {
        System.out.println("🎉 IntelliJ IDEA setup successful!");
        System.out.println("Java version: " + System.getProperty("java.version"));
        System.out.println("Ready for Day 1 training!");
    }
}
```

**4. Run Your First Program:**
- Right-click on `Main.java` → "Run 'Main.main()'"
- Or press `Ctrl + Shift + F10` (Windows/Linux) or `Cmd + Shift + R` (Mac)
- You should see output in the console at the bottom

#### **🎨 Alternative IDE: Visual Studio Code (Lightweight Option):**

**If IntelliJ feels too heavy, try VS Code:**

**1. Download VS Code:**
- Go to: https://code.visualstudio.com/
- Download for your OS
- Install with default settings

**2. Install Java Extension Pack:**
- Open VS Code
- Press `Ctrl + Shift + X` (Extensions)
- Search "Extension Pack for Java"
- Install the pack by Microsoft (includes 6 extensions)

**3. Configure Java:**
- Press `Ctrl + Shift + P` → "Java: Configure Classpath"
- Set Java Home to your Java 21 installation

#### **🛠️ Troubleshooting IntelliJ Issues:**

**Problem: "Project SDK is not defined"**

**Solution:**
1. File → Project Structure (Ctrl + Alt + Shift + S)
2. Project Settings → Project
3. Project SDK → Add SDK → JDK
4. Navigate to your Java 21 installation folder
5. Select and apply

**Problem: "Cannot resolve symbol" errors**

**Solution:**
1. File → Invalidate Caches and Restart
2. Or: Build → Rebuild Project
3. Check if SDK is properly configured

**Problem: IntelliJ runs slowly**

**Solution:**
1. Increase heap size: Help → Edit Custom VM Options
2. Add these lines:
   ```
   -Xms512m
   -Xmx2048m
   -XX:+UseG1GC
   ```
3. Restart IntelliJ

**Problem: Can't create new Java class**

**Solution:**
1. Ensure you're in a proper Java project
2. Right-click on `src` folder → New → Java Class
3. If no `src` folder, create new Java project

#### **📚 Essential IntelliJ Shortcuts to Learn:**

**Basic Navigation:**
- `Ctrl + N` (Cmd + N on Mac): Search for class
- `Ctrl + Shift + N`: Search for file
- `Ctrl + E`: Recent files
- `Alt + F1`: Locate file in Project view

**Code Editing:**
- `Ctrl + Space`: Code completion
- `Ctrl + Shift + Space`: Smart code completion
- `Alt + Enter`: Show intention actions
- `Ctrl + Alt + L`: Reformat code

**Running and Debugging:**
- `Ctrl + Shift + F10`: Run current file
- `Shift + F9`: Debug
- `F8`: Step over (debugging)
- `F7`: Step into (debugging)

**Refactoring:**
- `Shift + F6`: Rename
- `Ctrl + Alt + M`: Extract method
- `Ctrl + Alt + V`: Extract variable

### **Step 3: Install Node.js and Angular CLI - Complete Guide**

#### **📦 Install Node.js (Detailed Steps):**

**1. Download Node.js:**
- Go to: https://nodejs.org/
- **Choose LTS version** (Long Term Support) - currently Node.js 20.x.x
- Download for your operating system:
  - Windows: "Windows Installer (.msi)" 
  - Mac: "macOS Installer (.pkg)"
  - Linux: "Linux Binaries (x64)"

**2. Install Node.js:**

**For Windows:**
- Double-click the downloaded `.msi` file
- Click "Next" through the installer
- **Important:** Ensure "Add to PATH" is checked
- Accept license agreement
- Choose installation location (default is fine)
- **Check:** "Automatically install the necessary tools" (includes npm)
- Click "Install" and wait (2-3 minutes)
- Click "Finish"

**For Mac:**
- Double-click the downloaded `.pkg` file
- Follow installation wizard
- Enter Mac password when prompted
- Installation includes npm automatically

**For Linux:**
```bash
# Using package manager (Ubuntu/Debian)
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs

# Or using snap
sudo snap install node --classic
```

**3. Verify Node.js Installation:**
- **Close and reopen** Command Prompt/Terminal
- Type: `node --version` or `node -v`
- Expected output: `v20.x.x` (or newer)
- Type: `npm --version` or `npm -v`
- Expected output: `10.x.x` (or newer)

**4. Configure npm (Optional but Recommended):**
```bash
# Set npm registry to default (if needed)
npm config set registry https://registry.npmjs.org/

# Check npm configuration
npm config list

# Update npm to latest version
npm install -g npm@latest
```

#### **🅰️ Install Angular CLI 19 (Detailed Steps):**

**1. Install Angular CLI Globally:**
```bash
# Install specific Angular 19 version
npm install -g @angular/cli@19
```

**What this command does:**
- `npm`: Node Package Manager command
- `install`: Install a package
- `-g`: Install globally (available from anywhere on your system)
- `@angular/cli@19`: Angular Command Line Interface, version 19

**Installation Process:**
- Download size: ~50-70 MB
- Installation time: 2-5 minutes depending on internet speed
- You'll see progress indicators and package names scrolling

**2. Verify Angular CLI Installation:**
```bash
# Check Angular CLI version
ng version
```

**Expected Output:**
```
Angular CLI: 19.x.x
Node: 20.x.x
Package Manager: npm 10.x.x
OS: [your operating system]

Angular: 
... 

Package                      Version
------------------------------------------------------
@angular-devkit/architect    19.x.x
@angular-devkit/core         19.x.x
@angular-devkit/schematics   19.x.x
@schematics/angular          19.x.x
```

**3. Test Angular CLI:**
```bash
# Create a test project (optional)
ng new test-app --routing=false --style=css --skip-git
cd test-app
ng serve
```
- This creates a sample Angular app
- If successful, you'll see: "Compiled successfully"
- Open browser to `http://localhost:4200`
- You should see Angular welcome page
- Press `Ctrl + C` to stop the server
- You can delete the test-app folder after verification

#### **🔧 Environment Variables for Node.js:**

**For Windows:**
Node.js installer usually sets PATH automatically, but if needed:
1. Add to PATH: `C:\Program Files\nodejs\`
2. Add npm global modules: `C:\Users\[YourUsername]\AppData\Roaming\npm`

**For Mac/Linux:**
Add to your shell profile (`~/.zshrc` or `~/.bashrc`):
```bash
# Node.js Environment Variables
export NODE_HOME=/usr/local/bin/node
export PATH=$NODE_HOME:$PATH

# npm global modules
export PATH=$PATH:~/.npm-global/bin
```

#### **🚨 Troubleshooting Node.js & Angular Issues:**

**Problem: "'node' is not recognized as an internal or external command"**

**Solution:**
1. Restart Command Prompt/Terminal
2. Check if Node.js is in PATH:
   - Windows: `echo %PATH%` (should contain Node.js path)
   - Mac/Linux: `echo $PATH`
3. Reinstall Node.js if PATH issue persists

**Problem: "'ng' is not recognized as an internal or external command"**

**Solution:**
```bash
# Check if Angular CLI is installed globally
npm list -g @angular/cli

# If not installed, install it
npm install -g @angular/cli@19

# If installed but not in PATH, check npm global path
npm config get prefix

# Add npm global path to your system PATH
```

**Problem: Permission errors during npm install (Mac/Linux)**

**Solution:**
```bash
# Option 1: Use npx instead of global install
npx @angular/cli@19 new my-app

# Option 2: Fix npm permissions
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
export PATH=~/.npm-global/bin:$PATH
source ~/.bashrc  # or ~/.zshrc

# Option 3: Use Node Version Manager (nvm)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
nvm install node
```

**Problem: Angular CLI installation takes forever or fails**

**Solution:**
```bash
# Clear npm cache
npm cache clean --force

# Try with different registry
npm install -g @angular/cli@19 --registry https://registry.npmjs.org/

# Install with verbose logging to see what's happening
npm install -g @angular/cli@19 --verbose
```

**Problem: Version mismatch or multiple Angular CLI versions**

**Solution:**
```bash
# Uninstall all Angular CLI versions
npm uninstall -g @angular/cli
npm cache clean --force

# Reinstall specific version
npm install -g @angular/cli@19

# Verify
ng version
```

### **Step 4: Install Git and Create GitHub Account - Complete Guide**

#### **📥 Install Git (Detailed Steps):**

**For Windows:**
1. **Download Git:**
   - Go to: https://git-scm.com/downloads
   - Click "Windows" to download Git for Windows
   - File size: ~50 MB, named like `Git-2.42.x-64-bit.exe`

2. **Install Git:**
   - Double-click the installer
   - **Important Installation Options:**
     - ✅ "Use Git from the Windows Command Prompt" (adds Git to PATH)
     - ✅ "Use the OpenSSL library"
     - ✅ "Checkout Windows-style, commit Unix-style line endings"
     - ✅ "Use Windows' default console window"
   - Click "Next" through other options (defaults are fine)
   - Installation includes Git Bash (Unix-like terminal for Windows)

3. **Verify Installation:**
   - Open Command Prompt (Win + R, type `cmd`)
   - Type: `git --version`
   - Expected output: `git version 2.42.x.windows.x`

**For Mac:**

**Method 1: Official Installer**
1. Go to: https://git-scm.com/downloads
2. Click "macOS" to download
3. Double-click the downloaded `.dmg` file
4. Follow installation instructions

**Method 2: Using Homebrew (Recommended if you have it)**
```bash
# Install Homebrew if not already installed
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install Git
brew install git
```

**Method 3: Xcode Command Line Tools**
```bash
# This also installs Git
xcode-select --install
```

**For Linux (Ubuntu/Debian):**
```bash
# Update package list
sudo apt update

# Install Git
sudo apt install git

# Verify installation
git --version
```

#### **🐙 Create GitHub Account (Professional Setup):**

**1. Sign Up for GitHub:**
- Go to: https://github.com
- Click "Sign up" (green button, top right)

**2. Choose Username Wisely:**
**✅ Good Examples:**
- `johnsmith-dev`
- `priya-sharma`
- `rajesh-kumar-java`
- `jane-doe-fullstack`

**❌ Avoid:**
- `coolcoder123`
- `javaking2024`
- Numbers at the end randomly
- Very long usernames

**3. Account Details:**
- **Email:** Use your professional email address
- **Password:** Strong password with 12+ characters
- **Username:** As discussed above
- **Verification:** Complete the puzzle/verification

**4. Choose Plan:**
- Select "Free" plan (perfect for learning)
- You get unlimited public repositories
- Private repositories also included

#### **⚙️ Configure Git Environment (Critical Step):**

**1. Basic Configuration:**
```bash
# Set your name (use your real name)
git config --global user.name "Your Full Name"

# Set your email (same as GitHub account)
git config --global user.email "your.email@example.com"

# Set default branch name
git config --global init.defaultBranch main

# Set default editor (optional)
git config --global core.editor "code --wait"  # For VS Code
# OR
git config --global core.editor "notepad"      # For Windows Notepad
```

**2. Verify Configuration:**
```bash
# Check all settings
git config --list

# Check specific settings
git config user.name
git config user.email
```

**3. Advanced Configuration (Optional but Helpful):**
```bash
# Enable colored output
git config --global color.ui auto

# Set up aliases for common commands
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit

# Configure line ending handling
git config --global core.autocrlf true    # Windows
git config --global core.autocrlf input   # Mac/Linux

# Set up default pull behavior
git config --global pull.rebase false
```

#### **🔑 Set Up SSH Keys (Recommended for Security):**

**1. Generate SSH Key:**
```bash
# Generate new SSH key
ssh-keygen -t ed25519 -C "your.email@example.com"

# When prompted:
# - Press Enter for default file location
# - Enter a secure passphrase (optional but recommended)
```

**2. Add SSH Key to SSH Agent:**
```bash
# Start SSH agent
eval "$(ssh-agent -s)"

# Add your SSH key
ssh-add ~/.ssh/id_ed25519
```

**3. Add SSH Key to GitHub:**
```bash
# Copy SSH key to clipboard
# On Mac:
pbcopy < ~/.ssh/id_ed25519.pub

# On Windows (Git Bash):
clip < ~/.ssh/id_ed25519.pub

# On Linux:
cat ~/.ssh/id_ed25519.pub
# Then manually copy the output
```

**4. Add to GitHub:**
- Go to GitHub → Settings → SSH and GPG keys
- Click "New SSH key"
- Title: "My Development Machine" (or descriptive name)
- Paste the key in "Key" field
- Click "Add SSH key"

**5. Test SSH Connection:**
```bash
ssh -T git@github.com
# Expected output: "Hi [username]! You've successfully authenticated..."
```

#### **🔧 Environment Variables for Git:**

**For Windows:**
Git installer usually sets PATH automatically. If needed:
- Add to PATH: `C:\Program Files\Git\cmd`
- For Git Bash: `C:\Program Files\Git\bin`

**For Mac/Linux:**
Add to your shell profile if not automatically added:
```bash
# Usually not needed, but if required:
echo 'export PATH="/usr/local/bin:$PATH"' >> ~/.zshrc  # or ~/.bashrc
source ~/.zshrc
```

#### **🚨 Troubleshooting Git Issues:**

**Problem: "'git' is not recognized as an internal or external command"**

**Solution for Windows:**
1. Check if Git is installed: Look for "Git Bash" in Start Menu
2. Add Git to PATH manually:
   - System Properties → Environment Variables
   - Add `C:\Program Files\Git\cmd` to PATH
3. Restart Command Prompt
4. If still not working, reinstall Git with "Use Git from Command Prompt" option

**Problem: Permission denied (publickey) when pushing to GitHub**

**Solution:**
1. Use HTTPS instead of SSH initially:
   ```bash
   git remote set-url origin https://github.com/username/repository.git
   ```
2. Or set up SSH keys properly (see SSH setup above)

**Problem: Git asks for username/password every time**

**Solution:**
```bash
# Store credentials (Windows)
git config --global credential.helper manager-core

# Store credentials (Mac)
git config --global credential.helper osxkeychain

# Store credentials (Linux)
git config --global credential.helper store
```

**Problem: Line ending issues (files showing as modified when unchanged)**

**Solution:**
```bash
# For Windows
git config --global core.autocrlf true

# For Mac/Linux  
git config --global core.autocrlf input

# Reset repository
git rm --cached -r .
git reset --hard
```

### **Step 5: Install Postman**

1. Go to: https://www.postman.com/downloads/
2. Download for your operating system
3. Install and create free account
4. You'll use this to test your APIs

### **Step 6: Create Your First Repository**

**In GitHub:**
1. Click "New Repository" (green button)
2. Name it: `internship-projects`
3. Check "Add a README file"
4. Click "Create repository"

**Congratulations! You now have:**
✅ Complete development environment
✅ Professional GitHub presence
✅ All tools needed for 30-day journey

---

## 🎯 **Practice Tasks & Verification**

### **Complete Environment Verification Checklist:**

#### **Step 1: Java Environment Verification**
```bash
# Check Java version (should show 21.x.x)
java -version
# Expected output: openjdk version "21.0.x" 2024-xx-xx LTS

# Check Java compiler
javac -version
# Expected output: javac 21.0.x

# Verify JAVA_HOME environment variable is set correctly
echo $JAVA_HOME        # Mac/Linux
echo %JAVA_HOME%       # Windows Command Prompt  
echo $env:JAVA_HOME    # Windows PowerShell

# Expected output: Your Java 21 installation path
# Example: /usr/lib/jvm/java-21-openjdk (Linux)
#          /Library/Java/JavaVirtualMachines/jdk-21.jdk/Contents/Home (Mac)
#          C:\Program Files\Java\jdk-21 (Windows)
```

**Java Troubleshooting:**
- **"java: command not found":** Java not in PATH - restart terminal and re-check PATH setup
- **Wrong version shown:** Multiple Java versions installed, ensure JAVA_HOME points to Java 21
- **JAVA_HOME not set:** Run environment variable setup commands again
- **Permission issues:** Run terminal as administrator (Windows) or use sudo (Mac/Linux)

#### **Step 2: Node.js & Angular Verification**
```bash
# Check Node.js version (should be 20.x LTS or newer)
node -v
# Expected: v20.11.x or newer

# Check npm version 
npm -v
# Expected: 10.2.x or newer

# Verify npm global installation directory
npm config get prefix
# Should show global npm directory

# Check if Angular CLI is installed globally
ng version
# Expected output should include:
# Angular CLI: 19.x.x
# Node: 20.x.x
# Package Manager: npm 10.x.x

# If Angular CLI not found, install it:
npm install -g @angular/cli@latest
```

**Node.js/Angular Troubleshooting:**
- **"node: command not found":** Restart terminal, if still fails reinstall Node.js
- **"ng: command not found":** Install Angular CLI globally: `npm install -g @angular/cli@latest`
- **Permission errors on Mac/Linux:** Use `sudo npm install -g @angular/cli@latest`
- **Slow npm operations:** Clear cache: `npm cache clean --force`

#### **Step 3: Git Configuration Verification**
```bash
# Check Git version (should be 2.30+ for best compatibility)
git --version
# Expected: git version 2.x.x

# Verify Git is configured with your details
git config --global --list
# Should display:
# user.name=Your Full Name
# user.email=your.email@example.com

# Check specific configurations
git config --global user.name
git config --global user.email

# Test SSH connection to GitHub (if you set up SSH keys)
ssh -T git@github.com
# Expected: "Hi username! You've successfully authenticated..."
```

**Git Troubleshooting:**
- **No user name/email:** Run the git config commands from installation section
- **SSH authentication fails:** Use HTTPS instead or regenerate SSH keys
- **Git commands fail:** Ensure Git is added to PATH during installation

#### **Step 4: Complete Development Environment Test**
```bash
# Create a test workspace to verify everything works together
mkdir ~/development-test
cd ~/development-test

# Test Java compilation and execution
echo 'public class EnvironmentTest { 
    public static void main(String[] args) { 
        System.out.println("✅ Java 21 is working perfectly!"); 
        System.out.println("Java version: " + System.getProperty("java.version"));
    } 
}' > EnvironmentTest.java

# Compile and run Java program
javac EnvironmentTest.java
java EnvironmentTest

# Expected output:
# ✅ Java 21 is working perfectly!
# Java version: 21.0.x

# Test Angular CLI functionality  
ng new test-app --routing=true --style=css --skip-install
cd test-app

# Install dependencies
npm install

# Expected: No errors, all packages installed successfully

# Clean up test files
cd ../..
rm -rf ~/development-test

echo "🎉 Environment verification complete!"
```

#### **Step 5: Environment Variables Summary Check**

**For Mac/Linux users - run this verification script:**
```bash
echo "=================================="
echo "   DEVELOPMENT ENVIRONMENT CHECK  "
echo "=================================="
echo "JAVA_HOME: $JAVA_HOME"
echo "Java Version: $(java -version 2>&1 | head -n 1)"
echo "Node.js Version: $(node -v)"
echo "npm Version: $(npm -v)" 
echo "Angular CLI: $(ng version --help > /dev/null 2>&1 && echo 'Installed' || echo 'NOT FOUND')"
echo "Git Version: $(git --version)"
echo "=================================="
echo "PATH includes Java: $(echo $PATH | grep -q java && echo '✅ Yes' || echo '❌ No')"
echo "PATH includes Node: $(echo $PATH | grep -q node && echo '✅ Yes' || echo '❌ No')"
echo "=================================="
```

**For Windows users - run in Command Prompt:**
```cmd
echo ==================================
echo    DEVELOPMENT ENVIRONMENT CHECK  
echo ==================================
echo JAVA_HOME: %JAVA_HOME%
java -version
node -v
npm -v
ng version
git --version
echo ==================================
```

**For Windows PowerShell users:**
```powershell
Write-Host "=================================="
Write-Host "   DEVELOPMENT ENVIRONMENT CHECK  " 
Write-Host "=================================="
Write-Host "JAVA_HOME: $env:JAVA_HOME"
Write-Host "Java Version: $((java -version 2>&1)[0])"
Write-Host "Node.js Version: $(node -v)"
Write-Host "npm Version: $(npm -v)"
Write-Host "Git Version: $(git --version)"
Write-Host "=================================="
```

---

## 🔧 **Common Installation Issues & Solutions**

### **Java Installation Issues:**

**Problem:** "java: command not found" or "javac: command not found"
**Solution:**
```bash
# Check if Java is actually installed
ls /usr/lib/jvm/          # Linux
ls /Library/Java/JavaVirtualMachines/  # Mac
dir "C:\Program Files\Java"           # Windows

# If Java is installed but not in PATH, add it manually:
# Linux/Mac - Add to ~/.bashrc or ~/.zshrc:
export JAVA_HOME=/path/to/java-21
export PATH=$JAVA_HOME/bin:$PATH

# Windows - Add to System Environment Variables:
# JAVA_HOME=C:\Program Files\Java\jdk-21
# PATH=%JAVA_HOME%\bin;%PATH%

# Restart terminal after changes
```

**Problem:** JAVA_HOME shows wrong version or empty
**Solution:**
```bash
# Find Java installation path:
which java           # Mac/Linux
where java          # Windows

# Set JAVA_HOME correctly:
# Mac example:
export JAVA_HOME=$(/usr/libexec/java_home -v 21)

# Linux example:  
export JAVA_HOME=/usr/lib/jvm/java-21-openjdk

# Windows example:
set JAVA_HOME=C:\Program Files\Java\jdk-21

# Make permanent by adding to profile files
```

### **Node.js Installation Issues:**

**Problem:** "node: command not found" after installation
**Solution:**
```bash
# Restart terminal first, then check:
node -v

# If still not found, reinstall Node.js:
# 1. Download from https://nodejs.org (LTS version)
# 2. Run installer with admin privileges
# 3. Restart computer
# 4. Open new terminal and test
```

**Problem:** npm permission errors (Mac/Linux)
**Solution:**
```bash
# Option 1: Use sudo for global installs
sudo npm install -g @angular/cli@latest

# Option 2: Change npm global directory (recommended)
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
# Add to ~/.bashrc or ~/.zshrc:
export PATH=~/.npm-global/bin:$PATH
# Restart terminal
```

**Problem:** Angular CLI installation fails
**Solution:**
```bash
# Clear npm cache
npm cache clean --force

# Update npm to latest version
npm install -g npm@latest

# Install Angular CLI
npm install -g @angular/cli@latest

# If still fails, try specific version:
npm install -g @angular/cli@19.0.0
```

### **Git Installation Issues:**

**Problem:** Git commands not working or not found
**Solution:**
```bash
# Verify installation:
git --version

# If not found, reinstall Git:
# Windows: Download from https://git-scm.com/download/win
# Mac: Install Xcode Command Line Tools: xcode-select --install
# Linux: sudo apt-get install git (Ubuntu/Debian)
```

**Problem:** GitHub authentication issues
**Solution:**
```bash
# For HTTPS (easier for beginners):
git config --global credential.helper store
# Enter username/password when prompted

# For SSH (more secure):
ssh-keygen -t ed25519 -C "your.email@example.com"
# Add public key to GitHub account
# Test: ssh -T git@github.com
```

### **IDE Installation Issues:**

**Problem:** IntelliJ IDEA doesn't start or Java not detected
**Solution:**
```bash
# Ensure JAVA_HOME is set correctly
echo $JAVA_HOME

# Start IntelliJ from command line to see errors:
# Mac: /Applications/IntelliJ\ IDEA\ CE.app/Contents/bin/idea.sh
# Windows: "C:\Users\[username]\AppData\Local\JetBrains\Toolbox\apps\IDEA-C\ch-0\[version]\bin\idea64.exe"

# Configure Java SDK in IntelliJ:
# File → Project Structure → Platform Settings → SDKs
# Add JDK and point to your Java 21 installation
```

**Problem:** VS Code extensions not working
**Solution:**
```bash
# Restart VS Code
# Check if Java extension pack is installed:
# Extensions → Search "Extension Pack for Java" → Install

# Reload window: Ctrl+Shift+P → "Developer: Reload Window"
```

---

### **Platform-Specific Environment Variable Setup**

#### **Windows Environment Variables (Permanent Setup):**

**Using System Properties GUI:**
1. Right-click "This PC" → Properties
2. Advanced system settings → Environment Variables
3. System Variables → New:
   - Variable name: `JAVA_HOME`
   - Variable value: `C:\Program Files\Java\jdk-21`
4. Find `Path` in System Variables → Edit → New:
   - Add: `%JAVA_HOME%\bin`
   - Add: `C:\Program Files\nodejs`
5. Click OK on all dialogs
6. Restart Command Prompt/PowerShell

**Using Command Line (PowerShell as Admin):**
```powershell
# Set JAVA_HOME permanently
[Environment]::SetEnvironmentVariable("JAVA_HOME", "C:\Program Files\Java\jdk-21", "Machine")

# Add Java to PATH permanently
$path = [Environment]::GetEnvironmentVariable("PATH", "Machine")
$newPath = $path + ";C:\Program Files\Java\jdk-21\bin"
[Environment]::SetEnvironmentVariable("PATH", $newPath, "Machine")

# Restart PowerShell to see changes
```

#### **Mac Environment Variables (Permanent Setup):**

**For Zsh (default on macOS Catalina+):**
```bash
# Edit profile file
nano ~/.zshrc

# Add these lines:
export JAVA_HOME=$(/usr/libexec/java_home -v 21)
export PATH=$JAVA_HOME/bin:$PATH
export PATH=/usr/local/bin:$PATH

# Save (Ctrl+X, Y, Enter) and reload:
source ~/.zshrc
```

**For Bash:**
```bash
# Edit profile file  
nano ~/.bash_profile

# Add same lines as above, then:
source ~/.bash_profile
```

#### **Linux Environment Variables (Permanent Setup):**

**For Ubuntu/Debian:**
```bash
# Edit profile file
nano ~/.bashrc

# Add these lines:
export JAVA_HOME=/usr/lib/jvm/java-21-openjdk
export PATH=$JAVA_HOME/bin:$PATH
export PATH=/usr/local/bin:$PATH

# Save and reload:
source ~/.bashrc

# Make system-wide (optional):
sudo nano /etc/environment
# Add: JAVA_HOME="/usr/lib/jvm/java-21-openjdk"
```

### **Final Verification Script**

**Save this as `verify-setup.sh` (Mac/Linux) or `verify-setup.bat` (Windows):**

**Mac/Linux version:**
```bash
#!/bin/bash
echo "🔍 Verifying Complete Development Environment..."
echo "=============================================="

# Java check
if command -v java &> /dev/null; then
    echo "✅ Java: $(java -version 2>&1 | head -n 1)"
    echo "📁 JAVA_HOME: $JAVA_HOME"
else
    echo "❌ Java not found in PATH"
fi

# Node.js check  
if command -v node &> /dev/null; then
    echo "✅ Node.js: $(node -v)"
else
    echo "❌ Node.js not found"
fi

# npm check
if command -v npm &> /dev/null; then
    echo "✅ npm: $(npm -v)"
else
    echo "❌ npm not found"
fi

# Angular CLI check
if command -v ng &> /dev/null; then
    echo "✅ Angular CLI: Installed"
else
    echo "❌ Angular CLI not found - run: npm install -g @angular/cli@latest"
fi

# Git check
if command -v git &> /dev/null; then
    echo "✅ Git: $(git --version)"
    echo "👤 Git User: $(git config --global user.name) <$(git config --global user.email)>"
else
    echo "❌ Git not found"
fi

echo "=============================================="
echo "🎯 If you see any ❌ symbols, review the installation steps for that tool."
echo "✅ All green? You're ready for Day 2!"
```

**Windows version (verify-setup.bat):**
```batch
@echo off
echo 🔍 Verifying Complete Development Environment...
echo ==============================================

REM Java check
java -version >nul 2>&1
if %ERRORLEVEL% == 0 (
    echo ✅ Java: Found
    echo 📁 JAVA_HOME: %JAVA_HOME%
) else (
    echo ❌ Java not found in PATH
)

REM Node.js check
node -v >nul 2>&1
if %ERRORLEVEL% == 0 (
    echo ✅ Node.js: Found
) else (
    echo ❌ Node.js not found
)

REM npm check
npm -v >nul 2>&1
if %ERRORLEVEL% == 0 (
    echo ✅ npm: Found
) else (
    echo ❌ npm not found
)

REM Angular CLI check
ng version >nul 2>&1
if %ERRORLEVEL% == 0 (
    echo ✅ Angular CLI: Found
) else (
    echo ❌ Angular CLI not found - run: npm install -g @angular/cli@latest
)

REM Git check
git --version >nul 2>&1
if %ERRORLEVEL% == 0 (
    echo ✅ Git: Found
) else (
    echo ❌ Git not found
)

echo ==============================================
echo 🎯 If you see any ❌ symbols, review the installation steps for that tool.
echo ✅ All good? You're ready for Day 2!
pause
```


1. **Log into GitHub**
2. **Create new repository:**
   - Name: `day1-practice`
   - Description: "My first day of full-stack development journey"
   - Public repository
   - Initialize with README
3. **Edit README.md file:**
   ```markdown
   # Day 1 - My Full-Stack Journey Begins!
   
   ## What I Learned Today
   - Full-stack development concepts
   - Technology stack overview
   - Environment setup
   
   ## Tools I Installed
   - Java 21
   - IntelliJ IDEA
   - Node.js & Angular CLI 19
   - Git & GitHub
   - Postman
   
   ## What's Next
   Tomorrow I'll learn Java 21 features and build my first API!
   
   ## My Goal
   Build two complete applications in 30 days and become a full-stack developer!
   ```

4. **Commit changes** with message: "Day 1: Environment setup complete"

---

## 🎯 **Practice Exercise: Create Your First Repository**

Now that your environment is properly set up and verified, let's practice using your new tools together!

### **Exercise 1: GitHub Repository Creation**

1. **Log into GitHub**
   - Go to https://github.com
   - Sign in with your account

2. **Create new repository:**
   - Click the "+" icon → "New repository"
   - Repository name: `day1-practice`
   - Description: "My first day of full-stack development journey"
   - Make it **Public** (so you can showcase your learning!)
   - ✅ Check "Add a README file"
   - Click "Create repository"

3. **Edit your README.md file online:**
   - Click on README.md in your new repository
   - Click the pencil icon (Edit this file)
   - Replace the content with:

```markdown
# Day 1 - My Full-Stack Journey Begins! 🚀

## What I Learned Today
- ✅ Full-stack development concepts
- ✅ Modern technology stack: Java 21 + Spring Boot 3.4 + Angular 19
- ✅ Complete development environment setup
- ✅ Git, GitHub, and version control basics

## Tools I Successfully Installed & Configured
- ☕ **Java 21** - Latest LTS with modern features
- 🧠 **IntelliJ IDEA** - Professional Java IDE  
- 🌐 **Node.js 20.x LTS** - JavaScript runtime
- 🅰️ **Angular CLI 19** - Modern frontend framework
- 🔧 **Git & GitHub** - Version control and collaboration
- 🔍 **Postman** - API testing and development

## Environment Variables Configured
- `JAVA_HOME` → Points to Java 21 installation
- `PATH` → Includes Java, Node.js, and Git executables
- Git global configuration with my name and email

## My First Commands That Worked!
```bash
java -version        # ✅ Shows Java 21.x.x
node -v             # ✅ Shows Node 20.x.x  
npm -v              # ✅ Shows npm 10.x.x
ng version          # ✅ Shows Angular CLI 19.x.x
git --version       # ✅ Shows Git 2.x.x
```

## Useful Commands Reference
```bash
# Java compilation and execution
javac MyProgram.java && java MyProgram

# Angular project creation
ng new my-app --routing --style=css

# Git workflow
git add . && git commit -m "message" && git push
```

---
**Updated:** Day 1 - Environment Setup Complete ✅  
**Next Update:** Day 2 - Java 21 Features & HTTP Basics
```

4. **Commit your changes:**
   - Scroll down to "Commit changes"
   - Commit message: `Day 1: Environment setup complete - Ready for Java 21!`
   - Description: `Added development environment details and learning objectives`
   - Click "Commit changes"

### **Exercise 2: Local Development Test**

Now let's test your local environment by creating a simple Java program:

1. **Create a practice directory:**
```bash
# Create and navigate to practice folder
mkdir ~/day1-practice
cd ~/day1-practice
```

2. **Create your first Java 21 program:**
```bash
# Create a modern Java file showcasing Java 21 features
cat > Welcome.java << 'EOF'
public class Welcome {
    // Using Text Blocks (Java 15+) and modern syntax
    private static final String WELCOME_MESSAGE = """
            🎉 Welcome to Full-Stack Development with Java 21!
            
            ✅ Your environment is working perfectly!
            
            Technology Stack Ready:
            - Java 21 (Latest LTS)
            - Spring Boot 3.4.x 
            - Angular 19
            - Git & GitHub
            
            You're ready to build amazing applications! 🚀
            """;
    
    public static void main(String[] args) {
        System.out.println(WELCOME_MESSAGE);
        
        // Java 21 feature: Simple pattern matching
        String javaVersion = System.getProperty("java.version");
        System.out.println("Running on Java: " + javaVersion);
        
        // Verify we're on Java 21
        if (javaVersion.startsWith("21")) {
            System.out.println("✅ Perfect! You're using Java 21 - the latest LTS!");
        } else {
            System.out.println("⚠️  Consider upgrading to Java 21 for the best experience.");
        }
        
        System.out.println("\n🎯 Tomorrow we'll explore more Java 21 features!");
    }
}
EOF
```

3. **Compile and run your program:**
```bash
# Compile the Java program
javac Welcome.java

# Run the compiled program  
java Welcome

# Expected output: Welcome message with Java version confirmation
```

4. **Initialize Git repository and connect to GitHub:**
```bash
# Initialize local Git repository
git init

# Add your files
git add .

# Commit your first local changes
git commit -m "Day 1: First Java 21 program - environment verification"

# Connect to your GitHub repository (replace 'yourusername' with your actual GitHub username)
git remote add origin https://github.com/yourusername/day1-practice.git

# Push your code to GitHub
git branch -M main
git push -u origin main
```

### **Exercise 3: Angular CLI Quick Test**

Let's verify Angular CLI is working:

```bash
# Create a new directory for Angular test
mkdir ~/angular-test
cd ~/angular-test

# Create a minimal Angular app (this will take a few minutes)
ng new hello-angular --routing=false --style=css --skip-install

# Navigate into the project
cd hello-angular

# Install dependencies
npm install

# Start the development server (optional - you can skip this for now)
# ng serve
# Open http://localhost:4200 in browser to see "Hello Angular!"

# Clean up test project
cd ../..
rm -rf ~/angular-test
```

### **Exercise 4: Postman Setup Verification**

1. **Open Postman**
2. **Create a new workspace:**
   - Name: "Full-Stack Learning"
   - Description: "API testing for my 30-day journey"
3. **Create a simple GET request:**
   - URL: `https://jsonplaceholder.typicode.com/posts/1`
   - Click Send
   - You should see JSON response data
4. **Save the request as:** "Test API Call - Day 1"

---

### **Q: I'm completely new to programming. Will this be too difficult?**
**A:** Not at all! This course is designed for beginners. We start with basic concepts and build up gradually. Many successful developers started with zero experience.

### **Q: Why these specific technologies?**
**A:** 
- **Java 21:** Latest version with modern features, highly demanded in job market
- **Spring Boot:** Industry standard, used by 70% of Java applications
- **Angular 19:** Latest version with cutting-edge features, used by major companies
- This combination gets you hired faster!

### **Q: What if I get stuck during installation?**
**A:** Common solutions:
- Restart your computer after installations
- Run installers as Administrator (Windows) or with sudo (Mac/Linux)
- Check system requirements match your computer
- Ask for help in our community channels

### **Q: What happens after 30 days?**
**A:** You'll have:
- 2 complete applications in your portfolio
- Solid foundation in full-stack development
- Option to join 45-day advanced program for industry-ready skills
- Confidence to apply for developer positions

---

## 📚 **Additional Learning Resources**

### **If You Want to Learn More:**

**Java Basics:**
- Oracle Java Tutorials: https://docs.oracle.com/javase/tutorial/
- "Java: The Complete Reference" by Herbert Schildt
- YouTube: "Programming with Mosh - Java Tutorial"

**Web Development Concepts:**
- MDN Web Docs: https://developer.mozilla.org/
- FreeCodeCamp: https://www.freecodecamp.org/
- W3Schools: https://www.w3schools.com/

**Angular Learning:**
- Official Angular Tutorial: https://angular.io/tutorial
- Angular University courses
- YouTube: "Angular Tutorial" by Traversy Media

**Spring Boot:**
- Spring Boot Official Guides: https://spring.io/guides
- Baeldung Spring Boot tutorials: https://www.baeldung.com/
- "Spring Boot in Action" book

---

## 🎉 **Congratulations!**

You've completed Day 1! You now understand:
- ✅ What full-stack development is and why it's exciting
- ✅ The technology stack we'll master together
- ✅ How to set up your development environment

**Remember:** Every expert was once a beginner. You're on an amazing journey that will change your career prospects. Stay curious, ask questions, and enjoy the process! 🚀

---

**Need Help?**
- Review this guide as many times as needed
- Ask questions during tomorrow's session
- Remember: There's no such thing as a stupid question!

**See you tomorrow for Day 2** 🎯
