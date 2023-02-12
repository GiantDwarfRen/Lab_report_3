# Lab Report 3
Here is the [website](https://man7.org/linux/man-pages/man1/grep.1.html) that I found command-line option for `grep`
## -i --ignore-case
Ignore case distinctions in patterns and input data, so that characters that differ only in case match each other.
1. This is the case about "Lucayans" in our example. There is no "lucayans" in files, but if we ignore the case, we can find one in "Lucayans".
```
vincentren@ Lab_report_3 % grep -rl "lucayans" > grep-result.txt
vincentren@ Lab_report_3 % grep -irl "lucayans" > grep-result-ig.txt
vincentren@ Lab_report_3 % wc grep-result.txt 
       0       0       0 grep-result.txt
vincentren@ Lab_report_3 % wc grep-result-ig.txt 
       1       1      55 grep-result-ig.txt
```

2. To grep "To", if we just looking for "To", the number found will be less than if we ignore "to".
```
vincentren@ Lab_report_3 % grep -rl "To" > grep-result.txt
vincentren@ Lab_report_3 % grep -irl "To" > grep-result-ign.txt
vincentren@ Lab_report_3 % wc grep-result.txt 
     254     254   13233 grep-result.txt
vincentren@ Lab_report_3 % wc grep-result-ign.txt 
     362     362   19075 grep-result-ign.txt
```

