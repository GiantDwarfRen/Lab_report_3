# Lab Report 3
Here is the [website](https://man7.org/linux/man-pages/man1/grep.1.html) that I found command-line option for `grep`
## -i, --ignore-case
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

## -v, --invert-match
Invert the sense of matching, to select non-matching lines.
1. From `-i` section, we know that "Lucayans" shows up in `./written_2/travel_guides/berlitz2/Bahamas-History.txt`. If we just grep "Lucayans" in that `berlitz2` folder, the number found would be just 1. However, if we grep "Lucayans" using `-v`, we would found all files in `berlitz2` except `Bahamas-History.txt`.
```
vincentren@ Lab_report_3 % grep -vl "Lucayans" written_2/travel_guides/berlitz2/*.txt > grep-result-invert.txt
vincentren@ Lab_report_3 % grep -l "Lucayans" written_2/travel_guides/berlitz2/*.txt > grep-result.txt        
vincentren@ Lab_report_3 % wc grep-result-invert.txt 
      78      78    4211 grep-result-invert.txt
vincentren@ Lab_report_3 % wc grep-result.txt 
       1       1      53 grep-result.txt
```

2. Considering the same folder `berlitz2`. The difference of using `-v` and without using `-v` searching for "To" is showed below. The reason behind that is the same.
```
vincentren@ Lab_report_3 % grep -vl "To" written_2/travel_guides/berlitz2/*.txt > grep-result-invert.txt
vincentren@ Lab_report_3 % grep -l "To" written_2/travel_guides/berlitz2/*.txt > grep-result.txt        
vincentren@ Lab_report_3 % wc grep-result-invert.txt 
      78      78    4211 grep-result-invert.txt
vincentren@ Lab_report_3 % wc grep-result.txt 
      73      73    3945 grep-result.txt
```

## -n, --line-number
Prefix each line of output with the 1-based line number within its input file.
1. Using `-n`, we can know the line number of "vista"
```
vincentren@ Lab_report_3 % grep -rn "vista" > grep-result.txt
vincentren@ Lab_report_3 % cat grep-result.txt 
./written_2/travel_guides/berlitz1/IntroDublin.txt:40:        unexpected distant vistas will remind you that Dublin is by the sea,
./written_2/travel_guides/berlitz1/IntroMadeira.txt:86:        rewarded with spectacular vistas can be an exhilarating experience, but
./written_2/travel_guides/berlitz1/WhereToGreek.txt:172:        ancient port, now silted up. From here, the vista of the whole town can
./written_2/travel_guides/berlitz1/WhereToLakeDistrict.txt:466:        Harrison Stickle and Crinkle Crags — produce some of the finest vistas
./written_2/travel_guides/berlitz1/WhereToLakeDistrict.txt:894:        View,” a lookout that offers a panoramic vista of Derwent Water with
./written_2/travel_guides/berlitz1/WhereToIsrael.txt:1054:        rolling vistas of sand dunes, but is instead a rocky wasteland of
./written_2/travel_guides/berlitz1/WhereToFrance.txt:286:        vista was originally planned for Napo­leon to see from his bedroom in
./written_2/travel_guides/berlitz1/WhereToFrance.txt:2206:        The little port town of Cancale — with a wide vista across
...
```

2. Using `-n`, we can konw the line number of "Lucayans"
```
vincentren@ Lab_report_3 % grep -rn "Lucayans" > grep-result.txt
vincentren@ Lab_report_3 % cat grep-result.txt 
./written_2/travel_guides/berlitz2/Bahamas-History.txt:6:Centuries before the arrival of Columbus, a peaceful...
./written_2/travel_guides/berlitz2/Bahamas-History.txt:7:The Spaniards never bothered to settle in the Bahamas, but...
```