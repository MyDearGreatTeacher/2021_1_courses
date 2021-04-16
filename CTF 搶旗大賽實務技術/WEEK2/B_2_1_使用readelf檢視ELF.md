# 使用readelf檢視ELF
```
readelf
readelf檢視技術
```
# readelf
```
readelf is a program for displaying various information about object files 
on Unix-like systems such as objdump. 
It is part of the GNU binutils

https://linux.die.net/man/1/readelf
```
```
https://man7.org/linux/man-pages/man1/readelf.1.html

readelf [-a|--all]
               [-h|--file-header]  查看ELF header
               [-l|--program-headers|--segments]
               [-S|--section-headers|--sections]   查看Sections header
               [-g|--section-groups]
               [-t|--section-details]
               [-e|--headers]
               [-s|--syms|--symbols]
               [--dyn-syms]
               [-n|--notes]
               [-r|--relocs] 顯示文件的重定位部分的內容（如果有的話）
               [-u|--unwind]
               [-d|--dynamic]
               [-V|--version-info]
               [-A|--arch-specific]
               [-D|--use-dynamic]
               [-L|--lint|--enable-checks]
               [-x <number or name>|--hex-dump=<number or name>]
               [-p <number or name>|--string-dump=<number or name>]
               [-R <number or name>|--relocated-dump=<number or name>]
               [-z|--decompress]
               [-c|--archive-index]
               [-w[lLiaprmfFsoORtUuTgAckK]|
                --debug-dump[=rawline,=decodedline,=info,=abbrev,=pubnames,=aranges,=macro,
                       =frames,=frames-interp,=str,=str-offsets,=loc,=Ranges,=pubtypes,=trace_info,
                       =trace_abbrev,=trace_aranges,=gdb_index,=addr,=cu_index,=links,=follow-links]]
               [--dwarf-depth=n]
               [--dwarf-start=n]
               [--ctf=section]
               [--ctf-parent=section]
               [--ctf-symbols=section]
               [--ctf-strings=section]
               [-I|--histogram]
               [-v|--version]  顯示readelf的版本
               [-W|--wide]
               [-T|--silent-truncation]
               [-H|--help]    顯示readelf可以理解的命令行選項
               elffile...
```
# readelf分析技術
```
readelf - Displays information about ELF files.

查看ELF header   
查看可執行文件的入口處
查看Sections header
查看program header
查看重定表(Relocation Table)
[Examining the Relocation Section]
查看符號表system Table

查看某特定section
```
## 查看ELF header
```

```
# 
