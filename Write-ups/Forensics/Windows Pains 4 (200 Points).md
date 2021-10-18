# Windows Pains 4
![Category](http://img.shields.io/badge/Category-Forensics-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-200-brightgreen?style=for-the-badge)

## Details

> We want to see if any other machines are infected with this malware. Using the [memory dump file](https://tinyurl.com/wcekj3rt) from Window Pains, submit the SHA1 checksum of the malicious process.
>
> Submit the flag as `flag{SHA1 hash}`.
>
> **CAUTION:** Practice good cyber hygiene! Use an isolated VM to download/run the malicious process. While the malicious process is relatively benign, if you're using an insecurely-configured Windows host, it may be possible for someone to compromise your machine if they can reach you on the same network.
---


Using Volatility3 we can sump the files from the malicious process identified in the "Window Pains 3" challenge using the follwing command; 

```
sudo python3 vol.py -f physmemraw windows.dumpfiles --pid 8180
```

Which results in;

```
Volatility 3 Framework 2.0.0
Progress:  100.00               PDB scanning finished                        
Cache   FileObject      FileName        Result

ImageSectionObject      0x9a077f6d01a0  sechost.dll     file.0x9a077f6d01a0.0x9a077f0ddb20.ImageSectionObject.sechost.dll.img
ImageSectionObject      0x9a07857d4280  userinit.exe    file.0x9a07857d4280.0x9a07843b6a90.ImageSectionObject.userinit.exe.img
ImageSectionObject      0x9a0784c4e590  cryptsp.dll     file.0x9a0784c4e590.0x9a0784bbca20.ImageSectionObject.cryptsp.dll.img
ImageSectionObject      0x9a0784c6fa60  icuin.dll       file.0x9a0784c6fa60.0x9a07849e6600.ImageSectionObject.icuin.dll.img
ImageSectionObject      0x9a0784c6f740  icuuc.dll       file.0x9a0784c6f740.0x9a07849e4660.ImageSectionObject.icuuc.dll.img
DataSectionObject       0x9a078482feb0  ~FontCache-S-1-5-21-1114333211-2247716564-2192578087-1001.dat   Error dumping file
DataSectionObject       0x9a0780c1ec80  ~FontCache-FontFace.dat Error dumping file
ImageSectionObject      0x9a0786d55de0  mpr.dll file.0x9a0786d55de0.0x9a0786747740.ImageSectionObject.mpr.dll.img
ImageSectionObject      0x9a07850764a0  rsaenh.dll      file.0x9a07850764a0.0x9a0785489d80.ImageSectionObject.rsaenh.dll.img
ImageSectionObject      0x9a0786d50340  wsock32.dll     file.0x9a0786d50340.0x9a0785c64290.ImageSectionObject.wsock32.dll.img
ImageSectionObject      0x9a0785960830  wininet.dll     file.0x9a0785960830.0x9a078561e060.ImageSectionObject.wininet.dll.img
ImageSectionObject      0x9a0784c4bcf0  wkscli.dll      file.0x9a0784c4bcf0.0x9a0784bc0a20.ImageSectionObject.wkscli.dll.img
ImageSectionObject      0x9a078595f890  dhcpcsvc6.dll   file.0x9a078595f890.0x9a07851da4e0.ImageSectionObject.dhcpcsvc6.dll.img
ImageSectionObject      0x9a07859614b0  dnsapi.dll      file.0x9a07859614b0.0x9a0785613b60.ImageSectionObject.dnsapi.dll.img
ImageSectionObject      0x9a0784c4d780  msasn1.dll      file.0x9a0784c4d780.0x9a0784bb2dc0.ImageSectionObject.msasn1.dll.img
ImageSectionObject      0x9a0784c4ce20  sspicli.dll     file.0x9a0784c4ce20.0x9a0784b92c80.ImageSectionObject.sspicli.dll.img
ImageSectionObject      0x9a0785955ac0  userenv.dll     file.0x9a0785955ac0.0x9a0785465460.ImageSectionObject.userenv.dll.img
ImageSectionObject      0x9a078481ed40  netapi32.dll    file.0x9a078481ed40.0x9a0784ae8a20.ImageSectionObject.netapi32.dll.img
ImageSectionObject      0x9a078595d180  dhcpcsvc.dll    file.0x9a078595d180.0x9a07854a44e0.ImageSectionObject.dhcpcsvc.dll.img
ImageSectionObject      0x9a0786d5ba10  cscapi.dll      file.0x9a0786d5ba10.0x9a078404da20.ImageSectionObject.cscapi.dll.img
ImageSectionObject      0x9a078594ddc0  mswsock.dll     file.0x9a078594ddc0.0x9a07854cc4e0.ImageSectionObject.mswsock.dll.img
ImageSectionObject      0x9a0784f39ce0  cryptbase.dll   file.0x9a0784f39ce0.0x9a07848cfa20.ImageSectionObject.cryptbase.dll.img
ImageSectionObject      0x9a0784c4d5f0  profapi.dll     file.0x9a0784c4d5f0.0x9a0784b94a20.ImageSectionObject.profapi.dll.img
ImageSectionObject      0x9a078594cc90  winhttp.dll     file.0x9a078594cc90.0x9a078565e010.ImageSectionObject.winhttp.dll.img
ImageSectionObject      0x9a0784f68630  IPHLPAPI.DLL    file.0x9a0784f68630.0x9a0784b38b20.ImageSectionObject.IPHLPAPI.DLL.img
ImageSectionObject      0x9a077f6d0330  crypt32.dll     file.0x9a077f6d0330.0x9a077f0ddd80.ImageSectionObject.crypt32.dll.img
ImageSectionObject      0x9a078594a8a0  winmm.dll       file.0x9a078594a8a0.0x9a0784e6fc80.ImageSectionObject.winmm.dll.img
ImageSectionObject      0x9a077e87e7d0  ntdll.dll       file.0x9a077e87e7d0.0x9a077e8d5560.ImageSectionObject.ntdll.dll.img
ImageSectionObject      0x9a077f2f3510  KernelBase.dll  file.0x9a077f2f3510.0x9a077eb334a0.ImageSectionObject.KernelBase.dll.img
ImageSectionObject      0x9a077f6c9570  ws2_32.dll      file.0x9a077f6c9570.0x9a077ea0d010.ImageSectionObject.ws2_32.dll.img
ImageSectionObject      0x9a077f6d0e20  ucrtbase.dll    file.0x9a077f6d0e20.0x9a077f0cab80.ImageSectionObject.ucrtbase.dll.img
ImageSectionObject      0x9a077f6cf200  psapi.dll       file.0x9a077f6cf200.0x9a077f0cadb0.ImageSectionObject.psapi.dll.img
ImageSectionObject      0x9a077f6d1140  oleaut32.dll    file.0x9a077f6d1140.0x9a077f0dd8c0.ImageSectionObject.oleaut32.dll.img
ImageSectionObject      0x9a077f6cfcf0  advapi32.dll    file.0x9a077f6cfcf0.0x9a077f0dd660.ImageSectionObject.advapi32.dll.img
ImageSectionObject      0x9a077f6cace0  ole32.dll       file.0x9a077f6cace0.0x9a077f0ca6f0.ImageSectionObject.ole32.dll.img
ImageSectionObject      0x9a077f6d07e0  nsi.dll file.0x9a077f6d07e0.0x9a077f0ca950.ImageSectionObject.nsi.dll.img
ImageSectionObject      0x9a077f6c9bb0  imm32.dll       file.0x9a077f6c9bb0.0x9a077ea0d2b0.ImageSectionObject.imm32.dll.img
ImageSectionObject      0x9a077f2f2a20  rpcrt4.dll      file.0x9a077f2f2a20.0x9a077e8dc7c0.ImageSectionObject.rpcrt4.dll.img
ImageSectionObject      0x9a077f6c9d40  user32.dll      file.0x9a077f6c9d40.0x9a077e8dca20.ImageSectionObject.user32.dll.img
ImageSectionObject      0x9a077f111e70  bcrypt.dll      file.0x9a077f111e70.0x9a077eaf9010.ImageSectionObject.bcrypt.dll.img
ImageSectionObject      0x9a077f2f3830  gdi32.dll       file.0x9a077f2f3830.0x9a077eaf94d0.ImageSectionObject.gdi32.dll.img
ImageSectionObject      0x9a077f2f31f0  shlwapi.dll     file.0x9a077f2f31f0.0x9a077eafa4d0.ImageSectionObject.shlwapi.dll.img
ImageSectionObject      0x9a077f110d40  gdi32full.dll   file.0x9a077f110d40.0x9a077eb39580.ImageSectionObject.gdi32full.dll.img
ImageSectionObject      0x9a077f1116a0  msvcp_win.dll   file.0x9a077f1116a0.0x9a077eb34010.ImageSectionObject.msvcp_win.dll.img
ImageSectionObject      0x9a077f111ce0  msvcrt.dll      file.0x9a077f111ce0.0x9a077eb344c0.ImageSectionObject.msvcrt.dll.img
ImageSectionObject      0x9a077f2f20c0  bcryptprimitives.dll    file.0x9a077f2f20c0.0x9a077eb33270.ImageSectionObject.bcryptprimitives.dll.img
ImageSectionObject      0x9a077f111510  combase.dll     file.0x9a077f111510.0x9a077eb35550.ImageSectionObject.combase.dll.img
ImageSectionObject      0x9a077f2e39c0  kernel32.dll    file.0x9a077f2e39c0.0x9a077f0cdd60.ImageSectionObject.kernel32.dll.img
ImageSectionObject      0x9a077f110a20  win32u.dll      file.0x9a077f110a20.0x9a077ea5d520.ImageSectionObject.win32u.dll.img
ImageSectionObject      0x9a077f6b7ed0  wow64cpu.dll    file.0x9a077f6b7ed0.0x9a077eb38010.ImageSectionObject.wow64cpu.dll.img
ImageSectionObject      0x9a077f6a0510  wow64.dll       file.0x9a077f6a0510.0x9a077eb322f0.ImageSectionObject.wow64.dll.img
ImageSectionObject      0x9a077e87ed90  ntdll.dll       file.0x9a077e87ed90.0x9a077e896ba0.ImageSectionObject.ntdll.dll.img
ImageSectionObject      0x9a077eaa3250  wow64win.dll    file.0x9a077eaa3250.0x9a077e8432b0.ImageSectionObject.wow64win.dll.img

```

Next we run `sha1sum file.0x9a07857d4280.0x9a07843b6a90.ImageSectionObject.userinit.exe.img` and get;

```
962d96f30c8f126cbcdee6eecc5e50c3a408402b  file.0x9a07857d4280.0x9a07843b6a90.ImageSectionObject.userinit.exe.img
```

So the flag is;

## flag{962d96f30c8f126cbcdee6eecc5e50c3a408402b}
