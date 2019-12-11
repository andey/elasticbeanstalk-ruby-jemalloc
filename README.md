# elasticbeanstalk-ruby-jemalloc
yum repo for installing ruby with jemalloc on elasticbeanstalk

## Dependencies
```
sudo yum install jemalloc-devel
```

## Build
```
wget https://cache.ruby-lang.org/pub/ruby/2.6/ruby-2.6.5.tar.gz
tar xvzf ruby-2.6.5.tar.gz
cd ruby-2.6.5
LDFLAGS=-L/opt/rubies/ruby-2.6.5/lib CPPFLAGS=-I/opt/rubies/ruby-2.6.5/include ./configure --prefix=/opt/rubies/ruby-2.6.5 --with-jemalloc
make
```

## Install
```
wget https://github.com/andey/elasticbeanstalk-ruby-jemalloc/releases/download/2.6.5/ruby-2.6.5.tar.gz
tar -xzf ruby-2.6.5.tar.gz
cd ruby-2.6.5
sudo make install
```

## Verification

Check if ruby has  `-ljemalloc`

```
ruby -r rbconfig -e "puts RbConfig::CONFIG['MAINLIBS']"
```
