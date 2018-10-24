I didn't manage to produce vignettecalib using vignetteCalib yet, but I was able to produce a pcalib.txt file from my own dataset using responseCalib. I will try to explain the process.

Suppose you have a directory with your dataset called sweepData and you want to use responseCalib to create pcalib.txt for you.

    the directory sweepData should have following content:

sweepData:
   camera.txt
   images.zip
   times.txt

    camera.txt should contain camera calibration as described here
    My camera.txt look like this:

0.39500631 0.40439271 0.31469786 0.17470434 1.0
856 480
none
856 480

It can be written by hand on condition you know the intrinsic parameters for your camera.

    images.zip should be an archive of jpg files with names in format: XXXX.jpg where XXXX is imageID (leading zeroes starting with 0000)

    times.txt is a text file with three whitespace separated columns:
    imageID timestamp exposureTime
    Where timestamp is a POSIX time and exposureTime is a real number denoting exposure time in ms

Calling responseCalib like this:

./responseCalib /path/to/data/sweepData/

should produce directory with pcalib.txt