# Overthewire Bandit Wargames - Aginthan Rathikumar

I have already completed the levels Bandit Level 1-11 so I am going to start the documentation from Level 12.

### LEVEL - 12

This is the command I used to ssh into the game server.

```bash
ssh -p 2220 bandit12@bandit.labs.overthewire.org
```

In the level the task was "The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions".

So first I started by creating a temporary directory in /tmp directory.

```bash
mkdir /tmp/randomdir
```

Next I copied the data.txt file to the /tmp/randomdir directory nnd navigated to that directory.

```bash
cp data.txt /tmp/randomdir/data.txt
cd /tmp/randomdir
```

Next I read the file using CAT command and found out that it is a hexdump file.

```bash
cat data.txt
00000000: 1f8b 0808 83c9 8768 0203 6461 7461 322e  .......h..data2.
00000010: 6269 6e00 013e 02c1 fd42 5a68 3931 4159  bin..>...BZh91AY
00000020: 2653 59b3 3d8a f800 0013 7fff dbf1 c7ff  &SY.=...........
00000030: fddb edf9 bfc3 7ffb 7ffb b59f dffd ffcf  ................
00000040: ffff 3fb7 bfff 77ff fedf bfdf b001 3168  ..?...w.......1h
00000050: 2000 0003 4000 001a 1a00 d003 41b5 001a   ...@.......A...
00000060: 0001 a0d3 40d3 201a 0006 8000 d343 4d00  ....@. ......CM.
00000070: 68d1 a068 0341 89ea 0f14 3a7a 8000 0000  h..h.A....:z....
00000080: 681a 0068 00c8 f506 8003 11a0 00d0 d00f  h..h............
00000090: 4803 4d0d 3d46 8006 8c81 a320 1a68 0068  H.M.=F..... .h.h
000000a0: 00d3 4000 1a20 6868 0019 0d00 6864 3200  ..@.. hh....hd2.
000000b0: d190 c806 80c2 0308 0640 d340 0064 6868  .........@.@.dhh
000000c0: 0680 01a0 341a 0064 000d 0001 a030 a002  ....4..d.....0..
000000d0: 0600 22f6 608a 8c07 4584 404b 6b8c e883  ..".`...E.@Kk...
000000e0: 1307 4f7e 9079 ef82 6c54 65f0 d2ec 59bf  ..O~.y..lTe...Y.
000000f0: f0a9 a424 69df 44c0 9321 a3fc 43c6 10ac  ...$i.D..!..C...
00000100: d909 6a89 e2c4 4801 35a1 9e48 a9da 21f4  ..j...H.5..H..!.
00000110: 9425 4ea5 6f8b 443a 1354 c192 724a 41ce  .%N.o.D:.T..rJA.
00000120: 7ac2 b460 0a58 993d edf3 a684 20c1 7e19  z..`.X.=.... .~.
00000130: 19de 3818 a633 54c3 4e1b 39e6 59aa 745d  ..8..3T.N.9.Y.t]
00000140: 714b 641f 68d7 c110 2ed7 2b27 10bb 6903  qKd.h.....+'..i.
00000150: 681d 2a8f bd9f d69b c854 2ebd b4b2 57ea  h.*......T....W.
00000160: 2747 3e5c 88ea 6c87 64fe a021 97c5 1ac4  'G>\..l.d..!....
00000170: 1c82 0cc9 774a 0322 2239 940a 0fb3 b525  ....wJ.""9.....%
00000180: f110 93f3 db38 2d9c e030 4c84 f2b8 b872  .....8-..0L....r
00000190: fb49 be6a 4378 4206 5ed3 baf1 a670 bca0  .I.jCxB.^....p..
000001a0: 0bb2 d690 b4e7 f4c0 2657 db18 3ac5 077f  ........&W..:...
000001b0: 5658 13a4 2fae ff04 77fb 87d8 79de e31c  VX../...w...y...
000001c0: cf7c a692 7882 8407 c56d 1442 e1ce 068b  .|..x....m.B....
000001d0: d791 b2a3 c666 e685 2372 11f1 0b77 bf28  .....f..#r...w.(
000001e0: 3ef2 6605 4760 ac1f 11d5 780e c9f2 6066  >.f.G`....x...`f
000001f0: 4ab9 9087 0a80 0461 660b e746 dbc0 44c1  J......af..F..D.
00000200: 247e 109a e4c1 e31b ebef 3814 b9b4 69e3  $~........8...i.
00000210: acea 7dbe 8b3d 107f b304 d825 183f 2bc4  ..}..=.....%.?+.
00000220: 7c3e 58c3 30d7 e181 b973 1c50 501a 7f90  |>X.0....s.PP...
00000230: 614e c3d2 290f 3da4 acba 33aa 4ca9 2082  aN..).=...3.L. .
00000240: 5bfc 7d5a fd0f 0431 3a03 3c27 f8bb 9229  [.}Z...1:.<'...)
00000250: c284 8599 ec57 c051 a8b0 353e 0200 00    .....W.Q..5>...
```

