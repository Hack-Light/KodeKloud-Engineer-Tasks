# QUESTION

There is some data on `Nautilus App Server 3` in Stratos DC. Data needs to be altered in several of the files. On Nautilus App Server 3, alter the `/home/BSD.txt` file as per details given below:

1. Delete all lines containing word following and save results in `/home/BSD_DELETE.txt` file1. (Please be aware of case sensitivity)

2. Replace all occurrence of word `or` to `them` and save results in `/home/BSD_REPLACE.txt1` file.

> Note: Let's say you are asked to replace word to with from. In that case, make sure not to alter any words containing this string; for example upto, contributor etc.

# SOLUTION

```bash
# ssh into the server
ssh steve@stapp03

# delete
sed -e '/following/d' /home/BSD.txt > /home/BSD_DELETE.txt

# replace
sed 's/\bor\b/them/g' /home/BSD.txt > /home/BSD_REPLACE.txt

# confirm operations
cat /home/BSD_DELETE.txt
cat /home/BSD_REPLACE.txt
```
