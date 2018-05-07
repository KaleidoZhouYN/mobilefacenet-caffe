# mobilefacenet-caffe
a caffe implementation of mobilefacenet,with the record of trainnig log 

update the deploy.prototxt & training log of Amsoftmax on Webface @ 24/4/2018

update the solver.prototxt & training log of 6W iteration in ./proto_revise/ @ 30/4/2018

update @ 7/5/2018:

since there is a re-implementation of mobilefacenet by insightface:
	[https://github.com/deepinsight/insightface](https://github.com/deepinsight/insightface)
you can train on public dataset using insightface then transform the mxnet model to caffe model using [MxNet2Caffe](https://github.com/GarrickLin/MXNet2Caffe)

pay attention that:
1.there is something to be fixed in insightface/src/symbols/fmobilefacenet.py
you can just download the fmobilefacent.py in this project and replace it in insightface.
then type:
CUDA_VISIBLE_DEVICES='0,1,2,3' python -u train_softmax.py --network y1 --loss-type 4 --margin-m 0.5 --data-dir ../datasets/faces_ms1m_112x112  --prefix ../model-y1 --emb-size = 128
to train the mobilefacenet with insightface.

2.if you are using cudnn,the group convolution with cause a memory error while using Mxnet2Caffe
so you have to add engine:CAFFE in each group convolution layer
or you can download the prototxt_basic.py in this project and replace it in MXNet2Caffe

Links:

paper:[MobileFaceNets: Efficient CNNs for Accurate Real-time Face Verification on Mobile Devices](https://arxiv.org/abs/1804.07573)

amsoftmax:[happynear/AMSoftmax](https://github.com/happynear/AMSoftmax)

depthwise convolution:[yonghenglh6/DepthwiseConvolution](https://github.com/yonghenglh6/DepthwiseConvolution)

mobilenetv2-caffe:[shicai/MobileNet-Caffe](https://github.com/shicai/MobileNet-Caffe)