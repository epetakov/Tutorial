# Video Compression 
By Eva Petakovic

This tutorial covers the basic concept of video compression and some associated terminology. It's meant to serve as an introduction to these topics and offer jumping-off points for deeper study for college-age students.



Imagine watching an online video with a resolution of 1920x1080 pixels. With about 2.1 million pixels per frame, 24 bits per pixel, and at a rate of 25 frames per second, a video of this type would require 1.1 gigabits/second. Considering that the average broadband internet speed in the US is 18.7 *megabits*/second (mbps) this bitrate is impractical for the vast majority of internet users.


By reducing redundancy in video data, compression can cut down their file sizes considerably. Containers and codecs of many different types are used to compress video, but they use two main methods: spatial and temporal compression, which are called **intraframe** and **interframe** compression respectively. 


Spatial (intraframe) compression is applied to individual video frames. To compress a video frame you can use the same process used to compress a still image like a JPEG. When a JPEG is created, color data in the image is reduced in a process called 
[chroma subsampling](https://en.wikipedia.org/wiki/Chroma_subsampling), and then the image is split into sections of 8X8 pixels called [macroblocks](https://en.wikipedia.org/wiki/Macroblock). Other transformations are applied to these macroblocks such as [discrete cosign transform](https://en.wikipedia.org/wiki/Discrete_cosine_transform), [quantizing](https://en.wikipedia.org/wiki/Quantization), and [entropy encoding](https://en.wikipedia.org/wiki/Entropy_encoding) to further reduce the file size. Evidence of these macroblocks can be seen as the smudged, blocky-looking squares visible when video has poor playback quality. In these cases they are known as [compression artifacts](https://en.wikipedia.org/wiki/Compression_artifact). A shape of a solid color can be compressed much more than a more complex image because of its simplicity and therefore increased redundancy. 

As you move through a video frame by frame, many are almost totally identical which is a redundancy that can be easily compressed. All the parts of a video that don't change over time, like an unmoving background, only require an instruction for that part of the frame telling the pixels not to change. Like JPEG, the MPEG standard breaks a video frame into 8x8 pixel macroblocks, with each block receiving instructions about what to do with the pixels they currently have. There are instructions for staying exactly the same, moving, rotating, changing color, changing completely, and many other types of transformations. Called [keyframes](https://en.wikipedia.org/wiki/Key_frame#Video_compression) or intra-frames, these instructions use about half as much data as an I-frame, which can be thought of as a JPEG. There are also B frames which are predictions, or interpolations, between I and P frames, which are the predicted resulting frames. B frames use a quarter as much data as an I frame because they carry only the information about changes to the image between frames. The I, P and B frames are joined together in sequences that reference each other called [GOPs](https://en.wikipedia.org/wiki/Group_of_pictures) or Group of Pictures. A typical sequence for a GOP is IBBPBBP, where the initial I frame requires no extra information to decode it, the B and P frames contain motion-compensated difference information relative to frames that have already been decoded.

Sometimes a video file will be corrupted or missing some data. When that happens, you get effects caused by things like 
missing I-frames, which clear away old images to make way for new ones. Without the I-frame, the list of changes in the following B and P
frames are applied to the wrong image.

All of this can be broken down to one thing: The bitrate. Bitrate is the amount of data, or bits, that are being used by the video frames each second. If a video has a low bitrate, it will be low resolution and low quality with more compression artifacts. With a high bitrate, the video will be high quality and high resolution. 




