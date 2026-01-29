# Day 06 assignment – Linux Fundamentals: Read and Write Text Files
### Creating a file
- `touch notes.txt` Creating a file named notes.txt.
### Writing text to a file
- `echo "Hello dosto" > notes.txt` Writing message in notes.txt.
### Appending new lines
- `echo "Aaj mausam bahut achha hai" >> notes.txt` Appending new message in notes.txt.
- `echo "or aaj hum padhne wale hai devops" | tee -a notes.txt` Appending new message in notes.txt. (`tee` write and display at the same time)
- `echo "to chliye suru krte hai" | tee -a notes.txt` Appending new message in notes.txt.
### Reading the file back
- `cat notes.txt` Reading file.
- `head -n 2 notes.txt` Shows first 2 lines of notes.txt
- `tail -n 2 notes.txt` Shows last 2 lines of notes.txt

#### Output
```
ubuntu@ip-172-31-17-215:~$ touch notes.txt
ubuntu@ip-172-31-17-215:~$ ls
90DaysOfDevOps  Linux_2k.log  aws  awscliv2.zip  backup.sh  backups  commands.txt  devops  goal.txt  iostat_10min.log  notes.txt  ok  scripts
ubuntu@ip-172-31-17-215:~$ echo "Hello dosto" > notes.txt
ubuntu@ip-172-31-17-215:~$ cat notes.txt
Hello dosto
ubuntu@ip-172-31-17-215:~$ echo "Aaj mausam bahut badhiya hai" >> notes.txt
ubuntu@ip-172-31-17-215:~$ echo "or aaj hum padhne wale hai devops" | tee -a notes.txt
or aaj hum padhne wale hai devops
ubuntu@ip-172-31-17-215:~$ echo "or chliye suru krte hai" | tee -a notes.txt
or chliye suru krte hai
ubuntu@ip-172-31-17-215:~$ cat notes.txt
Hello dosto
Aaj mausam bahut badhiya hai
or aaj hum padhne wale hai devops
or chliye suru krte hai
ubuntu@ip-172-31-17-215:~$ head -n 2 notes.txt
Hello dosto
Aaj mausam bahut badhiya hai
ubuntu@ip-172-31-17-215:~$ tail -n 2 notes.txt
or aaj hum padhne wale hai devops
or chliye suru krte hai
ubuntu@ip-172-31-17-215:~$ vim notes.txt
ubuntu@ip-172-31-17-215:~$ tail -n 2 notes.txt
or aaj hum padhne wale hai devops
to chliye suru krte hai
```
