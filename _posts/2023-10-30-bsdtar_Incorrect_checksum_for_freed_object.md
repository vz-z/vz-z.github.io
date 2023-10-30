---
title: bsdtar Incorrect checksum for freed object
layout: default
filename: 2023-10-30-bsdtar_Incorrect_checksum_for_freed_object.md
date: 2023-10-30 00:00:00 +0900
categories: category
tags:
- GitHubPages
--- 

# bsdtar bug?
compressing a directory including 1million (30GB in total) files using `tar` command (bsdtar), a fatal error occurs.  
I googled, however, no related information found.
```bash
$ tar -cv --cd ~/path -f - .
tar(84564,0x1db241ec0) malloc: Incorrect checksum for freed object 0x1262041a8: probably modified after being freed.
Corrupt value: 0x77779982e39f81e3
tar(84564,0x1db241ec0) malloc: *** set a breakpoint in malloc_error_break to debug
```

try another version of tar (GNU-tar), no error occured.
```bash
$ brew install gnu-tar
$ (cd ~/path/; gtar -cv -f - .)
```
# Environment
M1 Mac Mini 2020  
macOS Sonoma 14.1（23B74）  
bsdtar 3.5.3 - libarchive 3.5.3 zlib/1.2.12 liblzma/5.0.5 bz2lib/1.0.8 
