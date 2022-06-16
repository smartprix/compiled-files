# compiled-files
Pre compiled files for various programs

## How to compile pika
```sh
sudo apt install -y liblz4-1 liblz4-dev libzstd1 libzstd-dev libsnappy1v5 libsnappy-dev zlib1g zlib1g-dev libprotobuf23 libprotobuf-dev protobuf-compiler libgoogle-glog0v5 libgoogle-glog-dev libgflags2.2 libgflags-dev
sudo apt install -y gcc-9 g++-9
cd /tmp
git clone https://github.com/OpenAtomFoundation/pika.git --depth 1
cd pika
git submodule update --init
sed -i 's#^CXX=.*#CXX=g++-9#' Makefile
sed -i '1s/^/DISABLE_WARNING_AS_ERROR=1\n/' third/rocksdb/Makefile
make
cd output
tar -czvf pika-3.4.1.tar.gz *
```
