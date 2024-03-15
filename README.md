# xtsync

Synchronize a transcoded/filtered view of files from a source to a target tree.

This synchronizes a FLAC (lossless, large) music library tree with an MP3 (lossy, smaller) view.
The target MP3 tree may then be distributed on portable media (say, with rsync) for use by players.

The ./source library consists of FLAC and MP3 files (all other files are ignored).
Source FLAC files are transcoded to MP3 in the ./target tree
and will include, potentially, an embedded, scaled, front-cover tag
from a source-adjacent folder.jpg file.
Source MP3 files are hard linked to in the target.

Target files that are not mapped from the source are deleted.
Target files that are up-to-date with source files (by modification time) are not regenerated.

The transcoding is performed by a gstreamer pipeline that depends on an “addtagmux” element.
Such is supported by the gstaddtagmux submodule.

## Deployment

Git this repository as appropriate. For examples,

    git clone https://github.com/rtyle/xtsync.git
    git clone git@github.com:rtyle/xtsync.git

Update all submodules of this repository.

    git submodule update --init --recursive

Build gstaddmux submodule

    (cd gstaddtagmux; make)

## Usage

(cd Music; ~/xtsync/xtsync.py)
