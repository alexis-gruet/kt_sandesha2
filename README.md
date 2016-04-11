# kt_sandesha2
Sandesha2/c

#Instruction
First compile kt_axis2c-unofficial then compile sandesha

#Additional note
Require Rampart/c

#Compile MAC OSX 
./configure --prefix=/usr/local/axis2c --with=/usr/local/axis2c/include/axis2-1.6.0

#Compile Ubuntu 14.04LTS

./autogen.sh
./configure --with-axis2=/usr/local/axis2c/include/axis2-1.6.0 --prefix=/usr/local/axis2c

make && make install
