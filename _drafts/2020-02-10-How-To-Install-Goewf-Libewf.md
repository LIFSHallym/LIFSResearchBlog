---
layout: post
title: "How to install Goewf which extends Libewf to read expert witness file"
icon: star-o
author: 2019tony
tags: [Expert Witness File Format, Digital Foensic, Disk Imaging]
---

Expert Witness File (EWF) format allows specific advantages like compression and headers information (specific meta-data included in an image) for data authenticity and more. Libewf is a C library that allows read/write of ewf format. On the other hand, there is a golang library (goewf) that extends the functions of Libewf so that one can carry out ewf task using golang. This is called software binding.

## PROBLEM

We want to be able to use "C" code in golang, otherwise called software binding. This has already been done in the goewf library. It reuses the "C" code in Libewf to carry out EWF task instead of writing all new functions in golang. This enables access to both software advantages of "C" and in golang at the same time. For example, the Libewf library does not currently support concurrency. Binding the library with goewf library gives us the ability to utilize concurrency in golang and possibly increase efficiency.

The goewf library currently has only implemented the read access function in the Libewf library. No warranty offered or implied, please validate if using in an evidentiary context.

This article demonstrates how to install goewf and libewf libraries and read an EWF file.

## INSTALL GOLANG
Skip if you already have golang installed.

I will assume you are using Linux. Otherwise see the [Golang](https://golang.org/) offical website for details on installing in your OS.
	
   #Update to apply latest ubuntu security
    
    	sudo apt-get update
	
   #Upgrade to apply latest ubuntu security
    
    	sudo apt-get -y upgrade 
	
   #Download the go binary archive
   
    	wget https://dl.google.com/go/go1.11.linux-amd64.tar.gz 
	
   #Extract the file archive
   
    	sudo tar -xvf go1.11.linux-amd64.tar.gz 
	
   #move the binary to local folder
    
    	sudo mv go /usr/local   
	
   #Open bash profile file
    
    	sudo nano ~/.zshrc or sudo nano ~/.bashrc 
	
   #copy the next 3lines below and save it into you zshrc or bashrc file.
   
        export GOROOT=/usr/local/go
        export GOPATH=$HOME/go
        export PATH=$GOPATH/bin:$GOROOT/bin:$PATH
	
   #displays the version of go installed. Run this command in a new terminal window.
   
    go version 

   #Bonus
    How to install go on mac os catalina with homebrew.
    #If you are trying to install go on Catalina  with home-brew, here is what work for me.
    
    Run all command from your terminal
    ## Install homebrew (see here https://treehouse.github.io/installation-guides/mac/homebrew for more on how to install homebrew)
    ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install) 
        
    # Open bash profile file
        sudo nano ~/.zshrc 

    # Copy the next 3lines below and save it into you zshrc or bashrc file.
    export GOROOT=/usr/local/opt/go/libexec
    export GOPATH=$HOME/.go
    export PATH=$PATH:$GOROOT/bin:$GOPATH/bin 

    #Install go with brew
        Brew install go

    #Check go version installed
	    go version

### CLONE THE GOEWF REPO FROM GITHUB TO DESIRED LOCATION ON YOUR SYSTEM
    git clone https://github.com/sydp/goewf.git #Clone the goewf repo

### INSTALL BUILD TOOLS
sudo apt install autoconf automake autopoint libtool pkg-config bison flex

#### INSTALL (RUN THE COMMANDS BELOW TO INSTALL AND BUILD THE PROGRAM)
    go get github.com/vitaminwater/cgo.wchar

   #Navigate to sydp/goewf/libewf
   ```bash
    cd libewf/
    
    ./synclibs.sh
    ./autogen.sh
    ./configure
    make
    ```
    
#Navigate to sydp/goewf/

    cd .. 
    
#Build the source

    go build -o goewf cmd/goewf/main.go


### READ THE FIRST 512 BYTES FROM AN EWF FILE NAMED image.E01
    goewf image.E01 512 #image.E01 should correspond to the path to an ewf file you want to read. 

## REFERENCE
https://github.com/sydp/goewf
