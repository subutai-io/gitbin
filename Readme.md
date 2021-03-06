# git-bin

![git-bin](https://confluence.subutai.io//download/attachments/20709643/GP?version=1&modificationDate=1433925138295&api=v2)

git-bin is a plugin for git. git-bin allows you store large and binary files outside of your git repository. Instead of normal files git tracks only symlinks to real files, that can be stored somewhere in the network.

Currently git-bin support the following network storages:

* SSH-based access (git-bin uses scp to transfer files)
* S3 Bucket (s3cmd or awscli tool are used to transfer files)

## Building

In order to build git-bin you need to build Poco C++ Libraries first:

* Clone poco from github: git clone https://github.com/pocoproject/poco.git
* cd poco
* Install poco dependencies: build-essential, libssl-dev
* ./configure --omit=Data/ODBC,Data/MySQL
    * If you planning to make a static build (single binary only) you need to configure poco with static libraries support: ./configure --static --omit=Data/ODBC,Data/MySQL
* cmake CMakeLists.txt
* make
* make install 
    * If you did a static build you need to create "lib" directory under git-bin project and move *.a file from poco/lib directory into git-bin/lib

Now you need to configure and build git-bin itself. Note, that git-bin uses cppunit library to run unit tests. If you have no installed cppunit library, than you should append --no-tests flag to configure script

*  ./configure 

    or
    
    ./configure --static

    for static build
* make
* make install