Next I converted the file to binary.

```bash
xxd -r data.txt > binary.txt

ls
binary.txt  data.txt

cat binary.txt
0"`E@Kk�O~y�Te���i�!C��j�H5H��%NoD:TrJA�´`hѠhA�:zhh��HM
X=� ~�3T��t]qKdh�.�'ih*֛�.W�G>\�d!��
                                   �J""9
%��8-�L�IjCxB^Ӻ�
                ֐�&W�:�VX/w���x�B�ב��r�w(>�G`��`fJ
af
  ��D$~���8i�}=�?+�>X��sPPaN�)=3L [}Z1:<')�Q5>
```

Next to find the type of the file.

```bash
file binary.txt 
binary.txt: gzip compressed data, was "data2.bin", last modified: Mon Jul 28 19:03:31 2025, max compression, from Unix, original size modulo 2^32 574
```

Since this text is compressed using gzip we can decompress using gunzip or gzip -d. Before that we have to rename the file to binary.txt --> binary.gz.

```bash
mv binary.txt binary.gz

gunzip binary.gz

cat binary 
0"`E@Kk�O~y�Te���i�!C��j�H5H��%NoD:TrJA�´`M
X=� ~�3T��t]qKdh�.�'ih*֛�.W�G>\�d!��
                                   �J""9
%��8-�L�IjCxB^Ӻ�
                ֐�&W�:�VX/w���x�B�ב��r�w(>�G`��`fJ
af
  ��D$~���8i�}=�?+�>X��sPPaN�)=3L [}Z1:<')�
```

Next repeated the same process by finding the type of the file and decompressed using gunzip, bunzip and tar until I find the password.

```bash
file binary 
binary: bzip2 compressed data, block size = 900k

bunzip2 binary
bunzip2: Can't guess original name for binary -- using binary.out

file binary.out 
binary.out: gzip compressed data, was "data4.bin", last modified: Mon Jul 28 19:03:31 2025, max compression, from Unix, original size modulo 2^32 20480

mv binary.out binary.gz

file binary 
binary: POSIX tar archive (GNU)

tar -xf binary

ls
binary  data5.bin  data.txt

rm binary

file data5.bin 
data5.bin: POSIX tar archive (GNU)

tar -xf data5.bin

ls
data5.bin  data6.bin  data.txt

rm data5.bin

file data6.bin 
data6.bin: bzip2 compressed data, block size = 900

ls
data6.bin.out  data.txt

file data6.bin.out 
data6.bin.out: POSIX tar archive (GNU)

tar -xf data6.bin.out

ls
data6.bin.out  data8.bin  data.txt

file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Mon Jul 28 19:03:31 2025, max compression, from Unix, original size modulo 2^32 49

mv data8.bin data8.gz

file data8 
data8: ASCII text

cat data8
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```

Finally the password is **FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn**

### Key Takeaways

1. Remote Access & Safe Workspace


SSH skills – I practiced logging into a remote server securely using SSH with a custom port:
```bash
ssh -p 2220 bandit12@bandit.labs.overthewire.org
```

Safe working directory – Creating a temp directory under /tmp avoids permission issues and keeps the main challenge files intact.

2. File Identification & Format Recognition

Using file command – This is crucial to identify file formats regardless of file extensions.

I encountered multiple formats:

- Hexdump (xxd)

- Gzip compressed data

- Bzip2 compressed data

- Tar archives

- Plain ASCII text

Lesson: Don’t trust file extensions; always verify with file.

3. Data Conversion & Transformation

Hexdump → Binary – Learned how to reverse a hexdump into its binary form:
```
xxd -r file.hex > file.bin
```

ROT13 encryption awareness – Though this challenge was more about compression layers, you recognized the idea of shifting letters in ROT13, which is a simple cipher.

4. Multi-Layer Compression Extraction

Learned to:

- Gzip decompress: gunzip file.gz or gzip -d

- Bzip2 decompress: bunzip2 file.bz2

- Tar extract: tar -xf file.tar

I realized that sometimes challenges nest multiple compression types in sequence, requiring repeated format checking and extraction.

5. Systematic & Iterative Problem Solving

I didn’t just guess; I:

- Checked file type.

- Chose the right decompression tool.

- Repeated until reaching the actual text file.

This methodical approach prevented corruption and data loss.

6. Cleanup & File Handling

- Used mv to rename files for correct tools to work.

- Removed intermediate files with rm to keep your workspace clean.

- Good habit: keeps your working environment manageable.

7. Core Takeaway

This level teaches a CTF (Capture the Flag) essential skill —
"When faced with an unknown file, identify its format, transform it as needed, and extract its contents step by step, without making assumptions."
I practiced a forensic-style investigation that’s directly applicable to penetration testing, malware analysis, and general Linux troubleshooting.



