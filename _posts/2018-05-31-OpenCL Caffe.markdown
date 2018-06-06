# OpenCL Caffe

## OpenCL Caffe
```
https://github.com/BVLC/caffe/tree/opencl
https://github.com/01org/caffe (Intel maintains)
```
### Dependency
1. lmdb-mdb
2. gflags
3. glog
4. leveldb
5. snappy
6. Altas (Hard to compile) /OpenBLAS
7. ViennaCL
8. libDNN
9. OpenCL-ICD-Loader
10. OpenCL & OpenCL Driver

#### ViennaCL
```
https://github.com/viennacl/viennacl-dev
```

#### libDNN
```
https://github.com/naibaf7/libdnn
```

#### OpenCL-ICD-Loader
It's a proxy to switch between different implementations of OpenCL in the device.
The config file is located in /etc/OpenCl/vendors/XXXXX.icd

#### OpenCL & Driver
Depends on your vendor.

## cuCaffe

#### Thrust
```
https://thrust.github.io/
```

#### NCCL
```
https://github.com/NVIDIA/nccl
```

#### Refs
