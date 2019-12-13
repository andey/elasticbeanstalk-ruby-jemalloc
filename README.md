# elasticbeanstalk-ruby-jemalloc
yum repo for installing ruby with jemalloc on elasticbeanstalk

## Dependencies
```
sudo yum install jemalloc-devel
```

## Build
These are the instructions I've used to build ruby.

```
wget https://cache.ruby-lang.org/pub/ruby/2.6/ruby-2.6.5.tar.gz
tar xvzf ruby-2.6.5.tar.gz
cd ruby-2.6.5
LDFLAGS=-L/opt/rubies/ruby-2.6.5/lib CPPFLAGS=-I/opt/rubies/ruby-2.6.5/include ./configure --prefix=/opt/rubies/ruby-2.6.5 --with-jemalloc --disable-install-doc
make
sudo make install
```

## Install
The release is just a tarball of the `/opt/rubies/ruby-2.6.5` directory. Simply download the tarball, unpack and replace.

```
wget https://github.com/andey/elasticbeanstalk-ruby-jemalloc/releases/download/2.6.5/ruby-2.6.5.tar.gzz
tar xvzf ruby-2.6.5.tar.gz -C /opt/rubies
```

## .ebextentions file
```
commands:
  "01":
    command: wget https://github.com/andey/elasticbeanstalk-ruby-jemalloc/releases/download/2.6.5/ruby-2.6.5.tar.gz
  "02":
    command: tar xvzf ruby-2.6.5.tar.gz -C /opt/rubies
 ```

## Verification

Check if ruby has  `-ljemalloc`

```
ruby -r rbconfig -e "puts RbConfig::CONFIG['MAINLIBS']"
```
