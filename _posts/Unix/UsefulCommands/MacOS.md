---


---

<h3 id="macos-useful-command">MacOS Useful command:</h3>
<p>atos -arch arm64 -o ISD.framework.dSYM/Contents/Resources/DWARF/ISD 205640</p>
<p>dwarfdump --arch arm64 ISD.framework.dSYM/Contents/Resources/DWARF/ISD --lookup 0x2d688</p>
<p>gobjdump -d <a href="http://libXXXisd.so">libXXXisd.so</a> --target elf32-littlearm<br>
gobjdump -d <a href="http://libXXX.so">libXXX.so</a> --target elf64-littleaarch64</p>

