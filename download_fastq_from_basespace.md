# Downloading fastq files from Illumina's Basespace

* You received a link from CAG/whomever for Basespace links to fastq files

* Upon first visit to Basespace, you will have to register and login

* Once the above is fulfilled, you will see at the top of the Basespace page for you data a name like so:

```
YOURNAME_000000_A00000_0000_AAA0A0AAA0
```

* Keep this name handy

* Assuming you will do this in some Linux environment (cluster preferably but you could do this locally on a Mac):

```
# change directories to whatever you like (just make sure it exists):
cd here/is/a/directory

# make a directory for the script to download the fastq files, download the script, and activate it:
mkdir -p scripts
wget "https://launch.basespace.illumina.com/CLI/latest/amd64-linux/bs" -O ./scripts/bs
chmod u+x scripts/bs

# run the script:
scripts/bs auth

# there will be some info printed in your terminal, including a URL
# you will have to go to the URL provided (open in a browser of choice)

# once authenticated via the above URL, go back to the terminal
# remember that long name I said to keep handy?
# copy it so you can paste it below (replace the YOURNAME_000000_A00000_0000_AAA0A0AAA0 below with your project's name)
# this will download ALL the fastq files simultaneously:
scripts/bs download project --name YOURNAME_000000_A00000_0000_AAA0A0AAA0

# at this point, you could move these (or could have made a new dir and moved to it before the command - your choice)
# e.g., made data dir and moved above to it:
mkdir -p data
mkdir -p data/fastq
# OPTIONAL: check to ensure you are not moving anything you would otherwise not want to move:
ls -ltrh *fastq.gz
# move them:
mv -f *fastq.gz data/fastq/
```
