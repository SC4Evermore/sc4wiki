---
title: "MAD"
description: ""
published: true
date: '2019-08-09T02:54:59Z'
tags: ["File Formats/SC4", "MTS2"]
editor: markdown
dateCreated: '2009-01-03T16:05:24Z'
---

> **Note:** Parts of this article were copied from the old ModTheSims2 Wiki (2003–2006) and may be out of date.

**MAD** is the the video format that is responsible for the opening movies. They are divided into alternating video and audio blocks that accompany each other. The audio blocks are known to be EA ASF STR Audio, however the video blocks are significantly different and use an EA specific type. Its possible they use [ASF](https://en.wikipedia.org/wiki/ASF) video compression, but they contain a very modified header.

The whole format is really a one block video, one block audio, repeat.

## MAD File Structure

### Video Blocks

The following is the specification of the video blocks of the MAD file, by [Hayly](/people/hayly), [DarkMatter](/people/darkmatter), and [Karybdis](/people/karybdis):

**Header:**

`DWORD - MAD* - Identifier of chunk where * is a unique chunk type identifier (see below).`  
`DWORD - Size of the frame chunk`  
`DWORD - Unknown (0)`  
`WORD  - Max Data rate per Sec. (ABAA normally. Max bytes needed to present the video properly per sec)`  
`WORD  - Delay, in microseconds, per frame.  The standard is 66ms or 15 frames a second.  This indicates file timing.`  
`WORD  - Pixel width of the frame chunk.`  
`WORD  - Pixel height of the frame chunk.`  
`BYTE  - Unknown`  
`BYTE  - Frame quantization`  
`BYTE  - In TS2 movies, chunk type. 02 = B-frame, 00 = P-frame, 01 = I-frame. In SC4 movies, blank.`  
`BYTE  - Unknown (0)`

**MAD Types:**

`---k = Intra Coded Keyframes (I-Frame) (estimated size, 30 byte block)`  
`---m = Predictive coded (previous) frames (P-Frame) (estimated 18 byte block)`  
`---e = Bidirectionally-predictive coded (both previous and following) frames (B-frame) (estimated 18 byte block)`

Note that e-types are only present in TS2 movies and not SC4.

SC4 uses a KMMMM KMMMM format with a keyframe every 5 frames. TS2 uses a KEMEMEMEMEMEME KEMEMEMEMEMEME format with a keyframe every 14 frames.

Video Data - Each video chunk has readable data blocks with a size dependent on its identifier (k,m,e). The codec details can be found [here](http://wiki.multimedia.cx/index.php?title=Electronic_Arts_MAD).

[FFmpeg](http://ffmpeg.org) can display and convert MAD files.

### Audio Blocks

The following document is by Valery V. Anisimovsky (samael@avn.mccme.ru), in three sections, and has been reproduced in Wiki format below.

#### .ASF/.STR Music Files (MAD Audio chunks)

The music in many new Electronic Arts games is in .ASF stand-alone files (sometimes ASF files have extension .STR). These files have the block structure analogous to RIFF. Namely, these files are divided into blocks (without any global file header like RIFFs have). Each block has the following header:

    struct ASFBlockHeader
    {
      char  szBlockID[4];
      DWORD dwSize;
    };

    szBlockID -- string ID for the block.

    dwSize -- size of the block (in bytes) INCLUDING this header.

Further I'll describe the contents of blocks of all block types in .ASF file. When I say "block begins with..." that means "the contents of that block (which begin just after ASFBlockHeader) begin with...". Quoted strings are block IDs.

**SCH1: Header Block:**

This is the first block in ASF. In the most of files this block begins with the ID string "PT\0\0" (or number 0x50540000). Further goes the PT header data which describes audio data in the file. This PT header should be parsed rather than just read as a simple structure. Here I give the parsing code. These functions use fread() and fseek() stdio functions.

    '' first of all, we need a function which reads a small (variable) number
    '' bytes and composes a DWORD of them. Note that such DWORD will be a kind
    '' of big-endian (Motorola) stored, e.g. 3 consecutive bytes 0x12 0x34 0x56
    '' will give a DWORD 0x00123456.
    DWORD ReadBytes(FILE* file, BYTE count)
    {
      BYTE  i, byte;
      DWORD result;

      result=0L;
      for (i=0;i<count;i++)
      {
        fread(&byte,sizeof(BYTE),1,file);
        result<<=8;
        result+=byte;
      }

      return result;
    }

    '' these will be set by ParsePTHeader
    DWORD dwSampleRate;
    DWORD dwChannels;
    DWORD dwCompression;
    DWORD dwNumSamples;
    DWORD dwDataStart;
    DWORD dwLoopOffset;
    DWORD dwLoopLength;
    DWORD dwBytesPerSample;
    BYTE  bSplit;
    BYTE  bSplitCompression;

    '' Here goes the parser itself
    '' This function assumes that the current file pointer is set to the
    '' start of PT header data, that is, just after PT string ID "PT\0\0"

    void ParsePTHeader(FILE* file)
    {
      BYTE byte;
      BOOL bInHeader, bInSubHeader;

      bInHeader=TRUE;
      while (bInHeader)
      {
        fread(&byte,sizeof(BYTE),1,file);
        switch (byte) '' parse header code
        {
          case 0xFF: '' end of header
           bInHeader=FALSE;
          case 0xFE: '' skip
          case 0xFC: '' skip
           break;
          case 0xFD: '' subheader starts...
           bInSubHeader=TRUE;
           while (bInSubHeader)
           {
             fread(&byte,sizeof(BYTE),1,file);
             switch (byte) '' parse subheader code
             {
               case 0x82:
                fread(&byte,sizeof(BYTE),1,file);
                dwChannels=ReadBytes(file,byte);
                break;
               case 0x83:
                fread(&byte,sizeof(BYTE),1,file);
                dwCompression=ReadBytes(file,byte);
                break;
               case 0x84:
                fread(&byte,sizeof(BYTE),1,file);
                dwSampleRate=ReadBytes(file,byte);
                break;
               case 0x85:
                fread(&byte,sizeof(BYTE),1,file);
                dwNumSamples=ReadBytes(file,byte);
                break;
               case 0x86:
                fread(&byte,sizeof(BYTE),1,file);
                dwLoopOffset=ReadBytes(file,byte);
                break;
               case 0x87:
                fread(&byte,sizeof(BYTE),1,file);
                dwLoopLength=ReadBytes(file,byte);
                break;
               case 0x88:
                fread(&byte,sizeof(BYTE),1,file);
                dwDataStart=ReadBytes(file,byte);
                break;
               case 0x92:
                fread(&byte,sizeof(BYTE),1,file);
                dwBytesPerSample=ReadBytes(file,byte);
                break;
               case 0x80: '' ???
                fread(&byte,sizeof(BYTE),1,file);
                bSplit=ReadBytes(file,byte);
                break;
               case 0xA0: '' ???
                fread(&byte,sizeof(BYTE),1,file);
                bSplitCompression=ReadBytes(file,byte);
                break;
               case 0xFF:
                subflag=FALSE;
                flag=FALSE;
                break;
               case 0x8A: '' end of subheader
                bInSubHeader=FALSE;
               default: '' ???
                fread(&byte,sizeof(BYTE),1,file);
                fseek(file,byte,SEEK_CUR);
             }
           }
           break;
          default:
           fread(&byte,sizeof(BYTE),1,file);
           if (byte==0xFF)
              fseek(file,4,SEEK_CUR);
           fseek(file,byte,SEEK_CUR);
        }
      }
    }

dwSampleRate -- Sample rate for the file. Note that headers of most of ASFs/MUSes I've seen DO NOT contain sample rate subheader section. Currently I just set sample rate for such files to the default: 22050 Hz. It seems to work okay.

dwChannels -- Number of channels for the file: 1 for mono, 2 for stereo. If this is NOT set by ParsePTHeader, then you may use the default: stereo.

dwCompression -- Compression tag. If this is 0x00, then no compression is used and audio data is signed 16-bit PCM. If this is 0x07, the audio data is compressed with EA ADPCM algorithm. Please read the next section for the description of EA ADPCM decompression scheme. In some files this tag is omitted - I use 0x00 (no compression) for them.

dwNumSamples -- Number of samples in the file.

dwDataStart -- In ASF files this's not used.

dwLoopOffset -- Offset when looping (from start of sound part).

dwLoopLength -- Length when looping.

dwBytesPerSample -- Bytes per sample (Default is 2). Divide this by dwChannels to get resolution of sound data.

bSplit -- This looks like to be 0x01 for files using "split" SCDl blocks (see below). If this subheader field is absent, the file uses "normal" (interleaved) SCDl blocks.

bSplitCompression -- This looks like to be 0x08 for files using non-compressed "split" SCDl blocks. If this subheader field is absent in the file using "split" SCDls, the file uses EA ADPCM compression. This subheader field should not appear in a file using "normal" (interleaved) SCDls.

**SCC1: Count Block:**

This block goes after "SCH1" and contains one DWORD value which is a number of "SCD1" data blocks in ASF file.

**SCD1: Data Block:**

These blocks contain audio data. Depending on the parameters set in the header (see above) SCDl block may contain compressed (by EA ADPCM or IMA ADPCM) or non-compressed audio data and the data itself may be interleaved or split (see below).

If no compression is used and the file does not use "split" SCDl blocks, SCDl block begins with a DWORD value which is the number of samples in this block and after that comes signed 16-bit PCM data, in the interleaved form:

`LRLR...LR (L and R are 16-bit sample values for left and right channels).`

Hereafter by "chunk" I mean the audio data in the "SCD1" data block, that is, compressed/non-compressed data which starts after chunk header.

In the newer EA games (NHL'2000/NBA'2000/FIFA'99'2000/NFS5) non-compressed "split" SCD1 blocks are used. These blocks begin with a chunk header:

    struct ASFSplitPCMChunkHeader
    {
      DWORD dwOutSize;
      DWORD dwLeftChannelOffset;
      DWORD dwRightChannelOffset;
    }

dwOutSize -- Size of audio data in this chunk (in samples).

dwLeftChannelOffset, dwRightChannelOffset -- Offsets to PCM data for left and right channels, relative to the byte which immediately follows ASFSplitPCMChunkHeader structure. E.g. for left channel this offset is zero - the data starts immediately after this structure.

After this structure comes PCM data for stereo wavestream and it's not interleaved (LRLRLR...), but it's split: first go sample values for left channel, then -- for right channel, that is the layout is LL...LRR...R.

If EA ADPCM (or IMA ADPCM) compression is used, but the file does not use "split" SCDls, each SCDl block begins with a chunk header:

    struct ASFChunkHeader
    {
      DWORD dwOutSize;
      SHORT lCurSampleLeft;
      SHORT lPrevSampleLeft;
      SHORT lCurSampleRight;
      SHORT lPrevSampleRight;
    };

dwOutSize -- Size of decompressed audio data in this chunk (in samples).

lCurSampleLeft, lCurSampleRight, lPrevSampleLeft, lPrevSampleRight Are initial values for EA ADPCM decompression routine for this data block (for left and right channels respectively). I'll describe the usage of these further when I get to EA ADPCM decompression scheme.

Note that the structure above is ONLY for stereo files. For mono there are just no lCurSampleRight, lPrevSampleRight fields. If IMA ADPCM compression is used, the meanings of some chunk header fields are different -- see my EA-ASF.TXT specs for details. After this chunk header the compressed data comes. See the next section for EA ADPCM decompression scheme description.

If EA ADPCM (or IMA ADPCM) compression is used and the file uses "split" SCDls, each SCDl block begins with a different chunk header:

    struct ASFSplitChunkHeader
    {
      DWORD dwOutSize;
      DWORD dwLeftChannelOffset;
      DWORD dwRightChannelOffset;
    };
    SHORT lCurSampleLeft;
    SHORT lPrevSampleLeft;
    BYTE  bLeftChannelData[]; '' compressed data for left channel goes here...
    SHORT lCurSampleRight;
    SHORT lPrevSampleRight;
    BYTE  bRightChannelData[]; '' compressed data for right channel goes here...

dwOutSize -- Size of decompressed audio data in this chunk (in samples).

dwLeftChannelOffset, dwRightChannelOffset -- Offsets to compressed data for left and right channels, relative to the byte which immediately follows ASFSplitChunkHeader structure. E.g. for left channel this offset is zero - the data starts immediately after this structure.

lCurSampleLeft, lCurSampleRight, lPrevSampleLeft, lPrevSampleRight have the same meaning as above, but note that these values are SHORTs.

So, use mono decoder for each channel data and then create normal LRLR... stereo waveform before outputting. Such (newer) files may be separated from the others by presence of 0x80 type section in PT header (the value stored in the section is 0x01 for such files). Some of such files also do not contain compression type (0x83) section in their PT header.

**SCL1: Loop Block:**

This block defines looping point for the song. It contains only DWORD value, which is the looping jump position (in samples) relative to the start of the song. You should make the jump just when you encounter this block.

**SCE1: End Block:**

This block indicates the end of audio stream.

Note that in some games audio files are contained within game resources. As a rule, such resources are not compressed/encrypted, so you may just search for ASF file signature (e.g. "SCH1") and this will mark the beginning of audio stream, while "SCE1" block marks the end of that stream.

#### EA ADPCM Decompression Algorithm

During the decompression four LONG variables must be maintained for stereo stream: lCurSampleLeft, lCurSampleRight, lPrevSampleLeft, lPrevSampleRight, and two LONG variables for mono stream: lCurSample, lPrevSample. At the beginning of each "SCDl" data block you must initialize these variables using the values in ASFChunkHeader. Note that LONG here is signed.

Here's the code which decompresses one "SCD1" block of EA ADPCM compressed stereo stream.

    BYTE  InputBuffer[InputBufferSize]; '' buffer containing audio data of "SCDl" block
    BYTE  bInput;
    DWORD dwOutSize;                    '' outsize value from the ASFChunkHeader
    DWORD i, bCount, sCount;
    LONG  c1left,c2left,c1right,c2right,left,right;
    BYTE  dleft,dright;

    DWORD dwSubOutSize=0x1c;

    i=0;

    '' process integral number of (dwSubOutSize) samples
    for (bCount=0;bCount<(dwOutSize/dwSubOutSize);bCount++)
    {
      bInput=InputBuffer[i++];
      c1left=EATable[HINIBBLE(bInput)];    '' predictor coefficients for left channel
      c2left=EATable[HINIBBLE(bInput)+4];
      c1right=EATable[LONIBBLE(bInput)];   '' predictor coefficients for right channel
      c2right=EATable[LONIBBLE(bInput)+4];
      bInput=InputBuffer[i++];
      dleft=HINIBBLE(bInput)+8;            '' shift value for left channel
      dright=LONIBBLE(bInput)+8;           '' shift value for right channel
      for (sCount=0;sCount<dwSubOutSize;sCount++)
      {
        bInput=InputBuffer[i++];
        left=HINIBBLE(bInput);         '' HIGHER nibble for left channel
        right=LONIBBLE(bInput);        '' LOWER nibble for right channel
        left=(left<<0x1c)>>dleft;
        right=(right<<0x1c)>>dright;
        left=(left+lCurSampleLeft*c1left+lPrevSampleLeft*c2left+0x80)>>8;
        right=(right+lCurSampleRight*c1right+lPrevSampleRight*c2right+0x80)>>8;
        left=Clip16BitSample(left);
        right=Clip16BitSample(right);
        lPrevSampleLeft=lCurSampleLeft;
        lCurSampleLeft=left;
        lPrevSampleRight=lCurSampleRight;
        lCurSampleRight=right;

        '' Now we've got lCurSampleLeft and lCurSampleRight which form one stereo
        '' sample and all is set for the next input byte...
        Output((SHORT)lCurSampleLeft,(SHORT)lCurSampleRight);  '' sends the sample to output
      }
    }

    '' process the rest (if any)
    if ((dwOutSize % dwSubOutSize) != 0)
    {
      bInput=InputBuffer[i++];
      c1left=EATable[HINIBBLE(bInput)];     '' predictor coefficients for left channel
      c2left=EATable[HINIBBLE(bInput)+4];
      c1right=EATable[LONIBBLE(bInput)];    '' predictor coefficients for right channel
      c2right=EATable[LONIBBLE(bInput)+4];
      bInput=InputBuffer[i++];
      dleft=HINIBBLE(bInput)+8;             '' shift value for left channel
      dright=LONIBBLE(bInput)+8;            '' shift value for right channel
      for (sCount=0;sCount<(dwOutSize % dwSubOutSize);sCount++)
      {
        bInput=InputBuffer[i++];
        left=HINIBBLE(bInput);          '' HIGHER nibble for left channel
        right=LONIBBLE(bInput);         '' LOWER nibble for right channel
        left=(left<<0x1c)>>dleft;
        right=(right<<0x1c)>>dright;
        left=(left+lCurSampleLeft*c1left+lPrevSampleLeft*c2left+0x80)>>8;
        right=(right+lCurSampleRight*c1right+lPrevSampleRight*c2right+0x80)>>8;
        left=Clip16BitSample(left);
        right=Clip16BitSample(right);
        lPrevSampleLeft=lCurSampleLeft;
        lCurSampleLeft=left;
        lPrevSampleRight=lCurSampleRight;
        lCurSampleRight=right;

        '' Now we've got lCurSampleLeft and lCurSampleRight which form one stereo
        '' sample and all is set for the next input byte...
        Output((SHORT)lCurSampleLeft,(SHORT)lCurSampleRight);  '' sends the sample to output
      }
    }

HINIBBLE and LONIBBLE are higher and lower 4-bit nibbles:

`#define HINIBBLE(byte) ((byte) >> 4)`  
`#define LONIBBLE(byte) ((byte) & 0x0F)`

Note that depending on your compiler you may need to use additional nibble separation in these defines, e.g. (((byte) \>\> 4) & 0x0F).

EATable is the table given in the next section of this document.

Output() is just a placeholder for any action you would like to perform for decompressed sample value.

Clip16BitSample is quite evident:

    LONG Clip16BitSample(LONG sample)
    {
      if (sample>32767)
         return 32767;
      else if (sample<-32768)
         return (-32768);
      else
         return sample;
    }

As to mono sound, it's just analoguous: dwSubOutSize=0x0E for mono and you should get predictor coeffs and shift from one byte:

    bInput=InputBuffer[i++];
    c1=EATable[HINIBBLE(bInput)];    '' predictor coefficients
    c2=EATable[HINIBBLE(bInput)+4];
    d=LONIBBLE(bInput)+8;            '' shift value

And also you should process HIGHER nibble of the input byte first and then LOWER nibble for mono sound.

Of course, this decompression routine may be greatly optimized.

#### EA ADPCM Table

    LONG EATable[]=
    {
      0x00000000,
      0x000000F0,
      0x000001CC,
      0x00000188,
      0x00000000,
      0x00000000,
      0xFFFFFF30,
      0xFFFFFF24,
      0x00000000,
      0x00000001,
      0x00000003,
      0x00000004,
      0x00000007,
      0x00000008,
      0x0000000A,
      0x0000000B,
      0x00000000,
      0xFFFFFFFF,
      0xFFFFFFFD,
      0xFFFFFFFC
    };
