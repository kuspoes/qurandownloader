qurandownloader
=================================================

Python 3 script to download Quran MP3 Recitations
=================================================

This is a tiny utility to download MP3 quran recitations from web sites. I have included my
personal reciters (in the reciterList dict object), however the user is free to add his or her
own list from a file when executing the script.

1. In every request for download an MP3 file, the name code of the reciter must be supplied with:
<code>
-r codeName or --reciter codeName
</code>
codeName is anything you wish to call your reciter.

2. Multiple reciters can be requested:
<code>
qurandownloader --reciter codeName1 --reciter codeName2 -r codeName 3.
</code>
If the MP3 recitations exist on the remote server exist, each recitation will be downloaded.

3. There are three ways to select a recitation:

[a]. --all or -a: This will download all 114 MP3 recitations or any that exist.
<code>
Example: qurandownloader -r aKanakiri -r mAyyub -r mMinshawi --all (or -a)
 </code>
[b]. --range or -g: This will download MP3 recitations with a specific range.
<code>
Example: qurandownloader -r aAbdussamad --range 90-114
</code>
All Suras from 90 all the way to Sura 114 for the reciter Abdulbassit Abdussamad will be downloaded.

[c]. --singleSura or -s: This will download a single Sura, or many Suras as you may specify.
<code>
Example 1: qurandownloader -r aKanakiri -s10
Example 2: qurandownloader -r aMatrood -s7 -s11 -s 3 -s 8 -s 19 -s18
(spaces are irrelevant.)
</code>
4. There are 2 ways to add your own list of reciters:

<H3>First way: With a file</H3>

This is done by supplying an -f argument to qurandownloader pointing to a file that contains a list of
reciters. To make your own list, you should MAKE SURE that the web server saves the MP3 recitations
in the common way most webservers do. That is: xxx.mp3, where xxx is any number from 1 - 114. If
you can access the MP3 file in such a way:
<pre>
http://some.host.com/somewhere/012.mp3
</pre>
then, you're ready. A file, then, should be prepared in the following format:

<pre>name_of_reciter:http://some.host.com/somewhere/</pre>
OR
<pre>name_of_reciter2.http://another.host.net/some/remote/directory/</pre>

(see qurandownloader --help)

<H3>Second way: by updating the script!</H3>

At the end of the script where you can see:
<code>
def main():
  try:
    d1 = QuranDownloader()
    reciter = str()
    dir1 = str()
</code>
just make it look this way:

<code>
def main():
  try:
    d1 = QuranDownloader()
<b>
    d1.reciterList.update({"yourReciter1":"http://some.remote.host.com/rest/of/url/"})
    d1.reciterList.update({"yourReciter2":"http://sremote.host.net/path/to/reciter/files/"})
</b> 
    reciter = str()
    dir1 = str()
</code>
5. Directories: By default qurandownloader saves the files in a local directory, you can however
direct the script to save the downloaded files to another director:
<code>
Example: qurandownloader -r aKhayat -d /home/Audios/ -s 15 -g 1-3
</code>

6. There are two ways to download a random sura:
<code>
[a]. qurandownloader -R
</code>

This will download a random sura by a random reciter and exit.
<code>
[b]. qurandownloader -r myReciter1 -R
</code>

This will download a random sura by <i>myReciter</i>. You can specify as many reciters as you want, so
this is also valid:
<code>
qurandownloader -r aKanakiri -r aMatrood -r aHuthayfi -R
</code>
7. To list the available reciters, simply do: qurandownloader --list or -l

---
Abdalla S. Alothman

