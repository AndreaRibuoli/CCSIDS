# CCSIDS

### Extract CCSIDs' definitions

---

This is an example of package for IBM i that simply executes on the target system
without actually installing a library permanently.

It is packaged consistently with [**WOPASE** ](https://github.com/AndreaRibuoli/WOPASE) format and conventions.

Uses a recently modified version of [**TMKMAKE** ](https://github.com/AndreaRibuoli/TMKMAKE) that is expected to be already
installed in the target system.

The `IBM*.txt` files generated can be transformed into *Markdown\-friendly* files
using the following *Python* script:

``` python
import numpy as np
import pandas
import glob

c_names = ['-0','-1','-2','-3','-4','-5','-6','-7','-8','-9','-A','-B','-C','-D','-E','-F']
r_names = ['4-','5-','6-','7-','8-','9-','A-','B-','C-','D-','E-','F-']

tablesList = glob.glob('IBM*.txt')
for table in tablesList:
    with open(table, 'r') as f:
        s = f.read().replace('\n','')
    a = list(s)
    t = np.matrix([a[i:i + 16] for i in range(0, len(a), 16)])    
    df = pandas.DataFrame(t, columns = c_names, index = r_names)
    md = table.replace('txt','md')
    with open(md, 'w') as m:
        o = df.to_markdown()
        m.write(o)
```

Two examples (`IBM280.md` and `IBM1148.md`) are included.

### IBM280.md
----
|    | -0   | -1   | -2   | -3   | -4   | -5   | -6   | -7   | -8   | -9   | -A   | -B   | -C   | -D   | -E   | -F   |
|:---|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
| 4- |      |      | â    | ä    | {    | á    | ã    | å    | \    | ñ    | °    | .    | <    | (    | +    | !    |
| 5- | &    | ]    | ê    | ë    | }    | í    | î    | ï    | ~    | ß    | é    | $    | *    | )    | ;    | ^    |
| 6- | -    | /    | Â    | Ä    | À    | Á    | Ã    | Å    | Ç    | Ñ    | ò    | ,    | %    | _    | >    | ?    |
| 7- | ø    | É    | Ê    | Ë    | È    | Í    | Î    | Ï    | Ì    | ù    | :    | £    | §    | '    | =    | "    |
| 8- | Ø    | a    | b    | c    | d    | e    | f    | g    | h    | i    | «    | »    | ð    | ý    | þ    | ±    |
| 9- | [    | j    | k    | l    | m    | n    | o    | p    | q    | r    | ª    | º    | æ    | ¸    | Æ    | ¤    |
| A- | µ    | ì    | s    | t    | u    | v    | w    | x    | y    | z    | ¡    | ¿    | Ð    | Ý    | Þ    | ®    |
| B- | ¢    | #    | ¥    | ·    | ©    | @    | ¶    | ¼    | ½    | ¾    | ¬    | |    | ¯    | ¨    | ´    | ×    |
| C- | à    | A    | B    | C    | D    | E    | F    | G    | H    | I    | ­    | ô    | ö    | ¦    | ó    | õ    |
| D- | è    | J    | K    | L    | M    | N    | O    | P    | Q    | R    | ¹    | û    | ü    | `    | ú    | ÿ    |
| E- | ç    | ÷    | S    | T    | U    | V    | W    | X    | Y    | Z    | ²    | Ô    | Ö    | Ò    | Ó    | Õ    |
| F- | 0    | 1    | 2    | 3    | 4    | 5    | 6    | 7    | 8    | 9    | ³    | Û    | Ü    | Ù    | Ú    |       |
---

### IBM1148.md
----
|    | -0   | -1   | -2   | -3   | -4   | -5   | -6   | -7   | -8   | -9   | -A   | -B   | -C   | -D   | -E   | -F   |
|:---|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
| 4- |      |      | â    | ä    | à    | á    | ã    | å    | ç    | ñ    | [    | .    | <    | (    | +    | !    |
| 5- | &    | é    | ê    | ë    | è    | í    | î    | ï    | ì    | ß    | ]    | $    | *    | )    | ;    | ^    |
| 6- | -    | /    | Â    | Ä    | À    | Á    | Ã    | Å    | Ç    | Ñ    | ¦    | ,    | %    | _    | >    | ?    |
| 7- | ø    | É    | Ê    | Ë    | È    | Í    | Î    | Ï    | Ì    | `    | :    | #    | @    | '    | =    | "    |
| 8- | Ø    | a    | b    | c    | d    | e    | f    | g    | h    | i    | «    | »    | ð    | ý    | þ    | ±    |
| 9- | °    | j    | k    | l    | m    | n    | o    | p    | q    | r    | ª    | º    | æ    | ¸    | Æ    | €    |
| A- | µ    | ~    | s    | t    | u    | v    | w    | x    | y    | z    | ¡    | ¿    | Ð    | Ý    | Þ    | ®    |
| B- | ¢    | £    | ¥    | ·    | ©    | §    | ¶    | ¼    | ½    | ¾    | ¬    | |    | ¯    | ¨    | ´    | ×    |
| C- | {    | A    | B    | C    | D    | E    | F    | G    | H    | I    | ­    | ô    | ö    | ò    | ó    | õ    |
| D- | }    | J    | K    | L    | M    | N    | O    | P    | Q    | R    | ¹    | û    | ü    | ù    | ú    | ÿ    |
| E- | \    | ÷    | S    | T    | U    | V    | W    | X    | Y    | Z    | ²    | Ô    | Ö    | Ò    | Ó    | Õ    |
| F- | 0    | 1    | 2    | 3    | 4    | 5    | 6    | 7    | 8    | 9    | ³    | Û    | Ü    | Ù    | Ú    |       |
---