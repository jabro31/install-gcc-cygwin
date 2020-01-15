# install-gcc-cygwin
Install gcc with cygwin on windows. I already did the annoying figuring out so you don't have to! Here, I'll show how to install gcc 9.2.0.

1. Follow the first two steps from https://preshing.com/20141108/how-to-install-the-latest-gcc-on-windows/.
2. In the cygwin64 folder, run the Cygwin.bat file.

!!! Cygwin automatically creates a folder in the "cygwin64/home" folder with your username. However, installation will fail if your username contains a space! To account for this, we want bash to open in a folder without a space. To do this, write the command:

```echo "cd C:\cygwin64\home\USER_NAME_WITHOUT_SPACE" >> ~/.bashrc```

Then run the Cygwin.bat file again.

3. This will download gcc-9.2.0 files and unpack them, enter:

```wget http://ftpmirror.gnu.org/gcc/gcc-9.2.0/gcc-9.2.0.tar.gz```, .

```tar xzf gcc-9.2.0.tar.gz```

4. To download prerequisites in the gcc-9.2.0 folder, enter:

```cd gcc-9.2.0```

```.contrib/download_prerequisites```

5. to set current directory to where gcc needs to be installed, enter:

```cd ..```

```mkdir objdir```

```cd objdir```, .

6. To create the makefile in objdir, but access the files in gcc-9.2.0 folder, enter:

```../gcc-9.2.0/configure --prefix=C:/cygwin64/home/USER_NAME_WITHOUT_SPACE/gcc-9.2.0 --enable-languages=c,c++,fortran```

7. Finally, run the following and go outside and take a walk, because this will take a long time.

```make -j 2``` or 4 or 8, depending on which order of parallisation you want it to install

```make install```

--- Atm it's not yet installed lol




Sources:

- https://preshing.com/20141108/how-to-install-the-latest-gcc-on-windows/ , make part didn't work and misses to install "download_prerequisites".
- https://stackoverflow.com/a/27070063/5588977 , to specify the costum directory in which Cygwin will open. Thanks dude.
- https://gcc.gnu.org/wiki/InstallingGCC , works if you replace "PWD" with ".." and don't "enable-languages" for "go".
- https://stackoverflow.com/questions/28054448/specifying-path-to-makefile-using-make-command , optional info.
