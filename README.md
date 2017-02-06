# Checking-OUP-DOIs

I am fed-up of broken DOIs that do not resolve to the article landing page that they should.
I therefore decided to test a sample of DOIs across ALL journals that Oxford University Press (OUP) publishes.

I tested across 394 OUP journals, using the CrossRef API to return me the 100 most recent DOIs from each journal and the 100 oldest DOIs from each journal. In total 70,907 unique DOIs were checked.

Across this sample I found that 1692 of these DOIs were 'broken' - they did not resolve to an article landing page and instead they return the HTTP 404 Not Found error message. This is 2.386 % of the sample of DOIs tested.

I would expect an error rate of less than 0.5% and competent publishers that care about this issue could ensure that there are no broken DOIs. I wonder if and when OUP might fix all these broken DOIs?

##Full list of broken DOIs that are the responsiblity of OUP
[/main/all-unique-404-OUP-dois.txt](./main/all-unique-404-OUP-dois.txt)

##Full list of 70,907 sampled DOIs
[/main/uniq-OUP-dois-tested.txt](./main/uniq-OUP-dois-tested.txt)
