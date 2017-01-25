# This Image creates an Ubuntu 16.04 Image with Android SDK Installed

## FOR UPTIGHT SECURITY AND TO FOLLOW CICD BEST PRACTICES
## FOLLOW THE STEPS BELOW TO CREATE THE ADDITIONAL ARTIFACTS
## REQUIRED BY THIS Dockerfile. WITHOUT THEM THIS Dockerfile WILL FAIL!

##

### THE ADDITIONAL ARTIFACTS ARE THE ORACLE JDK 8 AND THE ANDROID
### COMMAND LINE TOOLS THEY ARE FREELY AVAILABLE BUT, CAN'T BE
### INCLUDED HERE DUE TO SIZE AND LICENCE RESTRICTIONS.

#### STEPS to Install Oracle JDK 8 manually:

##### 1) Download the oracle jdk from:
#####    http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

##### 2) Verify the integrity of the download, uncompress the download, Virus check it.

##### 3) Recompress the jdk folder and add it to the same directory as the Dockerfile.

#####    The name of the folder should be "jdk.[current-version-number]" in my case
#####    the current version is '8.0_121' so my uncompressed jdk 8 folder is
#####    named: jdk1.8.0_121 after recompressing it should be jdk1.8.0_121.tar.gz

##### 4) Uncomment the statement 'ADD jdk1.8.0_121.tar.gz /opt/' to tell docker to
#####    uncompress 'jdk1.8.0_121.tar.gz into the /opt directory on the docker image.

##### 5) The statement starting with 'RUN update-alternatives --install' to sets all 
#####    the symlinks to make java executable from anywhere on the image and tests it's working.

#####    If it is successful the following text will be printed to the screan:

         java version "1.8.0_121"
         Java(TM) SE Runtime Environment (build 1.8.0_121-b13)
         Java HotSpot(TM) 64-Bit Server VM (build 25.121-b13, mixed mode)
####

##  Install Android Command Line tools securely ##

#### STEPS to Install Android Command Line (Terminal) tools SECURELY:

##### 1) Download the Android Terminal (Command Line) tools from from:
#####    https://developer.android.com/studio/index.html

#####    curl -O https://dl.google.com/android/repository/tools_rXX.X.X-linux.zip

#####    Current version (January 25 2017) tools_r25.2.3-linux.zip

##### 2) Verify the integrity of the download, uncompress the download, Virus check it.

##### 3) Recompress the 'tools' folder and add it to the same directory as the Dockerfile.

#####    The name of the folder should be "tools" in my case the current version
#####    is 'tools_r25.2.3' so my uncompressed Android command Line tools folder is
#####    named: tools. After recompressing it should be tools.tar.gz but, it might be
#####    prudent to rename it tools_r25.2.3-linux.tar.gz for documentation purposes.

##### 4) The statement 'ADD tools.tar.gz /opt/android/' tells docker to
#####    uncompress 'tools.tar.gz' into the /opt/android directory on the docker image.
#####    make sure that you change the 'ADD tools.tar.gz /opt/android/' statement to match
#####    the tools_rXX.X.X-linux.tar.gz file if you changed the name.

##### 5) The statement starting with 'RUN ln -s /opt/android/tools/android...' sets all the
#####    symbolic links to make the Android SDK executable from anywhere on the image and
#####    test it's working.

#####    If it is successful the following text will be printed to the terminal screan:

  Installed packages:
  Path                        | Version | Description                    | Location                    
  -------                     | ------- | -------                        | -------                     
  build-tools;23.0.3          | 23.0.3  | Android SDK Build-Tools 23.0.3 | build-tools/23.0.3/         
  build-tools;25.0.2          | 25.0.2  | Android SDK Build-Tools 25.0.2 | build-tools/25.0.2/         
  extras;android;m2repository | 41.0.0  | Android Support Repository     | extras/android/m2repository/
  platforms;android-14        | 4       | Android SDK Platform 14        | platforms/android-14/       
  platforms;android-15        | 5       | Android SDK Platform 15        | platforms/android-15/       
  platforms;android-16        | 5       | Android SDK Platform 16        | platforms/android-16/       
  platforms;android-17        | 3       | Android SDK Platform 17        | platforms/android-17/       
  platforms;android-18        | 3       | Android SDK Platform 18        | platforms/android-18/       
  platforms;android-19        | 4       | Android SDK Platform 19        | platforms/android-19/       
  platforms;android-20        | 2       | Android SDK Platform 20        | platforms/android-20/       
  platforms;android-21        | 2       | Android SDK Platform 21        | platforms/android-21/       
  platforms;android-22        | 2       | Android SDK Platform 22        | platforms/android-22/       
  platforms;android-23        | 3       | Android SDK Platform 23        | platforms/android-23/       
  tools                       | 25.2.3  | Android SDK Tools 25.2.3       | tools/                      

  Available Packages:
  Path                              | Version      | Description                      
  -------                           | -------      | -------                          
  add-ons;addon-g..._apis-google-15 | 3            | Google APIs                      
  add-ons;addon-g..._apis-google-16 | 4            | Google APIs
  .....
####
