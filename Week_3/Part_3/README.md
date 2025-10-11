# 🎯 Installation Of OpenSTA tool for Timing and Power Analysis


🎯  🛠️
Before **installing OpenSTA** make sure you have the necessary development tools and libraries installed.

### Prerequisites
The listed build dependency versions are the ones used during development; other versions might also work but aren’t guaranteed.
`````
         Ubuntu   Macos
        22.04.2   14.5
cmake    3.24.2    3.29.2
clang             15.0.0
gcc      11.4.0
tcl       8.6      8.6.16
swig      4.1.0    4.1.1
bison     3.8.2    3.8.2
flex      2.6.4    2.6.4

`````
### External Library requirements:
`````
           Ubuntu   Darwin  License
eigen       3.4.0   3.4.0   MPL2  required
cudd        3.0.0   3.0.0   BSD   required
tclreadline 2.3.8   2.3.8   BSD   optional
zLib        1.2.5   1.2.8   zlib  optional

`````
### Building with CMake
- On your home directory type the following command
`````
sudo apt-get update
sudo apt-get install build-essential tcl-dev tk-dev cmake git
`````
<img width="900" height="508" alt="image" src="https://github.com/user-attachments/assets/8fad62e4-0ddc-46cd-89a3-fb4fb7a4ea6a" />
<img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/446970e6-bc5f-478e-9b52-8f92badb811b" />

- Clone the OpenSTA repository by executing the following command
`````
git clone https://github.com/The-OpenROAD-Project/OpenSTA.git
`````
- Move into the OpenSTA directory that was created during cloning process using the following command
`````
cd OpenSTA
`````

- Create a build directory using the following command
`````
mkdir build
`````

- Move into the build directory using the following command
`````
cd build
`````

- Configure the build be executing the following command
`````
cmake ..
`````
This command configures the build process for OpenSTA, generating the necessary build files based on the project's configuration.
<img width="940" height="571" alt="image" src="https://github.com/user-attachments/assets/8c428e67-31db-4d62-b67e-7e37cb784672" />

If it shows an error related to Eigen3 like as shown below, then you have to install Eigen3 by using the following below command 

<img width="858" height="589" alt="image" src="https://github.com/user-attachments/assets/878f279f-1799-41c8-83d8-2c7e4c975a7c" /><br>

- Move to the home directory using the following command
`````
cd 
`````

- Install the eigen using the following command
````
sudo apt-get install libeigen3-dev
````
- Again move to the build directory in OpenSTA and configure the build by executing the following command
```
cmake ..
```
<img width="900" height="571" alt="image" src="https://github.com/user-attachments/assets/36da09bf-cc7c-44cd-aea4-b007a1a36ddb" /><br>
If the above error occured then you have to install CUDD
- Move to your home directory and clone the CUDD repository by executing the following command
```
git clone https://github.com/ivmai/cudd.git
```











