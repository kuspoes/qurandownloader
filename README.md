qurandownloader
=================================================

Python 3 script to download Quran MP3 Recitations
=================================================

This is a tiny utility to download MP3 quran recitations from web sites. I have included my
personal reciters (in the reciterList dict object), however the user is free to add his or her
own list from a file when executing the script.

1. In every request for download an MP3 file, the name code of the reciter must be supplied with:

-r codeName or --reciter codeName

codeName is anything you wish to call your reciter.

2. Multiple reciters can be requested:

qurandownloader --reciter codeName1 --reciter codeName2 -r codeName 3.

If the MP3 recitations exist on the remote server exist, each recitation will be downloaded.

3. There are three ways to select a recitation:

[a]. --all or -a: This will download all 114 MP3 recitations or any that exist.

Example: qurandownloader -r aKanakiri -r mAyyub -r mMinshawi --all (or -a)
 
[b]. --range or -g: This will download MP3 recitations with a specific range.

Example: qurandownloader -r aAbdussamad --range 90-114

All Suras from 90 all the way to Sura 114 for the reciter Abdulbassit Abdussamad will be downloaded.

[c]. --singleSura or -s: This will download a single Sura, or many Suras as you may specify.

Example 1: qurandownloader -r aKanakiri -s10
Example 2: qurandownloader -r aMatrood -s7 -s11 -s 3 -s 8 -s 19 -s18
(spaces are irrelevant.)

4. There are 2 ways to add your own list of reciters:

First way: With a file

This is done by supplying an -f argument to qurandownloader pointing to a file that contains a list of
reciters. To make your own list, you should MAKE SURE that the web server saves the MP3 recitations
in the common way most webservers do. That is: xxx.mp3, where xxx is any number from 1 - 114. If
you can access the MP3 file in such a way:

http://some.host.com/somewhere/012.mp3

then, you're ready. A file, then, should be prepared in the following format:

name_of_reciter:http://some.host.com/somewhere/
OR
name_of_reciter2.http://another.host.net/some/remote/directory/

(see qurandownloader --help)

Second way: by updating the script!

At the end of the script where you can see:

############################
def main():
  try:
    d1 = QuranDownloader()
    reciter = str()
    dir1 = str()
#############################

just make it look this way:

def main():
  try:
    d1 = QuranDownloader()
##### Add ######
    d1.reciterList.update({"yourReciter1":"http://some.remote.host.com/rest/of/url/"})
    d1.reciterList.update({"yourReciter2":"http://sremote.host.net/path/to/reciter/files/"})
##### and so on... #####
    reciter = str()
    dir1 = str()

5. Directories: By default qurandownloader saves the files in a local directory, you can however
direct the script to save the downloaded files to another director:

Example: qurandownloader -r aKhayat -d /home/Audios/ -s 15 -g 1-3

6. To list the available reciters, simply do: qurandownloader --list or -l

---
Abdalla S. Alothman

