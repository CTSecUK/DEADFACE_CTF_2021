# Windows Pains 3
![Category](http://img.shields.io/badge/Category-Forensics-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-100-brightgreen?style=for-the-badge)

## Details

One of De Monne's employees had their personal Windows computer hacked by a member of DEADFACE. The attacker managed to exploit a portion of a database backup that contains sensitive employee and customer PII.

> Using the [memory dump file](https://tinyurl.com/wcekj3rt) from Window Pains, find out the name of the malicious process.
>
> Submit the flag as `flag{process-name_pid}` (include the extension)..
>
> Example: `flag{svchost.exe_1234}`
---


Using Volatility3 we run `sudo python3 vol.py -f physmemraw windows.pstree`

```
❯ sudo python3 /opt/volatility3/vol.py -f physmemraw windows.pstree
Volatility 3 Framework 2.0.0
Progress:  100.00               PDB scanning finished                        
PID     PPID    ImageFileName   Offset(V)       Threads Handles SessionId       Wow64   CreateTime      ExitTime

4       0       System  0x9a077de79040  116     -       N/A     False   2021-09-07 14:24:34.000000      N/A
* 372   4       smss.exe        0x9a077eacc040  2       -       N/A     False   2021-09-07 14:24:34.000000      N/A
* 108   4       Registry        0x9a077dfc8040  4       -       N/A     False   2021-09-07 14:24:29.000000      N/A
* 1868  4       MemCompression  0x9a0780c24080  42      -       N/A     False   2021-09-07 14:24:56.000000      N/A
468     456     csrss.exe       0x9a077f2db140  11      -       0       False   2021-09-07 14:24:53.000000      N/A
544     536     csrss.exe       0x9a077fe9e140  12      -       1       False   2021-09-07 14:24:53.000000      N/A
568     456     wininit.exe     0x9a077fead080  1       -       0       False   2021-09-07 14:24:53.000000      N/A
* 864   568     fontdrvhost.ex  0x9a077ff54140  5       -       0       False   2021-09-07 14:24:55.000000      N/A
* 708   568     lsass.exe       0x9a077ff1d080  13      -       0       False   2021-09-07 14:24:55.000000      N/A
* 668   568     services.exe    0x9a077fedd080  9       -       0       False   2021-09-07 14:24:55.000000      N/A
** 1540 668     svchost.exe     0x9a0780af7300  7       -       0       False   2021-09-07 14:24:56.000000      N/A
** 2564 668     spoolsv.exe     0x9a0780e8b0c0  7       -       0       False   2021-09-07 14:24:57.000000      N/A
** 2056 668     svchost.exe     0x9a0780cd92c0  7       -       0       False   2021-09-07 14:24:57.000000      N/A
** 3084 668     svchost.exe     0x9a078408b240  5       -       0       False   2021-09-07 14:24:57.000000      N/A
** 1044 668     svchost.exe     0x9a078090e300  32      -       0       False   2021-09-07 14:24:56.000000      N/A
** 1556 668     svchost.exe     0x9a0780c88080  5       -       0       False   2021-09-07 14:24:57.000000      N/A
** 1564 668     svchost.exe     0x9a0780b35280  3       -       0       False   2021-09-07 14:24:56.000000      N/A
** 5152 668     svchost.exe     0x9a0784b10300  8       -       1       False   2021-09-07 14:25:13.000000      N/A
** 2552 668     svchost.exe     0x9a0780e93300  11      -       0       False   2021-09-07 14:24:57.000000      N/A
** 3112 668     svchost.exe     0x9a078408d2c0  4       -       0       False   2021-09-07 14:24:57.000000      N/A
** 2096 668     svchost.exe     0x9a0780ce1300  5       -       0       False   2021-09-07 14:24:57.000000      N/A
** 2612 668     svchost.exe     0x9a0780e8f0c0  13      -       0       False   2021-09-07 14:24:57.000000      N/A
** 2104 668     svchost.exe     0x9a078405f080  7       -       0       False   2021-09-07 14:24:57.000000      N/A
** 1092 668     svchost.exe     0x9a0780c872c0  6       -       0       False   2021-09-07 14:24:57.000000      N/A
** 1612 668     svchost.exe     0x9a0780b85300  2       -       0       False   2021-09-07 14:24:56.000000      N/A
** 1620 668     MsMpEng.exe     0x9a0784061340  12      -       0       False   2021-09-07 14:24:57.000000      N/A
** 4180 668     svchost.exe     0x9a0784750080  7       -       0       False   2021-09-07 14:25:07.000000      N/A
** 10840        668     svchost.exe     0x9a0784698080  12      -       0       False   2021-09-07 14:50:38.000000      N/A
** 1116 668     svchost.exe     0x9a0780942280  3       -       0       False   2021-09-07 14:24:56.000000      N/A
** 2148 668     svchost.exe     0x9a0780dc12c0  8       -       0       False   2021-09-07 14:24:57.000000      N/A
** 1656 668     svchost.exe     0x9a0780b472c0  5       -       0       False   2021-09-07 14:24:56.000000      N/A
** 1664 668     svchost.exe     0x9a0780b49280  7       -       0       False   2021-09-07 14:24:56.000000      N/A
** 4224 668     svchost.exe     0x9a0784792240  9       -       0       False   2021-09-07 14:25:07.000000      N/A
** 1168 668     svchost.exe     0x9a0780952240  9       -       0       False   2021-09-07 14:24:56.000000      N/A
*** 4732        1168    taskhostw.exe   0x9a07848e72c0  0       -       1       False   2021-09-07 14:25:12.000000      2021-09-07 14:25:12.000000 
*** 4564        1168    taskhostw.exe   0x9a078487a340  11      -       1       False   2021-09-07 14:25:12.000000      N/A
** 8336 668     svchost.exe     0x9a0785547080  4       -       0       False   2021-09-07 14:26:59.000000      N/A
** 9872 668     svchost.exe     0x9a078651c300  0       -       0       False   2021-09-07 14:29:57.000000      2021-09-07 14:30:05.000000 
** 2200 668     svchost.exe     0x9a0780dea300  18      -       0       False   2021-09-07 14:24:57.000000      N/A
** 1692 668     svchost.exe     0x9a0780bb1240  3       -       0       False   2021-09-07 14:24:56.000000      N/A
** 2208 668     svchost.exe     0x9a0780de80c0  4       -       0       False   2021-09-07 14:24:57.000000      N/A
** 2216 668     svchost.exe     0x9a0780dec2c0  6       -       0       False   2021-09-07 14:24:57.000000      N/A
** 5300 668     SearchIndexer.  0x9a07848ea080  32      -       0       False   2021-09-07 14:25:14.000000      N/A
*** 5864        5300    SearchFilterHo  0x9a0784d4d080  4       -       0       False   2021-09-07 14:56:16.000000      N/A
*** 10500       5300    SearchProtocol  0x9a0784e560c0  6       -       0       False   2021-09-07 14:53:47.000000      N/A
** 1220 668     svchost.exe     0x9a0780965240  4       -       0       False   2021-09-07 14:24:56.000000      N/A
** 6340 668     svchost.exe     0x9a07851d42c0  3       -       0       False   2021-09-07 14:25:22.000000      N/A
** 9428 668     svchost.exe     0x9a078514b080  7       -       0       False   2021-09-07 14:32:03.000000      N/A
** 8412 668     SgrmBroker.exe  0x9a0785760080  7       -       0       False   2021-09-07 14:26:59.000000      N/A
** 1256 668     svchost.exe     0x9a07809c22c0  3       -       0       False   2021-09-07 14:24:56.000000      N/A
** 8696 668     svchost.exe     0x9a0785409080  6       -       1       False   2021-09-07 14:27:01.000000      N/A
** 1264 668     svchost.exe     0x9a07809c8300  4       -       0       False   2021-09-07 14:24:56.000000      N/A
** 2808 668     svchost.exe     0x9a0780eea2c0  3       -       0       False   2021-09-07 14:24:57.000000      N/A
** 1272 668     svchost.exe     0x9a07809ca300  8       -       0       False   2021-09-07 14:24:56.000000      N/A
** 5392 668     svchost.exe     0x9a07855e50c0  5       -       0       False   2021-09-07 14:25:39.000000      N/A
** 2328 668     svchost.exe     0x9a077de68080  3       -       0       False   2021-09-07 14:24:57.000000      N/A
** 10008        668     svchost.exe     0x9a0785ce2080  4       -       0       False   2021-09-07 14:55:12.000000      N/A
** 4916 668     svchost.exe     0x9a0784932280  4       -       0       False   2021-09-07 14:25:12.000000      N/A
*** 4944        4916    ctfmon.exe      0x9a07848e6280  12      -       1       False   2021-09-07 14:25:12.000000      N/A
** 5948 668     svchost.exe     0x9a078553c080  3       -       0       False   2021-09-07 14:55:13.000000      N/A
** 832  668     svchost.exe     0x9a077ff82240  28      -       0       False   2021-09-07 14:24:55.000000      N/A
*** 5780        832     SearchApp.exe   0x9a0784db8080  72      -       1       False   2021-09-07 14:25:18.000000      N/A
*** 4248        832     smartscreen.ex  0x9a07867790c0  16      -       1       False   2021-09-07 14:56:38.000000      N/A
*** 9500        832     RuntimeBroker.  0x9a0785c19080  0       -       1       False   2021-09-07 14:27:19.000000      2021-09-07 14:57:54.000000 
*** 5664        832     RuntimeBroker.  0x9a0784dd8300  2       -       1       False   2021-09-07 14:25:18.000000      N/A
*** 1700        832     RuntimeBroker.  0x9a0785429340  4       -       1       False   2021-09-07 14:27:57.000000      N/A
*** 7480        832     TextInputHost.  0x9a078575b300  11      -       1       False   2021-09-07 14:26:17.000000      N/A
*** 6844        832     RuntimeBroker.  0x9a078528e080  2       -       1       False   2021-09-07 14:25:30.000000      N/A
*** 5564        832     StartMenuExper  0x9a0784bf9080  9       -       1       False   2021-09-07 14:25:16.000000      N/A
*** 4156        832     RuntimeBroker.  0x9a077eb17300  6       -       1       False   2021-09-07 14:57:01.000000      N/A
*** 6212        832     RuntimeBroker.  0x9a0785162300  4       -       1       False   2021-09-07 14:25:22.000000      N/A
*** 9544        832     ShellExperienc  0x9a07866e1080  15      -       1       False   2021-09-07 14:28:49.000000      N/A
*** 5200        832     YourPhone.exe   0x9a0784edc080  14      -       1       False   2021-09-07 14:25:20.000000      N/A
*** 8020        832     UserOOBEBroker  0x9a0785b4b080  4       -       1       False   2021-09-07 14:28:18.000000      N/A
*** 6752        832     RuntimeBroker.  0x9a078528d300  16      -       1       False   2021-09-07 14:25:26.000000      N/A
**** 10284      6752    powershell.exe  0x9a0786752300  14      -       1       False   2021-09-07 14:35:13.000000      N/A
***** 5860      10284   winpmem_mini_x  0x9a077f3e70c0  1       -       1       False   2021-09-07 14:57:44.000000      N/A
***** 10268     10284   conhost.exe     0x9a0786744340  6       -       1       False   2021-09-07 14:35:13.000000      N/A
*** 10208       832     WinStore.App.e  0x9a077f7550c0  19      -       1       False   2021-09-07 14:27:53.000000      N/A
*** 992 832     WWAHost.exe     0x9a0785443300  50      -       1       False   2021-09-07 14:57:05.000000      N/A
*** 3944        832     dllhost.exe     0x9a07855d7300  13      -       1       False   2021-09-07 14:26:17.000000      N/A
*** 8044        832     ApplicationFra  0x9a07854c1340  19      -       1       False   2021-09-07 14:26:52.000000      N/A
*** 9452        832     RuntimeBroker.  0x9a078677b300  4       -       1       False   2021-09-07 14:28:50.000000      N/A
*** 6000        832     RuntimeBroker.  0x9a0784bce080  16      -       1       False   2021-09-07 14:25:19.000000      N/A
*** 2928        832     SystemSettings  0x9a077f74d080  17      -       1       False   2021-09-07 14:28:16.000000      N/A
*** 5368        832     LockApp.exe     0x9a0784dd9080  13      -       1       False   2021-09-07 14:25:21.000000      N/A
*** 10748       832     Calculator.exe  0x9a0785cec340  22      -       1       False   2021-09-07 14:57:01.000000      N/A
** 2372 668     svchost.exe     0x9a0780e09080  7       -       0       False   2021-09-07 14:24:57.000000      N/A
** 2904 668     svchost.exe     0x9a0780ff4240  5       -       0       False   2021-09-07 14:24:57.000000      N/A
** 4444 668     svchost.exe     0x9a07847ed300  11      -       1       False   2021-09-07 14:25:11.000000      N/A
** 2912 668     svchost.exe     0x9a0780ff6300  4       -       0       False   2021-09-07 14:24:57.000000      N/A
** 2920 668     svchost.exe     0x9a0780ff3080  6       -       0       False   2021-09-07 14:24:57.000000      N/A
** 1392 668     svchost.exe     0x9a0780a2e240  8       -       0       False   2021-09-07 14:24:56.000000      N/A
*** 4412        1392    sihost.exe      0x9a07844ab080  14      -       1       False   2021-09-07 14:25:11.000000      N/A
** 7024 668     SecurityHealth  0x9a0784bb3080  15      -       0       False   2021-09-07 14:25:32.000000      N/A
** 3444 668     svchost.exe     0x9a0784236240  3       -       0       False   2021-09-07 14:24:57.000000      N/A
** 2936 668     svchost.exe     0x9a0780ff7080  10      -       0       False   2021-09-07 14:24:57.000000      N/A
** 4472 668     svchost.exe     0x9a07847ee080  8       -       1       False   2021-09-07 14:25:11.000000      N/A
** 1404 668     svchost.exe     0x9a0780a302c0  5       -       0       False   2021-09-07 14:24:56.000000      N/A
** 2944 668     svchost.exe     0x9a0780ff8080  16      -       0       False   2021-09-07 14:24:57.000000      N/A
** 1412 668     svchost.exe     0x9a0780a32300  5       -       0       False   2021-09-07 14:24:56.000000      N/A
** 1924 668     svchost.exe     0x9a0780c2d300  8       -       0       False   2021-09-07 14:24:57.000000      N/A
** 904  668     svchost.exe     0x9a07852240c0  10      -       0       False   2021-09-07 14:25:37.000000      N/A
** 8584 668     svchost.exe     0x9a0784d8f080  9       -       0       False   2021-09-07 14:27:00.000000      N/A
** 1936 668     svchost.exe     0x9a0780c7b240  2       -       0       False   2021-09-07 14:24:57.000000      N/A
** 2964 668     svchost.exe     0x9a0784036240  11      -       0       False   2021-09-07 14:24:57.000000      N/A
** 10648        668     svchost.exe     0x9a07864c0080  4       -       0       False   2021-09-07 14:32:36.000000      N/A
** 5020 668     svchost.exe     0x9a078497a2c0  8       -       0       False   2021-09-07 14:25:12.000000      N/A
** 3996 668     svchost.exe     0x9a0784a4d080  6       -       0       False   2021-09-07 14:25:12.000000      N/A
** 7584 668     svchost.exe     0x9a07853e12c0  12      -       0       False   2021-09-07 14:26:57.000000      N/A
** 4016 668     svchost.exe     0x9a0784471080  8       -       0       False   2021-09-07 14:25:01.000000      N/A
** 952  668     svchost.exe     0x9a078083a2c0  16      -       0       False   2021-09-07 14:24:56.000000      N/A
** 8656 668     svchost.exe     0x9a0785249080  11      -       0       False   2021-09-07 14:27:00.000000      N/A
** 3544 668     svchost.exe     0x9a07846cb240  0       -       0       False   2021-09-07 14:25:06.000000      2021-09-07 14:35:42.000000 
** 7132 668     svchost.exe     0x9a07855f0240  4       -       0       False   2021-09-07 14:25:33.000000      N/A
** 9692 668     svchost.exe     0x9a07854ac080  5       -       0       False   2021-09-07 14:28:03.000000      N/A
** 4064 668     svchost.exe     0x9a078458e080  5       -       0       False   2021-09-07 14:54:56.000000      N/A
** 996  668     svchost.exe     0x9a078085c240  7       -       0       False   2021-09-07 14:24:56.000000      N/A
** 3048 668     svchost.exe     0x9a0780ff2280  3       -       0       False   2021-09-07 14:24:57.000000      N/A
** 3060 668     svchost.exe     0x9a078405e240  6       -       0       False   2021-09-07 14:24:57.000000      N/A
** 2040 668     svchost.exe     0x9a0780c85280  3       -       0       False   2021-09-07 14:24:57.000000      N/A
644     536     winlogon.exe    0x9a077fe9c140  3       -       1       False   2021-09-07 14:24:54.000000      N/A
* 856   644     fontdrvhost.ex  0x9a077ff89140  5       -       1       False   2021-09-07 14:24:55.000000      N/A
* 428   644     dwm.exe 0x9a078087f080  21      -       1       False   2021-09-07 14:24:56.000000      N/A
* 384   644     LogonUI.exe     0x9a078087e080  0       -       1       False   2021-09-07 14:24:56.000000      2021-09-07 14:25:29.000000 
* 4140  644     userinit.exe    0x9a07849b5080  0       -       1       False   2021-09-07 14:25:12.000000      2021-09-07 14:25:36.000000 
** 4012 4140    explorer.exe    0x9a07849b7340  71      -       1       False   2021-09-07 14:25:12.000000      N/A
*** 10432       4012    notepad.exe     0x9a0785775300  6       -       1       False   2021-09-07 14:56:56.000000      N/A
*** 1796        4012    powershell.exe  0x9a0785404300  15      -       1       False   2021-09-07 14:29:07.000000      N/A
**** 8592       1796    conhost.exe     0x9a0785c11300  5       -       1       False   2021-09-07 14:29:08.000000      N/A
*** 1832        4012    powershell_ise  0x9a07862e60c0  23      -       1       False   2021-09-07 14:30:48.000000      N/A
**** 10992      1832    conhost.exe     0x9a0784f26080  5       -       1       False   2021-09-07 14:33:01.000000      N/A
*** 6988        4012    SecurityHealth  0x9a0784d15080  6       -       1       False   2021-09-07 14:25:32.000000      N/A
*** 7120        4012    msedge.exe      0x9a0785297080  0       -       1       False   2021-09-07 14:25:33.000000      2021-09-07 14:56:33.000000 
**** 3652       7120    msedge.exe      0x9a0784da7080  36      -       1       False   2021-09-07 14:56:33.000000      N/A
***** 7008      3652    msedge.exe      0x9a07851dc080  18      -       1       False   2021-09-07 14:56:34.000000      N/A
***** 32        3652    msedge.exe      0x9a07854e7080  17      -       1       False   2021-09-07 14:56:41.000000      N/A
***** 3556      3652    msedge.exe      0x9a0785548340  0       -       1       False   2021-09-07 14:56:39.000000      2021-09-07 14:56:46.000000 
***** 420       3652    msedge.exe      0x9a07864f6300  13      -       1       False   2021-09-07 14:56:52.000000      N/A
***** 9896      3652    msedge.exe      0x9a0785b1e340  0       -       1       False   2021-09-07 14:56:39.000000      2021-09-07 14:57:44.000000 
***** 5832      3652    msedge.exe      0x9a078428b080  7       -       1       False   2021-09-07 14:57:39.000000      N/A
***** 10808     3652    msedge.exe      0x9a0785ad6340  16      -       1       False   2021-09-07 14:56:49.000000      N/A
***** 6540      3652    msedge.exe      0x9a0786787340  10      -       1       False   2021-09-07 14:56:51.000000      N/A
***** 1996      3652    msedge.exe      0x9a078582b080  15      -       1       False   2021-09-07 14:57:03.000000      N/A
***** 2744      3652    msedge.exe      0x9a0785228080  0       -       1       False   2021-09-07 14:57:30.000000      2021-09-07 14:57:40.000000 
***** 6032      3652    msedge.exe      0x9a0785218080  8       -       1       False   2021-09-07 14:56:33.000000      N/A
***** 5240      3652    msedge.exe      0x9a0785bd0080  15      -       1       False   2021-09-07 14:57:35.000000      N/A
***** 2488      3652    msedge.exe      0x9a0785cb4340  13      -       1       False   2021-09-07 14:56:46.000000      N/A
***** 4924      3652    msedge.exe      0x9a0784a66080  7       -       1       False   2021-09-07 14:56:34.000000      N/A
***** 1628      3652    msedge.exe      0x9a07854da340  17      -       1       False   2021-09-07 14:56:34.000000      N/A
*** 7096        4012    OneDrive.exe    0x9a0785236080  25      -       1       False   2021-09-07 14:25:32.000000      N/A
7308    5292    Spotify.exe     0x9a07851dd080  35      -       1       True    2021-09-07 14:25:42.000000      N/A
* 7620  7308    Spotify.exe     0x9a07855d0300  6       -       1       True    2021-09-07 14:25:49.000000      N/A
* 7908  7308    Spotify.exe     0x9a07856ef2c0  8       -       1       True    2021-09-07 14:25:55.000000      N/A
* 7720  7308    Spotify.exe     0x9a0785784080  7       -       1       True    2021-09-07 14:25:50.000000      N/A
* 8136  7308    Spotify.exe     0x9a0785bce0c0  12      -       1       True    2021-09-07 14:25:58.000000      N/A
* 7896  7308    Spotify.exe     0x9a07847db080  6       -       1       True    2021-09-07 14:25:55.000000      N/A
8180    2252    userinit.exe    0x9a07843ab080  3       -       1       True    2021-09-07 14:55:55.000000      N/A

```

Next we also run ; `sudo python3 vol.py -f physmemraw windows.cmdLine`

```
❯ sudo python3 /opt/volatility3/vol.py -f physmemraw windows.cmdline
Volatility 3 Framework 2.0.0
Progress:  100.00               PDB scanning finished                        
PID     Process Args

4       System  Required memory at 0x20 is not valid (process exited?)
108     Registry        Required memory at 0x20 is not valid (process exited?)
372     smss.exe        \SystemRoot\System32\smss.exe
468     csrss.exe       %SystemRoot%\system32\csrss.exe ObjectDirectory=\Windows SharedSection=1024,20480,768 Windows=On SubSystemType=Windows ServerDll=basesrv,1 ServerDll=winsrv:UserServerDllInitialization,3 ServerDll=sxssrv,4 ProfileControl=Off MaxRequestThreads=16
544     csrss.exe       %SystemRoot%\system32\csrss.exe ObjectDirectory=\Windows SharedSection=1024,20480,768 Windows=On SubSystemType=Windows ServerDll=basesrv,1 ServerDll=winsrv:UserServerDllInitialization,3 ServerDll=sxssrv,4 ProfileControl=Off MaxRequestThreads=16
568     wininit.exe     wininit.exe
644     winlogon.exe    winlogon.exe
668     services.exe    C:\WINDOWS\system32\services.exe
708     lsass.exe       C:\WINDOWS\system32\lsass.exe
832     svchost.exe     C:\WINDOWS\system32\svchost.exe -k DcomLaunch -p
856     fontdrvhost.ex  Required memory at 0x1bcfe071a28 is inaccessible (swapped)
864     fontdrvhost.ex  Required memory at 0x1fbf9d01a28 is inaccessible (swapped)
952     svchost.exe     C:\WINDOWS\system32\svchost.exe -k RPCSS -p
996     svchost.exe     C:\WINDOWS\system32\svchost.exe -k DcomLaunch -p -s LSM
384     LogonUI.exe     Required memory at 0x29d6860020 is not valid (process exited?)
428     dwm.exe "dwm.exe"
1044    svchost.exe     C:\WINDOWS\System32\svchost.exe -k NetworkService -s TermService
1116    svchost.exe     C:\WINDOWS\System32\svchost.exe -k LocalSystemNetworkRestricted -p -s NcbService
1168    svchost.exe     C:\WINDOWS\system32\svchost.exe -k netsvcs -p -s Schedule
1220    svchost.exe     C:\WINDOWS\system32\svchost.exe -k netsvcs -p -s ProfSvc
1256    svchost.exe     C:\WINDOWS\system32\svchost.exe -k LocalServiceNoNetwork -p
1264    svchost.exe     C:\WINDOWS\System32\svchost.exe -k LocalServiceNetworkRestricted -p -s lmhosts
1272    svchost.exe     C:\WINDOWS\System32\svchost.exe -k LocalServiceNetworkRestricted -p -s EventLog
1392    svchost.exe     C:\WINDOWS\system32\svchost.exe -k netsvcs -p -s UserManager
1404    svchost.exe     C:\WINDOWS\system32\svchost.exe -k LocalService -p -s nsi
1412    svchost.exe     C:\WINDOWS\system32\svchost.exe -k LocalServiceNetworkRestricted -p -s TimeBrokerSvc
1540    svchost.exe     C:\WINDOWS\system32\svchost.exe -k LocalServiceNetworkRestricted -p -s Dhcp
1564    svchost.exe     C:\WINDOWS\System32\svchost.exe -k LocalSystemNetworkRestricted -p -s UmRdpService
1612    svchost.exe     C:\WINDOWS\system32\svchost.exe -k LocalService -p -s DispBrokerDesktopSvc
1656    svchost.exe     C:\WINDOWS\system32\svchost.exe -k LocalService -p -s EventSystem
1664    svchost.exe     C:\WINDOWS\system32\svchost.exe -k LocalSystemNetworkRestricted -p -s SysMain
1692    svchost.exe     C:\WINDOWS\System32\svchost.exe -k netsvcs -p -s Themes
1868    MemCompression  Required memory at 0x20 is not valid (process exited?)
1924    svchost.exe     C:\WINDOWS\System32\svchost.exe -k NetworkService -p -s NlaSvc
1936    svchost.exe     C:\WINDOWS\system32\svchost.exe -k netsvcs -p -s SENS
2040    svchost.exe     C:\WINDOWS\System32\svchost.exe -k LocalSystemNetworkRestricted -p -s AudioEndpointBuilder
1092    svchost.exe     C:\WINDOWS\system32\svchost.exe -k LocalService -p -s FontCache
1556    svchost.exe     C:\WINDOWS\system32\svchost.exe -k netsvcs -s CertPropSvc
2056    svchost.exe     C:\WINDOWS\System32\svchost.exe -k LocalServiceNetworkRestricted -p
2096    svchost.exe     C:\WINDOWS\System32\svchost.exe -k NetworkService -p -s LanmanWorkstation
2148    svchost.exe     C:\WINDOWS\System32\svchost.exe -k LocalService -p -s netprofm
2200    svchost.exe     C:\WINDOWS\system32\svchost.exe -k NetworkService -p -s Dnscache
2208    svchost.exe     C:\WINDOWS\System32\svchost.exe -k LocalServiceNetworkRestricted -p
2216    svchost.exe     C:\WINDOWS\system32\svchost.exe -k LocalServiceNetworkRestricted -p
2328    svchost.exe     C:\WINDOWS\System32\svchost.exe -k netsvcs -p -s ShellHWDetection
2372    svchost.exe     C:\WINDOWS\System32\svchost.exe -k netsvcs -p -s SessionEnv
2552    svchost.exe     C:\WINDOWS\system32\svchost.exe -k LocalServiceNetworkRestricted -p -s WinHttpAutoProxySvc
2564    spoolsv.exe     Required memory at 0x12e1ae8 is inaccessible (swapped)
2612    svchost.exe     C:\WINDOWS\system32\svchost.exe -k LocalServiceNoNetworkFirewall -p
2808    svchost.exe     C:\WINDOWS\system32\svchost.exe -k LocalService -p
2904    svchost.exe     C:\WINDOWS\system32\svchost.exe -k netsvcs -p -s IKEEXT
2912    svchost.exe     C:\WINDOWS\system32\svchost.exe -k NetworkServiceNetworkRestricted -p -s PolicyAgent
2920    svchost.exe     C:\WINDOWS\system32\svchost.exe -k NetworkService -p -s CryptSvc
2936    svchost.exe     C:\WINDOWS\System32\svchost.exe -k utcsvc -p
2944    svchost.exe     C:\WINDOWS\System32\svchost.exe -k LocalServiceNoNetwork -p -s DPS
2964    svchost.exe     C:\WINDOWS\system32\svchost.exe -k netsvcs -p -s Winmgmt
3048    svchost.exe     C:\WINDOWS\System32\svchost.exe -k LocalSystemNetworkRestricted -p -s TrkWks
3060    svchost.exe     C:\WINDOWS\system32\svchost.exe -k netsvcs -p -s LanmanServer
2104    svchost.exe     C:\WINDOWS\system32\svchost.exe -k netsvcs -p -s WpnService
1620    MsMpEng.exe     "C:\ProgramData\Microsoft\Windows Defender\platform\4.18.2107.4-0\MsMpEng.exe"
3084    svchost.exe     C:\WINDOWS\System32\svchost.exe -k NetSvcs -p -s iphlpsvc
3112    svchost.exe     C:\WINDOWS\System32\svchost.exe -k LocalService -p -s WdiServiceHost
3444    svchost.exe     C:\WINDOWS\system32\svchost.exe -k netsvcs -p -s lfsvc
4016    svchost.exe     C:\WINDOWS\System32\svchost.exe -k LocalService -p -s LicenseManager
3544    svchost.exe     Required memory at 0xdbe6836020 is not valid (process exited?)
4180    svchost.exe     C:\WINDOWS\system32\svchost.exe -k netsvcs -p -s TokenBroker
4224    svchost.exe     C:\WINDOWS\system32\svchost.exe -k appmodel -p -s StateRepository
4412    sihost.exe      sihost.exe
4444    svchost.exe     C:\WINDOWS\system32\svchost.exe -k UnistackSvcGroup -s CDPUserSvc
4472    svchost.exe     C:\WINDOWS\system32\svchost.exe -k UnistackSvcGroup -s WpnUserService
4564    taskhostw.exe   taskhostw.exe {222A245B-E637-4AE9-A93F-A59CA119A75E}
4732    taskhostw.exe   Required memory at 0xb6a8430020 is not valid (process exited?)
4916    svchost.exe     C:\WINDOWS\System32\svchost.exe -k LocalSystemNetworkRestricted -p -s TabletInputService
4944    ctfmon.exe      "ctfmon.exe"
5020    svchost.exe     C:\WINDOWS\system32\svchost.exe -k LocalService -p -s CDPSvc
4140    userinit.exe    Required memory at 0xfd21197020 is not valid (process exited?)
4012    explorer.exe    C:\WINDOWS\Explorer.EXE
3996    svchost.exe     C:\WINDOWS\System32\svchost.exe -k LocalServiceNetworkRestricted -s RmSvc
5152    svchost.exe     C:\WINDOWS\system32\svchost.exe -k ClipboardSvcGroup -p -s cbdhsvc
5300    SearchIndexer.  C:\WINDOWS\system32\SearchIndexer.exe /Embedding
5564    StartMenuExper  "C:\Windows\SystemApps\Microsoft.Windows.StartMenuExperienceHost_cw5n1h2txyewy\StartMenuExperienceHost.exe" -ServerName:App.AppXywbrabmsek0gm3tkwpr5kwzbs55tkqay.mca
5664    RuntimeBroker.  C:\Windows\System32\RuntimeBroker.exe -Embedding
5780    SearchApp.exe   "C:\Windows\SystemApps\Microsoft.Windows.Search_cw5n1h2txyewy\SearchApp.exe" -ServerName:CortanaUI.AppX8z9r6jm96hw4bsbneegw0kyxx296wr9t.mca
6000    RuntimeBroker.  C:\Windows\System32\RuntimeBroker.exe -Embedding
5200    YourPhone.exe   "C:\Program Files\WindowsApps\Microsoft.YourPhone_1.21072.160.0_x64__8wekyb3d8bbwe\YourPhone.exe" -ServerName:App.AppX9yct9q388jvt4h7y0gn06smzkxcsnt8m.mca
5368    LockApp.exe     "C:\Windows\SystemApps\Microsoft.LockApp_cw5n1h2txyewy\LockApp.exe" -ServerName:WindowsDefaultLockScreen.AppX7y4nbzq37zn4ks9k7amqjywdat7d3j2z.mca
6212    RuntimeBroker.  C:\Windows\System32\RuntimeBroker.exe -Embedding
6340    svchost.exe     C:\WINDOWS\system32\svchost.exe -k LocalService -p -s BthAvctpSvc
6752    RuntimeBroker.  C:\Windows\System32\RuntimeBroker.exe -Embedding
6844    RuntimeBroker.  C:\Windows\System32\RuntimeBroker.exe -Embedding
6988    SecurityHealth  "C:\Windows\System32\SecurityHealthSystray.exe" 
7024    SecurityHealth  C:\WINDOWS\system32\SecurityHealthService.exe
7096    OneDrive.exe    "C:\Users\Jimmie\AppData\Local\Microsoft\OneDrive\OneDrive.exe" /background
7120    msedge.exe      Required memory at 0x5f397ad020 is not valid (process exited?)
7132    svchost.exe     C:\WINDOWS\system32\svchost.exe -k netsvcs -p -s Appinfo
904     svchost.exe     C:\WINDOWS\system32\svchost.exe -k LocalSystemNetworkRestricted -p -s PcaSvc
5392    svchost.exe     C:\WINDOWS\System32\svchost.exe -k LocalSystemNetworkRestricted -p -s WdiSystemHost
7308    Spotify.exe     Spotify.exe --autostart
7620    Spotify.exe     "C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.167.586.0_x86__zpdnekdrzrea0\Spotify.exe" --type=crashpad-handler /prefetch:7 --max-uploads=5 --max-db-size=20 --max-db-age=5 --monitor-self-annotation=ptype=crashpad-handler "--database=C:\Users\Jimmie\AppData\Local\SpotifyAppX\User Data\Crashpad" "--metrics-dir=C:\Users\Jimmie\AppData\Local\SpotifyAppX\User Data" --url=https://crashdump.spotify.com:443/ --annotation=platform=win32 --annotation=product=spotify --annotation=version=1.1.67.586 --initial-client-data=0x5d0,0x5cc,0x5a0,0x5c8,0x5d4,0x6c433a28,0x6c433a38,0x6c433a44
7720    Spotify.exe     "C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.167.586.0_x86__zpdnekdrzrea0\Spotify.exe" --type=gpu-process --field-trial-handle=2108,4839584854497019253,9112382588695800992,131072 --disable-features=CalculateNativeWinOcclusion --disable-d3d11 --log-file="C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.167.586.0_x86__zpdnekdrzrea0\debug.log" --log-severity=disable --user-agent-product="Chrome/91.0.4472.114 Spotify/1.1.67.586" --lang=en --gpu-preferences=SAAAAAAAAADgAAAwAAAAAAAAAAAAAAAAAABgAAAAAAAoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAB4AAAAAAAAAHgAAAAAAAAAKAAAAAQAAAAgAAAAAAAAACgAAAAAAAAAMAAAAAAAAAA4AAAAAAAAABAAAAAAAAAAAAAAAAUAAAAQAAAAAAAAAAAAAAAGAAAAEAAAAAAAAAABAAAABQAAABAAAAAAAAAAAQAAAAYAAAAIAAAAAAAAAAgAAAAAAAAA --log-file="C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.167.586.0_x86__zpdnekdrzrea0\debug.log" --mojo-platform-channel-handle=2112 /prefetch:2
7896    Spotify.exe     "C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.167.586.0_x86__zpdnekdrzrea0\Spotify.exe" --type=utility --utility-sub-type=storage.mojom.StorageService --field-trial-handle=2108,4839584854497019253,9112382588695800992,131072 --disable-features=CalculateNativeWinOcclusion --lang=en-US --service-sandbox-type=utility --log-file="C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.167.586.0_x86__zpdnekdrzrea0\debug.log" --log-severity=disable --user-agent-product="Chrome/91.0.4472.114 Spotify/1.1.67.586" --lang=en --log-file="C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.167.586.0_x86__zpdnekdrzrea0\debug.log" --mojo-platform-channel-handle=3096 /prefetch:8
7908    Spotify.exe     "C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.167.586.0_x86__zpdnekdrzrea0\Spotify.exe" --type=utility --utility-sub-type=network.mojom.NetworkService --field-trial-handle=2108,4839584854497019253,9112382588695800992,131072 --disable-features=CalculateNativeWinOcclusion --lang=en-US --service-sandbox-type=none --log-file="C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.167.586.0_x86__zpdnekdrzrea0\debug.log" --log-severity=disable --user-agent-product="Chrome/91.0.4472.114 Spotify/1.1.67.586" --lang=en --log-file="C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.167.586.0_x86__zpdnekdrzrea0\debug.log" --mojo-platform-channel-handle=3252 /prefetch:8
8136    Spotify.exe     "C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.167.586.0_x86__zpdnekdrzrea0\Spotify.exe" --type=renderer --log-file="C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.167.586.0_x86__zpdnekdrzrea0\debug.log" --field-trial-handle=2108,4839584854497019253,9112382588695800992,131072 --disable-features=CalculateNativeWinOcclusion --disable-gpu-compositing --lang=en-US --log-file="C:\Program Files\WindowsApps\SpotifyAB.SpotifyMusic_1.167.586.0_x86__zpdnekdrzrea0\debug.log" --log-severity=disable --user-agent-product="Chrome/91.0.4472.114 Spotify/1.1.67.586" --disable-spell-checking --device-scale-factor=1 --num-raster-threads=2 --enable-main-frame-before-activation --renderer-client-id=5 --mojo-platform-channel-handle=3532 /prefetch:1
7480    TextInputHost.  "C:\Windows\SystemApps\MicrosoftWindows.Client.CBS_cw5n1h2txyewy\InputApp\TextInputHost.exe" -ServerName:InputApp.AppX9jnwykgrccxc8by3hsrsh07r423xzvav.mca
3944    dllhost.exe     C:\WINDOWS\system32\DllHost.exe /Processid:{973D20D7-562D-44B9-B70B-5A0F49CCDF3F}
8044    ApplicationFra  C:\WINDOWS\system32\ApplicationFrameHost.exe -Embedding
7584    svchost.exe     C:\WINDOWS\System32\svchost.exe -k NetworkService -p -s DoSvc
8336    svchost.exe     C:\WINDOWS\System32\svchost.exe -k LocalSystemNetworkRestricted -p -s StorSvc
8412    SgrmBroker.exe  C:\WINDOWS\system32\SgrmBroker.exe
8584    svchost.exe     C:\WINDOWS\system32\svchost.exe -k netsvcs -p -s UsoSvc
8656    svchost.exe     C:\WINDOWS\System32\svchost.exe -k LocalServiceNetworkRestricted -p -s wscsvc
8696    svchost.exe     C:\WINDOWS\system32\svchost.exe -k UnistackSvcGroup
9500    RuntimeBroker.  Required memory at 0x188c83a020 is not valid (process exited?)
10208   WinStore.App.e  "C:\Program Files\WindowsApps\Microsoft.WindowsStore_12107.1001.15.0_x64__8wekyb3d8bbwe\WinStore.App.exe" -ServerName:App.AppXc75wvwned5vhz4xyxxecvgdjhdkgsdza.mca
1700    RuntimeBroker.  C:\Windows\System32\RuntimeBroker.exe -Embedding
9692    svchost.exe     C:\WINDOWS\System32\svchost.exe -k netsvcs -p
2928    SystemSettings  "C:\Windows\ImmersiveControlPanel\SystemSettings.exe" -ServerName:microsoft.windows.immersivecontrolpanel
8020    UserOOBEBroker  C:\Windows\System32\oobe\UserOOBEBroker.exe -Embedding
9544    ShellExperienc  "C:\Windows\SystemApps\ShellExperienceHost_cw5n1h2txyewy\ShellExperienceHost.exe" -ServerName:App.AppXtk181tbxbce2qsex02s8tw7hfxa9xb3t.mca
9452    RuntimeBroker.  C:\Windows\System32\RuntimeBroker.exe -Embedding
1796    powershell.exe  "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" 
8592    conhost.exe     \??\C:\WINDOWS\system32\conhost.exe 0x4
9872    svchost.exe     Required memory at 0x3b47875020 is not valid (process exited?)
1832    powershell_ise  "C:\WINDOWS\system32\WindowsPowerShell\v1.0\PowerShell_ISE.exe" 
9428    svchost.exe     C:\WINDOWS\system32\svchost.exe -k LocalServiceAndNoImpersonation -p -s SSDPSRV
10648   svchost.exe     C:\WINDOWS\system32\svchost.exe -k WbioSvcGroup -s WbioSrvc
10992   conhost.exe     \??\C:\WINDOWS\system32\conhost.exe 0x4
10284   powershell.exe  "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" 
10268   conhost.exe     \??\C:\WINDOWS\system32\conhost.exe 0x4
10840   svchost.exe     C:\WINDOWS\system32\svchost.exe -k netsvcs -p -s wuauserv
10500   SearchProtocol  "C:\WINDOWS\system32\SearchProtocolHost.exe" Global\UsGthrFltPipeMssGthrPipe4_ Global\UsGthrCtrlFltPipeMssGthrPipe4 1 -2147483646 "Software\Microsoft\Windows Search" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT; MS Search 4.0 Robot)" "C:\ProgramData\Microsoft\Search\Data\Temp\usgthrsvc" "DownLevelDaemon" 
4064    svchost.exe     C:\WINDOWS\system32\svchost.exe -k appmodel -p -s camsvc
10008   svchost.exe     C:\WINDOWS\system32\svchost.exe -k wsappx -p -s AppXSvc
5948    svchost.exe     C:\WINDOWS\System32\svchost.exe -k wsappx -p -s ClipSVC
8180    userinit.exe    C:\Windows\Temp\userinit.exe
5864    SearchFilterHo  "C:\WINDOWS\system32\SearchFilterHost.exe" 0 800 804 812 8192 808 784 
3652    msedge.exe      "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --no-startup-window /prefetch:5
6032    msedge.exe      "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --type=crashpad-handler "--user-data-dir=C:\Users\Jimmie\AppData\Local\Microsoft\Edge\User Data" /prefetch:7 --monitor-self-annotation=ptype=crashpad-handler "--database=C:\Users\Jimmie\AppData\Local\Microsoft\Edge\User Data\Crashpad" --annotation=IsOfficialBuild=1 --annotation=channel= --annotation=chromium-version=93.0.4577.63 "--annotation=exe=C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --annotation=plat=Win64 "--annotation=prod=Microsoft Edge" --annotation=ver=93.0.961.38 --initial-client-data=0xf0,0xf4,0xf8,0xcc,0xfc,0x7ff88f5076c8,0x7ff88f5076d8,0x7ff88f5076e8
7008    msedge.exe      "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --type=gpu-process --field-trial-handle=2052,8545982222989981453,14056150474032184914,131072 --gpu-preferences=UAAAAAAAAADgAAAQAAAAAAAAAAAAAAAAAABgAAAAAAAwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAHgAAAAAAAAAeAAAAAAAAAAoAAAABAAAACAAAAAAAAAAKAAAAAAAAAAwAAAAAAAAADgAAAAAAAAAEAAAAAAAAAAAAAAADQAAABAAAAAAAAAAAQAAAA0AAAAQAAAAAAAAAAQAAAANAAAAEAAAAAAAAAAHAAAADQAAAAgAAAAAAAAACAAAAAAAAAA= --mojo-platform-channel-handle=2228 /prefetch:2
1628    msedge.exe      "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --type=utility --utility-sub-type=network.mojom.NetworkService --field-trial-handle=2052,8545982222989981453,14056150474032184914,131072 --lang=en-US --service-sandbox-type=none --mojo-platform-channel-handle=2328 /prefetch:3
4924    msedge.exe      "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --type=utility --utility-sub-type=storage.mojom.StorageService --field-trial-handle=2052,8545982222989981453,14056150474032184914,131072 --lang=en-US --service-sandbox-type=utility --mojo-platform-channel-handle=2964 /prefetch:8
4248    smartscreen.ex  C:\Windows\System32\smartscreen.exe -Embedding
3556    msedge.exe      Required memory at 0xac6f8ee020 is not valid (process exited?)
9896    msedge.exe      Required memory at 0xa9810be020 is not valid (process exited?)
32      msedge.exe      "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --type=renderer --disable-client-side-phishing-detection --field-trial-handle=2052,8545982222989981453,14056150474032184914,131072 --disable-gpu-compositing --lang=en-US --device-scale-factor=1 --num-raster-threads=2 --enable-main-frame-before-activation --renderer-client-id=7 --no-v8-untrusted-code-mitigations --mojo-platform-channel-handle=5140 /prefetch:1
2488    msedge.exe      "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --type=renderer --disable-client-side-phishing-detection --field-trial-handle=2052,8545982222989981453,14056150474032184914,131072 --disable-gpu-compositing --lang=en-US --device-scale-factor=1 --num-raster-threads=2 --enable-main-frame-before-activation --renderer-client-id=9 --no-v8-untrusted-code-mitigations --mojo-platform-channel-handle=5828 /prefetch:1
10808   msedge.exe      "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --type=renderer --disable-client-side-phishing-detection --field-trial-handle=2052,8545982222989981453,14056150474032184914,131072 --disable-gpu-compositing --lang=en-US --device-scale-factor=1 --num-raster-threads=2 --enable-main-frame-before-activation --renderer-client-id=10 --no-v8-untrusted-code-mitigations --mojo-platform-channel-handle=4132 /prefetch:1
6540    msedge.exe      "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --type=utility --utility-sub-type=audio.mojom.AudioService --field-trial-handle=2052,8545982222989981453,14056150474032184914,131072 --lang=en-US --service-sandbox-type=audio --mojo-platform-channel-handle=6256 /prefetch:8
420     msedge.exe      "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --type=renderer --disable-client-side-phishing-detection --field-trial-handle=2052,8545982222989981453,14056150474032184914,131072 --disable-gpu-compositing --lang=en-US --device-scale-factor=1 --num-raster-threads=2 --enable-main-frame-before-activation --renderer-client-id=12 --no-v8-untrusted-code-mitigations --mojo-platform-channel-handle=6504 /prefetch:1
10432   notepad.exe     "C:\WINDOWS\system32\notepad.exe" 
10748   Calculator.exe  "C:\Program Files\WindowsApps\Microsoft.WindowsCalculator_10.2103.8.0_x64__8wekyb3d8bbwe\Calculator.exe" -ServerName:App.AppXsm3pg4n7er43kdh1qp4e79f1j7am68r8.mca
4156    RuntimeBroker.  C:\Windows\System32\RuntimeBroker.exe -Embedding
1996    msedge.exe      "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --type=renderer --disable-client-side-phishing-detection --field-trial-handle=2052,8545982222989981453,14056150474032184914,131072 --disable-gpu-compositing --lang=en-US --device-scale-factor=1 --num-raster-threads=2 --enable-main-frame-before-activation --renderer-client-id=13 --no-v8-untrusted-code-mitigations --mojo-platform-channel-handle=6280 /prefetch:1
992     WWAHost.exe     "C:\Windows\system32\wwahost.exe" -ServerName:OfficeHubHWA.wwa
2744    msedge.exe      Required memory at 0xc7569f5020 is not valid (process exited?)
5240    msedge.exe      "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --type=renderer --disable-client-side-phishing-detection --field-trial-handle=2052,8545982222989981453,14056150474032184914,131072 --disable-gpu-compositing --lang=en-US --device-scale-factor=1 --num-raster-threads=2 --enable-main-frame-before-activation --renderer-client-id=15 --no-v8-untrusted-code-mitigations --mojo-platform-channel-handle=7216 /prefetch:1
5832    msedge.exe      "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --type=utility --utility-sub-type=entity_extraction_service.mojom.Extractor --field-trial-handle=2052,8545982222989981453,14056150474032184914,131072 --lang=en-US --service-sandbox-type=entity_extraction --mojo-platform-channel-handle=7408 /prefetch:8
5860    winpmem_mini_x  "C:\Users\Jimmie\Downloads\winpmem_mini_x64_rc2.exe" physmemraw

```

One line that looks odd is;

```
8180    userinit.exe    C:\Windows\Temp\userinit.exe
```

You can see that this process is running from the `C:\Windows\Temp` directory, which is a little odd!

We took a guess on this as it seemed suspicious and it paid off... the flag was;

## flag{userinit.exe_8180}
