# Checking-OUP-DOIs
Checking a sample of OUP's recently minted DOIs and comparing it to a control sample of recently minted DOIs at non-OUP journals indexed in pubmed

I like shell scripting. Bashtastic!

Sample bash code to reproduce the logfiles, given the DOI links in each journal folder within the non-OUP journals:
(You will need to replace the path "/home/ross/Checking-OUP-DOIs" with whatever the absolute path is on your computer)
(A user-agent is unfortunately required for Elsevier journals I think)

```
cd non-OUP

#parse out the DOIs from the pubmed screenscrape files, each called raw.txt
for dir in */ ; do cd $dir ; grep doi raw.txt |  tr ' ' '\n' | grep '10\.[0-9]' | sed 's/\.$//g' | sed 's/^/http:\/\/doi.org\//g' | sort -u > links.txt ; head -3 links.txt ; wc links.txt ; cd /home/ross/Checking-OUP-DOIs/non-OUP/ ; done

#Test each and every DOI. This step will take a long time. Set it running and get on with other work...
for dir in */ ; do cd $dir ; wget --user-agent="Mozilla/5.0 (Macintosh; Intel Mac OS X 10.8; rv:21.0) Gecko/20100101 Firefox/21.0" -w1 -i links.txt -o log.log ; cd /home/ross/Checking-OUP-DOIs/non-OUP/ ; done 

#Parse wget log files for 404 errors
grep -r "ERROR 404: Not Found" *
```

As Geoffrey Bilder mentions, there are probably much much better ways of doing this! I scripted this very hastily.
http://rossmounce.co.uk/2017/01/25/comparing-oup-to-other-publishers/#comment-3120769581
