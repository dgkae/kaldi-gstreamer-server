https://github.com/dgkae/kaldi-gstreamer-server

https://github.com/dgkae/gst-kaldi-nnet2-online

它把kaldi的decoder直接作为了gstreamer的plugin来工作，这是十分契合的。
但是我们现在的阶段，不求server上的接受端websocket->gstreamer后直接与kaldi的decoder相连，而是
先websocket->gstreamer通过一个Plugin存下来音频，然后调用我们的decoder脚本对音频进行处理，然后范围结果。

而且gstreamer的好处就是plugin的Pipleline形式，而现在没这个必要，最好服务端全python，而不要有c的gstream代码。
所有不用gstreamer。现在的目标就是做一个demo，用websocket，客户端用recorder.js来录音，然后传到服务器，服务器能够进行segments，并即使范围各segment的识别结果。