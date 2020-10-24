# Java-Ubuntu20.04

Install Java with Apt on Ubuntu 20.04

<h3 id="introduction">Introduction</h3>
<p>Java and the JVM (Java’s virtual machine) are required for many kinds of software, including <a href="http://tomcat.apache.org/">Tomcat</a>, <a href="https://www.eclipse.org/jetty/">Jetty</a>, <a href="https://javaee.github.io/glassfish/">Glassfish</a>, <a href="http://cassandra.apache.org/">Cassandra</a> and <a href="https://jenkins.io/">Jenkins</a>.</p>


<p>In this guide, you will install various versions of the Java Runtime Environment (JRE) and the Java Developer Kit (JDK) using <code>apt</code> . 
  You’ll install OpenJDK as well as the official JDK from Oracle.
  You’ll then select the version you wish to use for your projects. 
  When you’re finished, you’ll be able to use the JDK to develop software or use the Java Runtime to run software.</p>

<a name="prerequisites" data-unique="prerequisites"></a><a name="prerequisites" data-unique="prerequisites"></a><h2 id="prerequisites">Prerequisites</h2>

<p>To follow this tutorial, you will need:</p>

<ul>
<li>One Ubuntu 20.04 server set up by following the <a href="https://github.com/dogiparthy85/ubuntu20.04-server"> the Ubuntu 20.04 initial server setup guide</a> tutorial,  including a sudo non-root user and a firewall.</li>
</ul>

<a name="installing-the-default-jrejdk" data-unique="installing-the-default-jrejdk"></a><a name="installing-the-default-jrejdk" data-unique="installing-the-default-jrejdk"></a><h2 id="installing-the-default-jre-jdk">Installing the Default JRE/JDK</h2>

<p>The easiest option for installing Java is to use the version packaged with Ubuntu. 
  By default, Ubuntu 20.04 includes Open JDK 11,  which is an open-source variant of the JRE and JDK.</p>

<p>To install this version, first update the package index:</p>
<pre class="code-pre command prefixed"><code><ul class="prefixed"><li class="line" data-prefix="$">sudo apt update
</li></ul></code></pre>

<p>Next, check if Java is already installed:</p>
<pre class="code-pre command prefixed"><code><ul class="prefixed"><li class="line" data-prefix="$">java -version
</li></ul></code></pre>

<p>If Java is not currently installed, you’ll see the following output:</p>
<pre class="code-pre "><code><div class="secondary-code-label " title="Output">Output</div>Command 'java' not found, but can be installed with:

sudo apt install default-jre              # version 2:1.11-72, or
sudo apt install openjdk-11-jre-headless  # version 11.0.7+10-3ubuntu1
sudo apt install openjdk-13-jre-headless  # version 13.0.3+3-1ubuntu2
sudo apt install openjdk-14-jre-headless  # version 14.0.1+7-1ubuntu1
sudo apt install openjdk-8-jre-headless   # version 8u252-b09-1ubuntu1
</code></pre>

<p>Execute the following command to install the default Java Runtime Environment (JRE), which will install the JRE from OpenJDK 11:</p>
<pre class="code-pre command prefixed"><code><ul class="prefixed"><li class="line" data-prefix="$">sudo apt install default-jre
</li></ul></code></pre>

<p>The JRE will allow you to run almost all Java software.</p>

<p>Verify the installation with:</p>

<pre class="code-pre command prefixed"><code><ul class="prefixed"><li class="line" data-prefix="$">java -version
</li></ul></code></pre>

<p>You’ll see the following output:</p>

<pre class="code-pre "><code><div class="secondary-code-label " title="Output">Output</div>openjdk version "<span class="highlight">11.0.8</span>" 2020-07-14
OpenJDK Runtime Environment (build <span class="highlight">11.0.8+10</span>-post-Ubuntu-3ubuntu1)
OpenJDK 64-Bit Server VM (build <span class="highlight">11.0.8+10</span>-post-Ubuntu-3ubuntu1, mixed mode, sharing)
</code></pre>

