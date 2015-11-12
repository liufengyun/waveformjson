Waveformjson
========

Waveformjson is based on [waveform](https://github.com/benalavi/waveform) and functions the same. The only difference is that it generates json instead of png files.

Installation
============

Waveformjson depends on `ruby-audio`, which in turn depends on libsndfile.

Build libsndfile from (http://www.mega-nerd.com/libsndfile/), install it via `apt` (`sudo apt-get install libsndfile1-dev`), `libsndfile` in macports, etc...

Then:

    $ gem install waveformjson

or add following to Gemfile:

    gem 'waveformjson'

CLI Usage
=========

    $ waveformjson song.wav waveform.json

There are some nifty options you can supply to switch things up:

    -m sets the method used to sample the source audio file, it can either be
        'peak' or 'rms'. 'peak' is probably what you want because it looks
        cooler, but 'rms' is closer to what you actually hear.
    -W sets the width (in pixels) of the waveform.

There are also some less-nifty options:

    -q will generate your waveform without printing out a bunch of stuff.
    -h will print out a help screen with all this info.
    -F will automatically overwrite destination file.
    -o will output your waveform data to the console.

Usage in code
=============

The CLI is really just a thin wrapper around the Waveformjson class, which you can also use in your programs for reasons I haven't thought of. The Waveform class takes pretty much the same options as the CLI when generating waveforms.

Requirements
============

`ruby-audio`

The gem version, *not* the old outdated library listed on RAA. `ruby-audio` is a wrapper for `libsndfile`, on my Ubuntu 10.04LTS VM I installed the necessary libs to build `ruby-audio` via: `sudo apt-get install libsndfile1-dev`.

Converting MP3 to WAV
=====================

Waveform used to (very thinly) wrap ffmpeg to convert MP3 (and whatever other format) to WAV audio before processing the WAV and generating the waveform image. It seemed a bit presumptious for Waveform to handle that, especially since you might want to use your own conversion options (i.e. downsampling the bitrate to generate waveforms faster, etc...).

If you happen to be using ffmpeg, you can easily convert MP3 to WAV via:

    ffmpeg -i "/path/to/source/file.mp3" -f wav "/path/to/output/file.wav"

Tests
=====

    $ rake


Sample sound file used in tests is in the Public Domain from soundbible.com: <http://soundbible.com/1598-Electronic-Chime.html>.

References
==========

<http://pscode.org/javadoc/src-html/org/pscode/ui/audiotrace/AudioPlotPanel.html#line.996>
<http://github.com/pangdudu/rude/blob/master/lib/waveform_narray_testing.rb>
<http://stackoverflow.com/questions/1931952/asp-net-create-waveform-image-from-mp3>
<http://codeidol.com/java/swing/Audio/Build-an-Audio-Waveform-Display>

License
=======

Copyright (c) 2013 liufengyun

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
