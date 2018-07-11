# Caffe Tools

### File suffix
1. .binaryprototxt: The mean value of input images.


2. .prototxt
   1) solver.prototxt:          Wrap configuration of caffe training
   2) .prototxt:                Layer descriptions
      deploy.prototxt is similiar to train_val.prototxt.
      BUT They are different.
      
      I.  deploy.prototxt:       raw model
      
      Data Layer
      ```
      name: "CaffeNet"                                             
      layer {                                                      
        name: "data"                                               
        type: "Input"                                              
        top: "data"                                                
        input_param { shape: { dim: 10 dim: 3 dim: 227 dim: 227 } }
      }
      ```
      
      Softmax
      ```
      layer {          
        name: "prob"   
        type: "Softmax"
        bottom: "fc8"  
        top: "prob"    
      }                
      ```
      II. train_val.prototxt:    configured model for training or testing.
      
      Data Layer
      ```
      name: "CaffeNet"
      layer {
        name: "data"
        type: "Data"                                          
        top: "data"
        top: "label"                                          
        include {                                             
          phase: TRAIN                                        
        }                                                     
        transform_param {                                     
          mirror: true                                        
          crop_size: 227                                      
          mean_file: "data/ilsvrc12/imagenet_mean.binaryproto"
        }                                                     
      # mean pixel / channel-wise mean instead of mean image  
      #  transform_param {                                    
      #    crop_size: 227                                     
      #    mean_value: 104                                    
      #    mean_value: 117                                    
      #    mean_value: 123                                    
      #    mirror: true                                       
      #  }                                                    
        data_param {                                          
          source: "examples/imagenet/ilsvrc12_train_lmdb"     
          batch_size: 256                                     
          backend: LMDB                                       
        }                                                     
      }                                                                                                 
      ```
      
      Accuracy
      ```
      layer {                  
        name: "accuracy"       
        type: "Accuracy"       
        bottom: "fc8"          
        bottom: "label"        
        top: "accuracy"        
        include {              
          phase: TEST          
        }                      
      }
      ```
      Softmax
      ```
      layer {                   
        name: "loss"            
        type: "SoftmaxWithLoss" 
        bottom: "fc8"           
        bottom: "label"         
        top: "loss"             
      }                         
      ```
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
