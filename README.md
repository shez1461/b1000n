# B1000N Web UI Demo:
[![Part 1](https://img.youtube.com/vi/pFfOZwLhzeM/0.jpg)](https://youtu.be/pFfOZwLhzeM)

# Bamboo Application Repository
The BambooApps repository is the common repository as the source base for all applications running on different Bamboo platforms. 

The repository acts a self contained system without necessary setup of toolchains etc. 

The applications on the repository can be compiled for linux-PC or for embedded platform with 32 bit/64 bit ARM processors. The swtest system can be compiled for Linux, arm processor allowing some offboard testing/emulation. Debugging on the board requires a serial terminal connection.

Checkout the software tree from git server

For more information of the directory structure refer to -
https://kaleao.atlassian.net/wiki/display/CHAS/Getting+started+with+Chassis+Platfrom+Application

### Setting up build environment
All tools that are essential to build a system are available in the software tree. You will require a unix style shell prompt to build a system. The cross-platform build tools are 32-bit applications. Recommended host development environment are Ubuntu 14-04, 16-04 or 18-04.

### Clone Applications repository
System should be built from the source directory. Software checkout in - /home/user/applications:
***For example:***
```sh
$ cd /home/$USER/
$ git clone git@bitbucket.org:kaleao/bambooapps.git
OR
$ git clone https://$USER@bitbucket.org/kaleao/bambooapps.git
Replace the above '$USER' with your username of the bitbucket account & Make sure you have account privileges.
```

### Command to build a system
To build a system, the current working directory - /home/$USER/applications:
***For example:***
```sh
$ cd /home/$USER/applications/
$ make KALEAO_SYSTEM=[systemX] BUILD_TYPE=[debug] KALEAO_PLAT=[platform]

# To Run Single-Bladed Simulator:
$ sudo ./build/swtest/linux/debug/swtest_linux -lin -ler -r TestN1uSim::testSingleBladeChassis
```

***KALEAO_SYSTEM*** - can be any of the systems under directory - 'system/'

***BUILD_TYPE*** - can be either of 'debug' or 'release' or 'clean'.

***KALEAO_PLAT*** - is optional and only needed when 'KALEAO_SYSTEM' is 'swtest'. It can be either - 'linux' or 'rpi3'.

Location of build outputs - **'build/[systemX]/[BUILD_TYPE]/'**

### Build using script
To use a pre-defined 'build' script, type & execute './build.sh' located under tools/buildscripts for usage & options.
'./build.sh' requires [bash](https://linux.die.net/man/1/bash) to run.
```sh
$ cd applications/tools/buildScript
$ ./build.sh
```

### Usage:
/tools/buildScript/[build.sh](https://bitbucket.org/kaleao/bambooapps/src/master/tools/buildScript/build.sh)
[clean][swtest-sim][run-single][run-dual]
***For example:***
```sh

Bamboo Applications - all-in-one script for building Bamboo platform applications.
Usage: 'build.sh'  [clean]|[swtest-sim]|[n1u-sim]|[n1u-bmc]
                   [run-swtest-sim]|[run-n1u-single]|[run-n1u-dual]
For example:
$ ./build.sh clean
 - To Clean the build directory.

[Build Simulator]:
$ ./build.sh swtest-sim
 - To Build swtest simulation & tests on linux machine or

[Run Simulators]:
$ ./build.sh run-single
 - To Run N1U simulator [single] Bladed application on linux machine or

$ ./build.sh run-dual
 - To Run N1U simulator [dual] Bladed application on linux machine or


```

### Web UI - Swtest Simulator
To access the WebUI, run simulator - 'run-single' & navigate by typing your machine's IP along with port number [:5001] in your preferred browser:

***For example:***
```sh
http://<ip address>:5001
http://127.0.0.1:5001
```

Copyright Bamboo Systems Group Ltd.
