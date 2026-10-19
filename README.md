Linux CLI Practical

These are my notes from practising basic Linux commands in the Ubuntu terminal on my Windows laptop. I have also written down the mistakes I made, because I learned most from those.


Part 1: files, folders and /etc/passwd

I started with mkdir test_dir, but the folder was already there so it said "File exists". I carried on with the same folder.

touch example.txt makes an empty file. I ran it once in the home folder and once inside test_dir after going in with cd test_dir.

mv is used to rename a file. mv example.txt renamed_example1.txt changed the name. My mistake here was typing the names the wrong way round the first time (mv renamed_example1.txt example.txt). mv takes the old name first and the new name second, so it said no such file or directory.

cat /etc/passwd prints the full list of user accounts. head -n5 /etc/passwd shows only the first five lines.


Part 2: tail, grep and installing zip

tail -n5 /etc/passwd shows the last five lines, and my own user acer is at the bottom. grep "root" /etc/passwd prints only the lines which have the word root in them.

I installed zip with sudo apt install zip. It asked for my password and then Y/n, and it installed unzip along with it.

Mistakes here: I typed LS in capital letters and got "command not found", because Linux commands are case sensitive. Then I ran zip -r test_dir.zip test_dir while I was already inside test_dir, so there was no test_dir to zip and it gave "zip file empty".


Part 3: zip, unzip, wget, chmod and export

I tried echo "Hello Angad" > test_dir/renamed_example1.txt but I was already inside test_dir, so the path was wrong. Then I did cd renamed_example1.txt, which failed with "Not a directory" because it is a file. I should have checked with pwd first.

The correct way was zip -r test_dir.zip . where the dot means the current folder. It added both files this time. Then I went back with cd ~, made a folder with mkdir -p unzipped_dir and extracted using unzip test_dir/test_dir.zip -d unzipped_dir. ls unzipped_dir showed both files, so it worked.

wget downloads a file from a link. I used it on a sample API link and got 200 OK and a small JSON file. The file got saved as users?page=2 because of the question mark in the link, so ls shows it in quotes.

touch secure.txt and chmod 444 secure.txt made the file read only for everyone. ls -l secure.txt showed -r--r--r-- which confirms it.

export MY_VAR ="HELLO LINUX" gave "not a valid identifier" because I left a space before the equals sign. export MY_VAR="Hello Linux" worked.


Mistakes I made

1. wrote the mv names in the wrong order
2. typed LS instead of ls
3. zipped test_dir from inside test_dir
4. used a wrong path and did cd into a file
5. put a space before = in export


What I learned

Most of my errors happened because I did not know which folder I was in. Next time I will use pwd and ls before using any path, and read the error message properly, because every error told me exactly what was wrong.


Files in this repo

commands.sh has all the commands that worked, in order.
The screenshots folder has the terminal screenshots.
The docs folder has the Word document with the same explanation.
The files folder has the sample files I created.
