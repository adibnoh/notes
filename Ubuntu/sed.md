# Sed is the ultimate stream editor

If using mac, it is better to install gnu-sed

`brew install gnu-sed`

And then use gsed instead of sed, which will just work as expected.

## Commands

All commands below is referring to content below. Assume we are in directory where file demo.txt is located. Content of file demo.txt is

```txt
Copyright (c) 2022, FTW All rights reserved.

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

Rules are:

1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.
2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
3. All advertising materials mentioning features or use of this software must display the following acknowledgement: This product includes software developed by the FTW.
4. Neither the name of the FTW nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.
```

### Replace

Replace `rights` with `wrong`. `s` stand for substitute.

`sed 's/rights/wrong/' demo.txt`

Command above is not going to modify demo.txt file. To modify file, we need to add `-i` argument

`sed -i 's/rights/wrong/' demo.txt`

It is reconmmended to create a backup file when modifying any file. To keep a backup, we can add append our argument `-i` with any file extension, such as `-i.bak`

`sed -i.bak 's/rights/wrong/' demo.txt`

SED will operate all command line by line, and will only target first occurence of each line

for examples:

```
Copyright (c) 2022, FTW All rights reserved rights.
Redistribution and rights in source and binary forms.
``` 

this sentence has 2 occurences of `rights` on first line, but command `sed 's/rights/wrong/' demo.txt` will only replace first occurences on first line. To target all occurences for each lines, we need to add `g` in our command expression, such so

`sed 's/rights/wrong/g' demo.txt`

### Append

This command will append content on a new line after an expression found a match. This command below will append `All goods here` after `Rules are:`

`sed '/Rules are:/a All goods here' demo.txt`

Command above is not going to modify demo.txt file. To modify file, we need to add `-i` argument

`sed -i '/Rules are:/a All goods here' demo.txt`

It is reconmmended to create a backup file when modifying any file. To keep a backup, we can add append our argument `-i` with any file extension, such as `-i.bak`

`sed -i.bak '/Rules are:/a All goods here' demo.txt`

## Reference

* [Sed - An Introduction and Tutorial by Bruce Barnett](https://www.grymoire.com/Unix/Sed.html#uh-0)
* [https://stackoverflow.com/a/60562182](https://stackoverflow.com/a/60562182)