---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page
title: HEVC Large Scale Dataset
#permalink: /resources/large_scale_dataset_HEVC
---

The group has been developing a database of HEVC-encoded video sequences to investigate the characteristics of several objective Video Quality Measures (VQMs).

## Dataset

The whole dataset can be downloaded from this FTP: [ftp://ftp.ivc.polytech.univ-nantes.fr/VQEG/JEG/HYBRID/hevc_database/](ftp://ftp.ivc.polytech.univ-nantes.fr/VQEG/JEG/HYBRID/hevc_database/) (Note: ~300 GB)

Folders:

* ENC : compressed video sequences (59,520 sequences)
* FR : available quality measures (see below)
* SRC : uncompressed original video sequences used for encoding and quality measures (10 sequences x 3 resolutions)

Sequences (from src01 to src10):

![src01]({{site.baseurl}}/images/Db_hevc_src01.jpg "src01"){: style="padding:5px"}
![src02]({{site.baseurl}}/images/Db_hevc_src02.jpg "src02"){: style="padding:5px"}
![src03]({{site.baseurl}}/images/Db_hevc_src03.jpg "src03"){: style="padding:5px"}
![src04]({{site.baseurl}}/images/Db_hevc_src04.jpg "src04"){: style="padding:5px"}
![src05]({{site.baseurl}}/images/Db_hevc_src05.jpg "src05"){: style="padding:5px"}
![src06]({{site.baseurl}}/images/Db_hevc_src06.jpg "src06"){: style="padding:5px"}
![src07]({{site.baseurl}}/images/Db_hevc_src07.jpg "src07"){: style="padding:5px"}
![src08]({{site.baseurl}}/images/Db_hevc_src08.jpg "src08"){: style="padding:5px"}
![src09]({{site.baseurl}}/images/Db_hevc_src09.jpg "src09"){: style="padding:5px"}
![src10]({{site.baseurl}}/images/Db_hevc_src10.jpg "src10"){: style="padding:5px"}

[//]: # (COMMENT ![src02]({{site.baseurl}}/images/HD_SRC_02.jpg) )

### Key to compressed file naming

Example filename:

    src01_960x544p25.yuv_LDGOP4_8000001_2_16_64_8_4.265

Convention

    src<SEQN>_<WIDTH>x<HEIGHT>p25.yuv_<GOPTYPESIZE>_<RATECONTROL>_<REFRESH>_<INTRAPERIOD>_<SEARCHRANGE>_<BITDEPTH>_<SLICEARGUMENT>.265

Meaning of parameters (Refer to https://hevc.hhi.fraunhofer.de/svn/svn_HEVCSoftware/branches/HM-11.0-dev/doc/software-manual.pdf for further details on the encoder)

SEQN = sequence number, from 01 to 10

WIDTH = picture width, possibile values: 960, 1280, 1920

HEIGHT = picture height, possibile values: 544, 720, 1080

GOPTYPESIZE = GOP type and size, possibile values: GOP2, GOP4, GOP8, LDGOP4

    GOP2 : GOP size 2
    GOP4 : GOP size 4
    GOP8 : GOP size 8
    LDGOP4 : GOP size 4 in low-delay configuration

RATECONTROL = parameter for rate control, possibile values: 26, 32, 38, 46 or a number >= 500000 (ending with 0 or 1)

    The number <= 46 corresponds to the -q encoder option
    The number >= 500000 corresponds to the --TargetBitrate encoder option
    The last digit (0 or 1) if number >= 500000 corresponds to the --LCULevelRateControl encoder option
      26 : fixed QP = 26
      32 : fixed QP = 32
      38 : fixed QP = 38
      46 : fixed QP = 46
      500000 : rate control at the frame level, 500 kbit/s
      500001 : rate control at the LCU level, 500 kbit/s
      1000000 : rate control at the frame level, 1 Mbit/s
      1000001 : rate control at the LCU level, 1 Mbit/s
      2000000 : rate control at the frame level, 2 Mbit/s
      2000001 : rate control at the LCU level, 2 Mbit/s
      4000000 : rate control at the frame level, 4 Mbit/s
      4000001 : rate control at the LCU level, 4 Mbit/s
      8000000 : rate control at the frame level, 8 Mbit/s
      8000001 : rate control at the LCU level, 8 Mbit/s
      16000000 : rate control at the frame level, 16 Mbit/s
      16000001 : rate control at the LCU level, 16 Mbit/s

REFRESH = intra refresh type, possible values: 1, 2

    The number corresponds to the --DecodingRefreshType encoder option
      1 : Applies a non-IDR clean random access point (open GOP).
      2 : Applies an IDR random access point (closed GOP).

INTRAPERIOD = intra frame period, possible values: 8, 16, 32, 64

    The number corresponds to the --IntraPeriod encoder option
      8 : one intra every 8
      16 : one intra every 16
      32 : one intra every 32
      64 : one intra every 64

SEARCHRANGE = search range for motion estimation (around the predictor), possibile values: only 64

    The number corresponds to the --SearchRange encoder option

BITDEPTH = bit depth used for coding, possibile values: only 8

    The number corresponds to the --InternalBitDepth encoder option

SLICEARGUMENT = specifies how slicing is performed for each picture, possibile values: 0, 2, 4, 1500

    The number corresponds to the --SliceMode and --SliceArgument encoder options
      0 : only one slice per frame
        (SliceMode = 0 and SliceArgument = 0)
      2 : 2 slices per frame (max 270,120,75 CTU per slice when WIDTH=1920,1280,960)
        (SliceMode = 1 and SliceArgument =  270 if 1920, 120 if 1280, 75 if 960)
      4 : 4 slices per frame (max 130,60,34 CTU per slice when WIDTH=1920,1280,960)
        (SliceMode = 1 and SliceArgument =  130 if 1920, 60 if 1280, 34 if 960)
      1500 : each slice is maximum 1500 bytes
        (SliceMode = 2 and SliceArgument = 1500)

## Downloads

### Database

The database of the original and processed video sequences can be downloaded via FTP at:

[ftp://ftp.ivc.polytech.univ-nantes.fr/VQEG/JEG/HYBRID/hevc_database/](ftp://ftp.ivc.polytech.univ-nantes.fr/VQEG/JEG/HYBRID/hevc_database/)

Please note that the whole database is larger than 300 GB. In particular:

* the SRC folder contains the original video sequences in YUV format
* the ENC folder contains the compressed files (.265 extension)

### Objective scores

Already computed objective scores are available in the FR folder:

* for PSNR, SSIM, VIFP: look for .csv files

  **FRmetricsAverage.csv** contains the final average value for each sequence.

  **FRmetricsFrameByFrame.csv** contains the detailed values for each frame, for each sequence.

* for VQM, PVQM: look for the .tar.bz2 files

  **results_vqm001_RES_converted.tar.bz2** contains the detailed values of VQM for each frame for each sequence at resolution RES (can be 960, 1280, 1920). One csv file per sequence is provided.

  **results_pvqm001_RES_converted.tar.bz2** contains the detailed values of PVQM for each frame for each sequence at resolution RES (can be 960, 1280, 1920). One csv file per sequence is provided.

In both cases, in each csv file, the line "final_value" contains the final value of the metric for that sequence.

For convienience, all final_value results are included in a single csv file available from FRmetricsAverage_pvqm_vqm_psnr054_ssim_vifp.csv.bz2. Note that in this case when the PSNR value of a single frame is infinite, the value has been clipped at 54.15 dB PSNR (hence the name psnr054). This happens for some sequences which have completely black frames which are encoded perfectly. The other SSIM and VIFP values are the same as the ones available in the FRmetricsAverage.csv file, and the data format is the same.

### Tools

The tools used to compute the scores:

* to compute PSNR, SSIM, VIFP: [VQMT](http://mmspg.epfl.ch/vqmt){: target=_blank}
* to compute VQM: [NTIA/ITS](http://www.its.bldrdoc.gov/resources/video-quality-research/software.aspx){: target=_blank}
* to compute PVQM: [PVQM_EM](http://media.polito.it/jeg){: target=_blank}
* [T-Labs HEVC packet loss toolchain](https://gitlab.com/vqeg/hevc_packet_loss_tool_chain){: target=_blank}

[//]: # (COMMENT### Preliminary Analysis  Some preliminary analysis of the data contained in the database is available in this result page)

## Current status

The database is composed of 59520 sequences (10 different contents at three different resolutions each, encoded with 1984 different encoding parameters).

For all 59520 HEVC sequences in the database, the following objective quality metrics are available:

* PSNR (as computed by the VQMT software)
* SSIM (as computed by the VQMT software)
* VIF (as computed by the VQMT software)
* VQM (as computed by the software available at NTIA/ITS)
* PVQM (as computed by the PVQM_EM software)

The database is currently being extended by computing the previous measures on sequences which have loss impairments. 25 different loss patterns are being used.

## Priority list

Since the work of expanding the database by computing the previous measures on sequences which have loss impairments is huge, a priority list has been agreed in the periodic bi-weekly JEG conference calls.

It has been suggested to prioritize the work according to three classes:

* **GOLD** - should always be done
* *SILVER* - should be done if possible
* BRONZE - the rest of the work

Other criteria include testing the extreme values first whenever reasonable.

The current proposal is:

Param/Values | Value 1 |Value 2 | Value 3|Value 4|Value 5|Value 6
-|-|-|-|-|-|-|
WIDTH|**960**|*1280*|**1920**|||
GOPTYPESIZE|**GOP2**|GOP4|**GOP8**|**LDGOP4**||
RATECONTROL_QP|**26**|32|38|**46**||
RATECONTROL_FRAME_kbit/s|**500**|1000|*2000*|**4000**|8000|*16000*|
RATECONTROL_LCU_kbit/s|500|*1000*|2000|4000|*8000*|16000|
REFRESH|**1**|2||||
INTRAPERIOD|**8**|16|32|**64**||
SLICEARGUMENT|**0**|2|*4*|**1500**||

Enrico is computing PSNR, SSIM, VIF, VQM, PVQM on several combinations of such parameters. As of Jan 19, 2015, all 960x544, subject to 25 different loss patterns, are available. Only a subset of sequences at 1280x720 and 1920x1080 are currently available. More information at: [http://media.polito.it/downloads/jeg/with_losses/](http://media.polito.it/downloads/jeg/with_losses/) (see also README file there).


Analysis
It is possible to visualize the quality metrics in the database by using the tool at [http://app.rawgraphs.io/](http://app.rawgraphs.io/){: target=_blank} Please note that all processing is done in the browser and processing about 60,000 entries requires 20-30 seconds per operation on a recent computer. Smaller sets (e.g., 2,000 lines, which are equivalent to all HRCs for one sequence at one resolution) are processed almost immediately.

To take the most advantage from the data available at [ftp://ftp.ivc.polytech.univ-nantes.fr/VQEG/JEG/HYBRID/hevc_database/FR/FRmetricsAverage.csv](ftp://ftp.ivc.polytech.univ-nantes.fr/VQEG/JEG/HYBRID/hevc_database/FR/FRmetricsAverage.csv) ([alternative link as zip file](FRmetricsAverage.zip)) the file has been preprocessed to isolate the main coding parameters in single columns. The preprocessed data, as well as some subsets based on the content type and resolution, has been made available by Enrico at [http://media.polito.it/downloads/jeg/encoding_quality/FRmetricsParams/](http://media.polito.it/downloads/jeg/encoding_quality/FRmetricsParams/) (content should be self-explaining from the filename).

To use the tool, cut&paste the content of a csv file from the latest link (or download and upload it) at [http://app.rawgraphs.io/](http://app.rawgraphs.io/){: target=_blank}, then choose a type of graph (e.g., scatter plot / bubble chart) and the columns that you want to use on x, y, point size and point color. For instance, x=psnr, y=ssim, point size=intrarefresh, pointcolor=slicetype gives something similar to the following graph:

![Src01 Res960 scatter plot example.png]({{site.baseurl}}/images/Src01_Res960_scatter_plot_example.png)
