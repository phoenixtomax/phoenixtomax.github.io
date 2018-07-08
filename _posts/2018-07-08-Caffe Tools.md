# Caffe Tools

### File suffix
1. .binaryprototxt: The mean value of input images.


2. .prototxt
   1) solver.prototxt:  wrap configuration of caffe training
   2) .prototxt:        Layer descriptions
   #### Grammary
   bottom: the input of layer
   
   up: the output of layer
   
   include {}:  specify phase(TEST/TRAIN) of caffe.

3. .caffemodel: weights of specified layer description.
   * TIPS: The layer descriptions seems also to be written into .caffemodel.


4. lmdb/leveldb: the database of input images.
   * TIPS: the lmdb(B+ Tree) consume more memory that leveldb. But it's faster than leveldb.

   Refs: [LMDB](http://www.lmdb.tech/doc/)

5. file list: the file path of input images & the classes of each which follows file path.
   


### Tools
1. compute_image_mean: compute mean value of images into .binaryprototxt

2. upgrade_net_proto_text: Upgrade old prototxt file into new prototxt file.

3. convert_imageset: Convert images(png/jpg) into database (lmdb/leveldb)