<p>You may need the Java Development Kit (JDK) in addition to the JRE in order to compile and run some specific Java-based software. To install the JDK, execute the following command, which will also install the JRE:</p>

<pre class="code-pre command prefixed"><code><ul class="prefixed"><li class="line" data-prefix="$">sudo apt install default-jdk
</li></ul></code></pre>

<p>Verify that the JDK is installed by checking the version of <code>javac</code>, the Java compiler:</p>

<pre class="code-pre command prefixed"><code><ul class="prefixed"><li class="line" data-prefix="$">javac -version
</li></ul></code></pre>

<p>You’ll see the following output:</p>
<pre class="code-pre "><code><div class="secondary-code-label " title="Output">Output</div>javac <span class="highlight">11.0.8</span>
</code></pre>

<p>Next, let’s look at how to install Oracle’s official JDK and JRE.</p>

<a name="installing-oracle-jdk-11" data-unique="installing-oracle-jdk-11"></a><a name="installing-oracle-jdk-11" data-unique="installing-oracle-jdk-11"></a><h2 id="installing-oracle-jdk-11">Installing Oracle JDK 11</h2>

<p>Oracle’s licensing agreement for Java doesn’t allow automatic installation through package managers. To install the Oracle JDK, which is the official version distributed by Oracle, you must create an Oracle account and manually download the JDK to add a new package repository for the version you’d like to use. Then you can use <code>apt</code> to install it with help from a <a href="https://launchpad.net/%7Elinuxuprising/+archive/ubuntu/java/+packages">third party installation script</a>.</p>

<p>The version of Oracle’s JDK you’ll need to download must match version of the installer script. To find out which version you need, visit the <a href="https://launchpad.net/%7Elinuxuprising/+archive/ubuntu/java/+packages"><code>oracle-java11-installer</code></a> page.</p>

<p>Locate the package for <strong>Focal</strong>, as shown in the following figure:</p>

<p class="growable"><img src="https://github.com/dogiparthy85/Java-Ubuntu20.04/blob/main/javapackage.png" alt="Installer package for Ubuntu 2.04"></p>

<p>In this image, the version of the script is <code>11.0.9</code>.  In this case, you’ll need Oracle JDK 11.0.9.  You don’t need to download anything from this page; you’ll download the installation script through <code>apt</code> shortly.</p>

<p>Then visit the <a href="https://www.oracle.com/technetwork/java/javase/downloads/index.html">Downloads page</a> and locate the version that matches the one you need.</p>

<p class="growable"><img src="https://raw.githubusercontent.com/dogiparthy85/Java-Ubuntu20.04/main/t50afne%5B1%5D.png" alt="Oracle Java 11"></p>

<p>Click the <strong>JDK Download</strong> button and you’ll be taken to a screen that shows the versions available.  Click the <code>.tar.gz</code> package for Linux.</p>

<p class="growable"><img src="https://github.com/dogiparthy85/Java-Ubuntu20.04/blob/main/JDK.png" alt="Linux download"></p>

<p>You’ll be presented with a screen asking you to accept the Oracle license agreement. Select the checkbox to accept the license agreement and press the <strong>Download</strong> button. Your download will begin. You may need to log in to your Oracle account one more time before the download starts.</p>

