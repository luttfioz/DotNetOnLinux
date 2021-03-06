
# Getting Started
## .NET on Linux

### Prerequisites

1. A system running Red Hat Enterprise Linux
1. Your system needs to have 'wget' installed. You can assure that by running the following command:  
`yum install -y wget`

**NOTE:** If you ran the Vagrantfile inside vagrant-machine/ directory, you can go directly to *Prove your dotnet installation* section.

## Instructions
### Get the .NET bits
`wget https://dotnetcli.blob.core.windows.net/dotnet/beta/Binaries/Latest/dotnet-dev-rhel-x64.latest.tar.gz`

### Install some dependencies
`sudo yum install -y libicu libuuid libcurl openssl libunwind`

### Create a home for the dotnet binaries
`mkdir ~/dotnet`

### Unpack the dotnet binaries
`tar xf dotnet-dev-rhel-x64.latest.tar.gz -C ~/dotnet --verbose`  
(Note: The verbose option is shown in order to give you a sense of the scope of the .NET framework)  

### Add the binaries to our path; now, the dotnet command is ready for use
`export DOTNET_HOME=$HOME/dotnet`  
`export PATH=$PATH:$DOTNET_HOME`

Note: It's a good idea to add the above to lines to your .bash_profile file.  

### Prove your dotnet installation  
`dotnet --help`  
This will prove that you have successfully installed the dotnet CLI and provide you with an over of the command available.  

### Create and move into a directory for our "Hello world" code
`mkdir src`  
`mkdir src/helloworld_cli`  
`cd src/helloworld_cli/`  

### Here's the magic; Create a new project, pull down the dependencies, and run it
`dotnet new`  
`dotnet restore`  
`dotnet run`  

You should see a message similar to  
```Compiling helloworld_cli for .NETStandard,Version=v1.5```

After a successful compile, you should see `Hello World!` as console output.

<hr>  
## Stop! If you are reading this document online...  
...you will need to download or `git clone` this repo in order to continue. The code referenced from this point forward assumes you have copied this repo to your local machine.  
<hr>

## HelloWeb example
### Move to the directory
`cd ~/src/DotNetOnLinux/cli-samples-master/HelloWeb`

### Restore and run the code
`dotnet restore`  
`dotnet run`  

You should receive the following message:  
`Now listening on: http://*:5000`  
`Application started. Press Ctrl+C to shut down.`  

* If you are running RHEL with a graphical shell, you can open your browser and point it to `http://localhost:5000` to see the results.  
* If you are running RHEL in a Virtual Machine (VM), choose one of the following to find the correct IP address:  
 - If you're using the CDK, use `http://10.1.2.2:5000`  
 - If you're running inside of Hyper-V, use the command `ifconfig`, then run `systemctl stop firewalld` to gain access.  

Your browser should show the message "Hello World!".  

Press `Ctrl+C` to terminate the .NET web server.  

## HelloMvc example
### Move to the directory  
`cd ~/src/DotNetOnLinux/cli-samples-master/HelloMvc`  

### Restore and run the code  
`dotnet restore`  
`dotnet run`  

As with the previous example, you'll need to use the appropriate IP address to form your browser URL. You should see a banner representing the successful execution of an ASP.NET MVC web application.  

## HelloWebApi example  
### Move to the directory  
`cd ~/src/DotNetOnLinux/cli-samples-master/HelloMvcApi`  

### Restore and run the code  
`dotnet restore`  
`dotnet run`  

As with the previous example, you'll need to use the appropriate IP address to form your browser URL. In this case, you should be able to use the following as examples:  
`http://{your ip address here}:5000/api/products`   
`http://{your ip address here}:5000/api/products/1`  


## Entity Framework InMemory example  
This example is a simple demonstration of an InMemory database using Entity Framework.  

### Move to the directory   
`cd ~/src/DotNetOnLinux/cli-samples-master/EFInMemory`  

### Restore and run the code  
`dotnet restore`  
`dotnet run`  

### Open the web site in your browser  
As with the previous example, you'll need to use the appropriate IP address to form your browser URL. For this example, simply append a word or phrase to the end of your URL; It will be saved to a database and the page will refresh with an updated list of the 10 most recent requests -- a request history.  

`http://{your ip address here}:5000/{word or phrase here}`

(If you look a the source code in /Controllers/ValuesController, you can change the number of items to be listed)  
