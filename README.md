# Video Compression Tutorial
By Eva Petakovic
This tutorial is about the basic concept of compression as it applies to video

Video streaming websites like YouTube, Netflix and Hulu would not be able to stream high quality, high frame rate videos without using video compression.

Let's say you're watching a video with a resolution of 1920x1080 pixels, which is 2, 073,600  million pixels per frame,
at a rate of 30 frames per second. That would amount to 62 million pixels per second. If each pixel needs 24 bits, or 3
bytes of information, you're looking at 178 megabytes of data per second. Completely uncompressed that would be 51 gigabytes of information 
for a 5 minute video. Even with fast internet

Fortunately a 5 minute high def YouTube video is not 51 gigabytes. It is closer to 72 megabytes including audio. That's like 700 times smaller.
How did they do that? That's the magic of video compression, which works by minimizing redundancy in the video data. There are all
sorts of different ways to compress video, many different containers and codecs. The main thing you need to know is that there are 2 ways 
compress video, spatial and temporal compression, which are called intraframe and interframe compression respectively. 

Spatial (intraframe) compression is applied only to individual video frames. To compress a video frame you can use the same process
that's used to compress a still image like a JPEG. When a JPEG is created, color information of the image is reduced in a process called 
chroma subsampling, and then the image is split into sections of 8X8 pixels called macroblocks. Other transformations are applied
to these macroblocks such as discrete cosign transform, quantizing, and entropy encoding, to further reduce the file size. It's easy to 
see this effect on an image that has been saved with a high amount of compression. All those ugly looking squares are known as compression
artefacts. Some images, like a square of a solid color, can be compressed more than a more complicated photograph because of its simplicity
and increased redundancy. That's how a JPEG uses spatial compression. 

For an MPEG, sometimes called a "motion JPEG", things are bit more complicated than lining up many JPEGs one after another to be used as 
video frames. Doing it that way would not allow for interframe or temporal compression. Temporal compression works, again, by reducing
redundancy. If you go through a video frame by frame, you'll notice that many frames are almost completely identical. That's redundancy
which can be easily be compressed. All the parts of a video that don't change over time, like an unmoving background, all that is
needed is an instruction for that part of the frame which says "don't change anything". Like JPEG, the MPEG standard breaks a video
frame into 8x8 pixel macroblocks, and each block receives instructions about what to do with pixels they already have. There are
instructions for staying exactly the same, moving, rotating, changing color, changing completely or so on. Video instructions of
this type are called keyframes, and they use about half as much data as an i-frame, which is basically a JPEG. There are also B frames
which are predictions, or interpolations, between I and P frames. B frames use a quarter as much data as an i frame. This is easy to
see on a video file that has been saved in an extremely low quality setting. Again, all the fuzzy squares are called compression artefacts.
Furthermore, sometimes a video file will be corrupted or missing some data. When that happens, you get effects caused by things like 
missing i-frames, which clear away old image to make way for a new one. WIthout the i frame, the list of changes in the following B and P
frames are applied to the wrong image. So now you know why a video sometimes looks weird and blocky. Those artefacts are a result of
the video compression being either too high or some other error in the coding or transmission of the video data.

All of this can be broken down to one thing: Bitrate. The bitrate is the amount of data, or bits, that are being used every second. If
a video has a low bitrate, it will be low resolution and low quality with lots of compression artefacts. If a video has a high bitrate,
it will be high quality and high resolution. The more bits you have to work with, the better the video will look. There's just no getting 
around that even with the best compression methods. Video compression is a balancing act between a good looking video and a small file size.
You can't have both!