<p>Install the <code>software-properties-common</code> package, which adds the <code>add-apt-repository</code> command to your system:</p>
<pre class="code-pre command prefixed"><code><ul class="prefixed"><li class="line" data-prefix="$">sudo apt install software-properties-common
</li></ul></code></pre>
<p>Next, import the signing key used to verify the software you’re about to install:</p>
<pre class="code-pre command prefixed"><code><ul class="prefixed"><li class="line" data-prefix="$">sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EA8CACC073C3DB2A
</li></ul></code></pre>
<p>You’ll see this output:</p>
<pre class="code-pre "><code><div class="secondary-code-label " title="Output">Output</div>gpg: key EA8CACC073C3DB2A: public key "Launchpad PPA for Linux Uprising" imported
gpg: Total number processed: 1
gpg:               imported: 1
</code></pre>
<p>Then use the <code>add-apt-repository</code> command to add the repo to your list of package sources:</p>
<pre class="code-pre command prefixed"><code><ul class="prefixed"><li class="line" data-prefix="$">sudo add-apt-repository ppa:linuxuprising/java
</li></ul></code></pre>
<p>You’ll see this message:</p>
<pre class="code-pre "><code><div class="secondary-code-label " title="Output">Output</div> Oracle Java 11 (LTS) and 12 installer for Ubuntu, Linux Mint and Debian.

Java binaries are not hosted in this PPA due to licensing. The packages in this PPA download and install Oracle Java 11, so a working Internet connection is required.

The packages in this PPA are based on the WebUpd8 Oracle Java PPA packages: https://launchpad.net/~webupd8team/+archive/ubuntu/java

Created for users of https://www.linuxuprising.com/

Installation instructions (with some tips), feedback, suggestions, bug reports etc.:

. . .

Press [ENTER] to continue or ctrl-c to cancel adding it
</code></pre>
<p>Press <code>ENTER</code> to continue the installation. You may see a message about <code>no valid OpenPGP data found</code>, but you can safely ignore this.</p>

<p>Update your package list to make the new software available for installation:</p>
<pre class="code-pre command prefixed"><code><ul class="prefixed"><li class="line" data-prefix="$">sudo apt update
</li></ul></code></pre>
<p>The installer will look for the Oracle JDK you downloaded in <code>/var/cache/oracle-jdk11-installer-local</code>. 
 Create this directory and move the Oracle JDK archive there:</p>
<pre class="code-pre command prefixed"><code><ul class="prefixed"><li class="line" data-prefix="$">sudo mkdir -p /var/cache/oracle-jdk11-installer-local/
</li><li class="line" data-prefix="$">sudo cp jdk-<span class="highlight">11.0.9</span>_linux-x64_bin.tar.gz /var/cache/oracle-jdk11-installer-local/
</li></ul></code></pre>
<p>Finally, install the package:</p>
<pre class="code-pre command prefixed"><code><ul class="prefixed"><li class="line" data-prefix="$">sudo apt install oracle-java11-installer-local
</li></ul></code></pre>
<p>The installer will first ask you to accept the Oracle license agreement. Accept the agreement, then the installer will extract the Java package and install it.</p>

<p>Now let’s look at how to select which version of Java you want to use.</p>

<a name="managing-java" data-unique="managing-java"></a><a name="managing-java" data-unique="managing-java"></a><h2 id="managing-java">Managing Java</h2>

<p>You can have multiple Java installations on one server. You can configure which version is the default for use on the command line by using the <code>update-alternatives</code> command.</p>
<pre class="code-pre command prefixed"><code><ul class="prefixed"><li class="line" data-prefix="$">sudo update-alternatives --config java
</li></ul></code></pre>
<p>This is what the output would look like if you’ve installed both versions of Java in this tutorial:</p>
<pre class="code-pre "><code><div class="secondary-code-label " title="Output">Output</div>There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                         Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-11-openjdk-amd64/bin/java   1111      auto mode
  1            /usr/lib/jvm/java-11-openjdk-amd64/bin/java   1111      manual mode
* 2            /usr/lib/jvm/java-11-oracle/bin/java          1091      manual mode

Press &lt;enter&gt; to keep the current choice[*], or type selection number:
</code></pre>
<p>Choose the number associated with the Java version to use it as the default, or press <code>ENTER</code> to leave the current settings in place.</p>

