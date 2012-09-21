.. _encode:

ENCODING
========

You can encode files from one format/codec to another using this facility.

-o <filename>
    Enables encoding mode and specifies the output file name.

--of=<format>
    Specifies the output format (overrides autodetection by the extension of
    the file specified by -o).
    See --of=help for a full list of supported formats.

--ofopts=<options>
    Specifies the output format options for libavformat.
    See --ofopts=help for a full list of supported options.

    Options are managed in lists. There are a few commands to manage the
    options list.

    --ofopts-add=<options1[,options2,...]>
        Appends the options given as arguments to the options list.

    --ofopts-pre=<options1[,options2,...]>
        Prepends the options given as arguments to the options list.

    --ofopts-del=<index1[,index2,...]>
        Deletes the options at the given indexes. Index numbers start at 0,
        negative numbers address the end of the list (-1 is the last).

--ofps=<float value>
    Specifies the output format time base (default: 24000). Low values like 25
    limit video fps by dropping frames.

--oautofps
    Sets the output format time base to the guessed frame rate of the input
    video (simulates mencoder behaviour, useful for AVI; may cause frame
    drops). Note that not all codecs and not all formats support VFR
    encoding, and some which do have bugs when a target bitrate is
    specified - use --ofps or --oautofps to force CFR encoding in these
    cases.

--oharddup
    If set, the frame rate given by --ofps is attained not by skipping time
    codes, but by duplicating frames (constant frame rate mode).

--oneverdrop
    If set, frames are never dropped. Instead, time codes of video are
    readjusted to always increase. This may cause AV desync, though; to
    work around this, use a high-fps time base using --ofps and absolutely
    avoid --oautofps.

--oac=<codec>
    Specifies the output audio codec.
    See --oac=help for a full list of supported codecs.

--oaoffset=<value>
    Shifts audio data by the given time (in seconds) by adding/removing
    samples at the start.

--oacopts=<options>
    Specifies the output audio codec options for libavcodec.
    See --oacopts=help for a full list of supported options.

    EXAMPLE: "--oac=libmp3lame --oacopts=b=128000" selects 128kbps MP3
    encoding.

    Options are managed in lists. There are a few commands to manage the
    options list.

    --oacopts-add=<options1[,options2,...]>
        Appends the options given as arguments to the options list.

    --oacopts-pre=<options1[,options2,...]>
        Prepends the options given as arguments to the options list.

    --oacopts-del=<index1[,index2,...]>
        Deletes the options at the given indexes. Index numbers start at 0,
        negative numbers address the end of the list (-1 is the last).

--ovc=<codec>
    Specifies the output video codec.
    See --ovc=help for a full list of supported codecs.

--ovoffset=<value>
    Shifts video data by the given time (in seconds) by shifting the pts
    values.

--ocopyts
    Copies input pts to the output video (not supported by some output
    container formats, e.g. avi). Discontinuities are still fixed.
    By default, audio pts are set to playback time and video pts are
    synchronized to match audio pts, as some output formats do not support
    anything else.

--orawts
    Copies input pts to the output video (not supported by some output
    container formats, e.g. avi). In this modem discontinuities are not fixed
    and all pts are passed through as-is. Never seek backwards or use multiple
    input files in this mode!

--ovcopts <options>
    Specifies the output video codec options for libavcodec.
    See --ovcopts=help for a full list of supported options.

    EXAMPLE: "--ovc=mpeg4 --oacopts=qscale=5" selects constant quantizer scale
    5 for MPEG-4 encoding.

    EXAMPLE: "--ovc=libx264 --ovcopts=crf=23" selects VBR quality factor 23 for
    H.264 encoding.

    Options are managed in lists. There are a few commands to manage the
    options list.

    --ovcopts-add=<options1[,options2,...]>
        Appends the options given as arguments to the options list.

    --ovcopts-pre=<options1[,options2,...]>
        Prepends the options given as arguments to the options list.

    --ovcopts-del=<index1[,index2,...]>
        Deletes the options at the given indexes. Index numbers start at 0,
        negative numbers address the end of the list (-1 is the last).
