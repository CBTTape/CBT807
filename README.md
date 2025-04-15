# CBT807
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. 
Due to amazing work by Alison Zhang and Jake Choi repos are no longer deleted.

```
//***FILE 807 is from Morris Karlin, Norman Lindner, and Irwin      *   FILE 807
//*           Eisenstein, and contains their programs HFSELECT      *   FILE 807
//*           and SUPRDUMP.  These programs were originally for     *   FILE 807
//*           sale, but Morris Karlin and Norman Lindner have       *   FILE 807
//*           given permission for them to be included on the       *   FILE 807
//*           CBT Tape collection, subject to CBT Tape disclaimers  *   FILE 807
//*           and conditions.                                       *   FILE 807
//*                                                                 *   FILE 807
//*     HFSELECT is a powerful file selection and match-merge       *   FILE 807
//*           program, which has additional capabilities, as        *   FILE 807
//*           described below.                                      *   FILE 807
//*                                                                 *   FILE 807
//*     SUPRDUMP is a program that can read, copy, and print the    *   FILE 807
//*           contents of a large variety of tapes.                 *   FILE 807
//*                                                                 *   FILE 807
//*     These programs were reworked for HLASM and z/OS by Morris   *   FILE 807
//*     Karlin, who is their principal author.                      *   FILE 807
//*                                                                 *   FILE 807
//*           email:  Morris_Karlin@bmc.com                         *   FILE 807
//*                   morris.karlin@gmail.com                       *   FILE 807
//*                                                                 *   FILE 807
//*                    HFSELECT  -  Introduction                    *   FILE 807
//*                                                                 *   FILE 807
//*          HFSELECT is an easy to use parameter-driven high       *   FILE 807
//*     performance utility program that can selectively            *   FILE 807
//*     retrieve, reject, count, print and sequence check           *   FILE 807
//*     records of an input file. The selection, rejection, etc.    *   FILE 807
//*     can be based on record contents, record position within     *   FILE 807
//*     a file, or by comparison with another file.  Extensive      *   FILE 807
//*     statistics of the input and output files are printed by     *   FILE 807
//*     HFSELECT.                                                   *   FILE 807
//*                                                                 *   FILE 807
//*          HFSELECT performs file or record matching of two       *   FILE 807
//*     input files and optionally can merge the matched records    *   FILE 807
//*     onto a separate output file.                                *   FILE 807
//*                                                                 *   FILE 807
//*          HFSELECT performs VTOC, catalog and PDS directory      *   FILE 807
//*     searches and outputs formatted records of the results.      *   FILE 807
//*     It can recursively call itself for each dsn/member in       *   FILE 807
//*     these formatted records.                                    *   FILE 807
//*                                                                 *   FILE 807
//*          The program can replace a character string by          *   FILE 807
//*     another within a given range in a record.  It can           *   FILE 807
//*     encrypt selected fields to create test files from           *   FILE 807
//*     sensitive or confidential data sets, or to convert data     *   FILE 807
//*     from one format to another.                                 *   FILE 807
//*                                                                 *   FILE 807
//*          The input file can be a physical sequential (PS)       *   FILE 807
//*     data set (QSAM), an indexed sequential (IS) data set        *   FILE 807
//*     (QISAM), a VSAM data set (VSAM) or a partitioned            *   FILE 807
//*     organization (PO) data set (BPAM).                          *   FILE 807
//*                                                                 *   FILE 807
//*          The record formats for QSAM, ISAM and BPAM input       *   FILE 807
//*     files can be fixed, variable, undefined, blocked,           *   FILE 807
//*     spanned, standard or any valid combination of these         *   FILE 807
//*     formats.  All VSAM data sets except variable spanned can    *   FILE 807
//*     be processed.  The input files are always read              *   FILE 807
//*     sequentially. VSAM files may be read either sequentially    *   FILE 807
//*     by key or by physical sequential RBA.                       *   FILE 807
//*                                                                 *   FILE 807
//*          Multiple output files may be generated, depending      *   FILE 807
//*     upon the option and suboptions selected, and on the JCL.    *   FILE 807
//*     The output files may be sequential, VSAM or PDS. Thus       *   FILE 807
//*     HFSELECT may be used to copy sequential, PDS or VSAM        *   FILE 807
//*     files, or to convert ISAM, VSAM or PDS files to             *   FILE 807
//*     sequential files or VSAM files.  In addition, variable      *   FILE 807
//*     format files may be converted to fixed format files.        *   FILE 807
//*     Output file LRECLs and BLKSIZEs may differ from their       *   FILE 807
//*     corresponding input files.                                  *   FILE 807
//*                                                                 *   FILE 807
//*          The output files may be directed to any system         *   FILE 807
//*     storage device (tape, disk, etc.), or any or all of the     *   FILE 807
//*     output files may be printed either unformatted, in          *   FILE 807
//*     character, character and HEX format, or character with a    *   FILE 807
//*     ruler line.                                                 *   FILE 807
//*                                                                 *   FILE 807
//*          User exits may be used to modify standard HFSELECT     *   FILE 807
//*     features, and also to modify records before and after       *   FILE 807
//*     processing.                                                 *   FILE 807
//*                                                                 *   FILE 807
//*          Thus, instead of writing and debugging a program       *   FILE 807
//*     each time selection of records from a file is required,     *   FILE 807
//*     HFSELECT steps may be written in a few minutes to obtain    *   FILE 807
//*     the desired results.                                        *   FILE 807
//*                                                                 *   FILE 807
//*                    SUPRDUMP  -  Introduction                    *   FILE 807
//*                                                                 *   FILE 807
//*          SUPRDUMP is an easy-to-use utility print program       *   FILE 807
//*          designed to                                            *   FILE 807
//*                                                                 *   FILE 807
//*           - copy an entire tape volume to one output tape       *   FILE 807
//*             volume                                              *   FILE 807
//*           - print datasets, in whole or in part, from any       *   FILE 807
//*             system storage device.                              *   FILE 807
//*           - show the characteristics of all data sets on a      *   FILE 807
//*             tape volume, including labels, formats (ASCII or    *   FILE 807
//*             EBCDIC) and tapemarks for tapes with blocksizes     *   FILE 807
//*             of up to 65535 bytes.                               *   FILE 807
//*           - show the position and attributes of files, and      *   FILE 807
//*             the position of tapemarks on tape volumes.          *   FILE 807
//*           - print files in hex, with simultaneous               *   FILE 807
//*             interpretation of each character in both ASCII      *   FILE 807
//*             and EBCDIC format.                                  *   FILE 807
//*                                                                 *   FILE 807
//*          SUPRDUMP is parameter-driven, with the parameters      *   FILE 807
//*     coded in the PARM of the EXECute statement. All             *   FILE 807
//*     parameters are keywords and all have defaults so that       *   FILE 807
//*     none need be explicitly specified.                          *   FILE 807
//*                                                                 *   FILE 807
//*          Information messages displayed by the program are      *   FILE 807
//*                                                                 *   FILE 807
//*           - PARM coded on the EXECute statement                 *   FILE 807
//*           - Jobname, Stepname and Procstepname of SUPRDUMP      *   FILE 807
//*             job & step                                          *   FILE 807
//*           - output tape characteristics and a summary of        *   FILE 807
//*             copied files                                        *   FILE 807
//*           - DSN coded on the input file (SYSUT1) DD             *   FILE 807
//*             statement                                           *   FILE 807
//*           - maximum block size in the file                      *   FILE 807
//*           - minimum block size in the file                      *   FILE 807
//*             (excluding the last block)                          *   FILE 807
//*           - size of the last block on the file                  *   FILE 807
//*           - total number of bytes in the file                   *   FILE 807
//*           - total number of blocks in the file                  *   FILE 807
//*           - for tape, the sequence number of the file on the    *   FILE 807
//*               tape, the density, and the recording mode         *   FILE 807
//*               technique                                         *   FILE 807
//*           - serial number of the volume containing the file     *   FILE 807
//*           - change in BLKSIZE messages (with relative block     *   FILE 807
//*             number)                                             *   FILE 807
//*           - RECFM and LRECL of each data set                    *   FILE 807
//*           - Creation and Expiration dates                       *   FILE 807
//*           - Approximate tape length of each tape file, and      *   FILE 807
//*               the approximate total tape length of all          *   FILE 807
//*               processed files                                   *   FILE 807
//*                                                                 *   FILE 807
//*          The SYSUT1 input file record formats may be fixed,     *   FILE 807
//*     variable, undefined, blocked, spanned, standard or any      *   FILE 807
//*     valid combination of these formats, but the file must be    *   FILE 807
//*     physical sequential.  The RECFM, LRECL and BLKSIZE of       *   FILE 807
//*     these files need not be known before- hand.  One file in    *   FILE 807
//*     print format (SYSUT2) is generated and one output tape      *   FILE 807
//*     volume may be created (TAPECOPY). The printout can be in    *   FILE 807
//*     any one of five display formats. Variable-length records    *   FILE 807
//*     can be printed in readable form.  It shows all bytes of     *   FILE 807
//*     the block including the BDW and the RDW if any.             *   FILE 807
//*                                                                 *   FILE 807
//*          An optional output file can be coded to capture        *   FILE 807
//*     status and sense bytes from reads of tape/cartridge data    *   FILE 807
//*     sets.                                                       *   FILE 807
//*                                                                 *   FILE 807
```
