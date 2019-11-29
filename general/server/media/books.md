---
uid: server-media-books
title: Books
---

# Music

The most common organization scheme for books is separation by Audiobook then by Author.

```
/Books
    /Audiobooks
        /Author
            Book1.flac
            Book2.flac
    /Books
        /Author
            Book1.epub
            Book2.mp3
```

```

## Images

Images will be scraped from album or artist folders, and they can also be embedded in the music files themselves. The supported filenames are listed below for each respective image.

### Primary

  * folder
  * poster
  * cover
  * default

### Art

  * clearart

### Backdrop

Multiple backdrop images can be used to cycle through several over time. Simply append a number to the end of the filename directly after or after a hyphen.

  * backdrop
  * fanart
  * background
  * art
  * extrafanart

### Banner

  * banner

### Logo

  * logo

### Thumb

  * thumb
  * landscape
