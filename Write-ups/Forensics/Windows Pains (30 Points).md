# Windows Pains
![Category](http://img.shields.io/badge/Category-Forensics-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-30-brightgreen?style=for-the-badge)

## Details

One of De Monne's employees had their personal Windows computer hacked by a member of DEADFACE. The attacker managed to exploit a portion of a database backup that contains sensitive employee and customer PII.

>Inspect the memory dump and tell us the Windows Major Operating System Version, bit version, and the image date/time (UTC, no spaces or special characters). Submit the flag as `flag{OS_BIT_YYYYMMDDhhmmss}`.
>
> Example: `flag{WindowsXP_32_202110150900}`
>
> [Download File](https://tinyurl.com/wcekj3rt) (1.5GB; ~5GB after decompression)
> 
> SHA1: 293c3a2a58ed7b15a8454f6dcd8bec0773ba550e
> 
> Password: `d34df4c3`
---


Using Volatility3  we run `sudo python3 vol.py -f physmemraw windows.info`

```
Volatility 3 Framework 2.0.0
Progress:  100.00               PDB scanning finished                        
Variable        Value

Kernel Base     0xf8005da00000
DTB     0x1aa000
Symbols file:///opt/volatility3/volatility3/symbols/windows/ntkrnlmp.pdb/47114209A62F3B9930F6B8998DFD4A99-1.json.xz
Is64Bit True
IsPAE   False
layer_name      0 WindowsIntel32e
memory_layer    1 FileLayer
KdVersionBlock  0xf8005e60f378
Major/Minor     15.19041
MachineType     34404
KeNumberProcessors      4
SystemTime      2021-09-07 14:57:44
NtSystemRoot    C:\WINDOWS
NtProductType   NtProductWinNt
NtMajorVersion  10
NtMinorVersion  0
PE MajorOperatingSystemVersion  10
PE MinorOperatingSystemVersion  0
PE Machine      34404
PE TimeDateStamp        Sat Apr  7 12:04:17 2068

```

Using this information we can assemble eth flag as;


## flag{Windows10_64_20210907145744}
