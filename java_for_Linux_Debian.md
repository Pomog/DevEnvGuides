### 1. Update Package Index
```bash
sudo apt update
```

### 2. Verify JAVA Installation
```bash
java -version
```
for a Debian-based system
```bash
dpkg -l | grep openjdk
```
```bash
ls /usr/lib/jvm
```

### 3. To see all available editions of OpenJDK, search the apt libraries
The headless versions (-headless) provide non-GUI libraries only 
```bash
apt-cache search openjdk
```

### 4. Install JDK.
The Java Development Kit (JDK) includes the JRE and adds development tools like javac (the compiler), javadoc (for generating documentation), and other tools for developing Java applications.
```bash
sudo apt install openjdk-17-jdk
```

### 5. Uninstall OpenJDK
```bash
apt list --installed | grep openjdk
sudo apt remove openjdk-11-jre-headless openjdk-11-jre
sudo apt autoremove
```

### 5. Set the Environment Variables for Java
Edit the .bashrc file (for individual users) in your home directory and add the following definitions to the end of the file.
To set these values for all system users, add the following changes to /etc/environment
# changing /etc/environment can lead to LOGIN LOOP
# on LOGIN LOOP use different TTY (Ctrl-Alt-F3) and remove these Environment Variables
# /etc/environment used for system-wide environment variables, and the shell starts up before some of the GUI or graphical login tools can load. Incorrect paths or commands in this file can prevent the system from properly launching the graphical environment, resulting in a login loop.
```bash
export JAVA_HOME=$(dirname $(dirname $(readlink -f $(which java))))
export PATH=$PATH:$JAVA_HOME/bin
```

Source the .bashrc file to apply the changes.
```bash
source ~/.bashrc
echo $JAVA_HOME
echo $PATH
```

### 6. Write a Simple Program
```bash
vim HelloWorld.java
```

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

### 7. Compile the Java Code
Compilation turns the .java file into a .class file, which the JVM can execute.
```bash
javac HelloWorld.java
```

### 8. Run the Java Program
```bash
java HelloWorld
```

[The Gnu song](https://www.youtube.com/watch?v=j53z6RfFb7U&ab_channel=PeterMc)
