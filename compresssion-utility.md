# Compress/Decompress Utility

By [Robert Sokoloski](https://github.com/rpsoko)

Let's do some cmprssn!

## Basic model:
Consider some bytestream (data) B. We apply some compression magic to it, yielding C(B). We send our friend the C(B) file over a network, and they can apply expansion magic to get back the original B. The result of compression and expansion is identical to the original bytestream.

    B -------->        C(B)      ------>       B

This is known as lossless compression, a common example is the .zip file format. There is also lossy compression, where expansion results in an approximation of the original. This is common in multimedia formats such at .jpg and .mp3 (look/listen closely and you can totally see/hear the difference).

## Warm-up DNA Compression:
Disclaimer: I'm not a biologist. Say we want to save a DNA strand to disk, but have limited disk space. A always gets paired with T, and G with C, like so:

    A  G  C  T
    |  |  |  |
    T  C  G  A

Since DNA follows strict rules, the bottom row of characters is redundant. We only need the following information to reconstruct the original sequence:

    AGCT

Cool, so we reduced our memory usage by half, but we can go further. Assuming ASCII encoding, each character above consumes 1 byte of memory. See if you can invent an encoding that will store all four characters in 1 byte of memory. Use that encoding to compress a strand.dna file into a strand.zipdna file and back.

## Huffman Coding:
I don't think I can write about this nearly as well as some other sources.
See:
* Robert Sedgewick, [Algorithms](http://algs4.cs.princeton.edu/55compression/), chapter 5.5
* Wikipedia, ["Huffman Coding"](http://en.wikipedia.org/wiki/Huffman_coding)
* Steven Skiena, [Algorithm Design Manual](http://sist.sysu.edu.cn/~isslxm/DSA/textbook/Skiena.-.TheAlgorithmDesignManual.pdf), sec. 18.5.

## Another Idea:
Play around with a lossy compression algorithm!
