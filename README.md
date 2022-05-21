# xtsync

Synchronize a transcoded/filtered view of files from a source to a target tree.

This synchronizes a FLAC (lossless, large) music library tree with an MP3 (lossy, smaller) view.
The target MP3 tree may then be distributed on portable media (say, with rsync) for use by players.

The ./source library consists of FLAC and MP3 files (all other files are ignored).
Source FLAC files are transcoded to MP3 in the ./target tree
and will include, potentially, an embedded, scaled, front-cover tag
from a source-folder-adjacent folder.jpg file.
Source MP3 files are hard linked to in the target.

Target files that are not mapped from the source are deleted.
Target files that are up-to-date with source files (by modification time) are not regenerated.

The transcoding is performed by a gstreamer pipeline that depends on an “addtagmux” element.
Such is supported by https://github.com/rtyle/gstaddtagmux

## Usage

(cd Music; ~/xtsync/xtsync.py)