<p>You can do this for other Java commands, such as the compiler (<code>javac</code>):</p>
<pre class="code-pre command prefixed"><code><ul class="prefixed"><li class="line" data-prefix="$">sudo update-alternatives --config <span class="highlight">javac</span>
</li></ul></code></pre>
<p>Other commands for which this command can be run include, but are not limited to: <code>keytool</code>, <code>javadoc</code> and <code>jarsigner</code>.</p>

<a name="setting-the-java_home-environment-variable" data-unique="setting-the-java_home-environment-variable"></a><a name="setting-the-java_home-environment-variable" data-unique="setting-the-java_home-environment-variable"></a><h2 id="setting-the-java_home-environment-variable">Setting the <code>JAVA_HOME</code> Environment Variable</h2>

<p>Many programs written using Java use the <code>JAVA_HOME</code> environment variable to determine the Java installation location.</p>

<p>To set this environment variable,  first determine where Java is installed. Use the <code>update-alternatives</code> command:</p>
<pre class="code-pre command prefixed"><code><ul class="prefixed"><li class="line" data-prefix="$">sudo update-alternatives --config java
</li></ul></code></pre>
<p>This command shows each installation of Java along with its installation path:</p>
<pre class="code-pre "><code><div class="secondary-code-label " title="Output">Output</div>There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                         Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-11-openjdk-amd64/bin/java   1111      auto mode
  1            /usr/lib/jvm/java-11-openjdk-amd64/bin/java   1111      manual mode
* 2            /usr/lib/jvm/java-11-oracle/bin/java          1091      manual mode

Press &lt;enter&gt; to keep the current choice[*], or type selection number:
</code></pre>
<p>In this case the installation paths are as follows:</p>

<ol>
<li>OpenJDK 11 is located at <code>/usr/lib/jvm/java-11-openjdk-amd64/bin/java.</code></li>
<li>Oracle Java  is located at <code>/usr/lib/jvm/java-11-oracle/jre/bin/java</code>.</li>
</ol>

<p>Copy the path from your preferred installation. Then open <code>/etc/environment</code> using <code>nano</code> or your favorite text editor:</p>
<pre class="code-pre command prefixed"><code><ul class="prefixed"><li class="line" data-prefix="$">sudo nano /etc/environment
</li></ul></code></pre>
<p>At the end of this file, add the following line, making sure to replace the highlighted path with your own copied path, but <strong>do not</strong> include the <code>bin/</code> portion of the path:</p>
<div class="code-label " title="/etc/environment">/etc/environment</div><pre class="code-pre "><code>JAVA_HOME="<span class="highlight">/usr/lib/jvm/java-11-openjdk-amd64</span>"
</code></pre>
<p>Modifying this file will set the <code>JAVA_HOME</code> path for all users on your system.</p>

<p>Save the file and exit the editor.</p>

<p>Now reload this file to apply the changes to your current session:</p>
<pre class="code-pre command prefixed"><code><ul class="prefixed"><li class="line" data-prefix="$">source /etc/environment
</li></ul></code></pre>
<p>Verify that the environment variable is set:</p>
<pre class="code-pre command prefixed"><code><ul class="prefixed"><li class="line" data-prefix="$">echo $JAVA_HOME
</li></ul></code></pre>
<p>You’ll see the path you just set:</p>
<pre class="code-pre "><code><div class="secondary-code-label " title="Output">Output</div><span class="highlight">/usr/lib/jvm/java-11-openjdk-amd64</span>
</code></pre>
<p>Other users will need to execute the command <code>source /etc/environment</code> or log out and log back in to apply this setting.</p>

<a name="conclusion" data-unique="conclusion"></a><a name="conclusion" data-unique="conclusion"></a><h2 id="conclusion">Conclusion</h2>

<p>In this tutorial you installed multiple versions of Java and learned how to manage them. You can now install software which runs on Java, such as Tomcat, Jetty, Glassfish, Cassandra or Jenkins.</p>
