# Day 16 Assignment – Shell Scripting Basics

## Task 1: Your First Script
1. Create a file `hello.sh`
2. Add the shebang line `#!/bin/bash` at the top
3. Print `Hello, DevOps!` using echo
4. Make it executable and run it
```
chmod +x hello.sh
./hello.sh
```
- Script:
  ```
  #!/bin/bash
  echo "Hello, DevOps!"
  
  ```
- Execution & output:
  ```
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim hello.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ chmod 764 hello.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./hello.sh
  Hello, DevOps!
  
  ---remove the shebang line---
  
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim hello.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./hello.sh
  Hello, DevOps!
  ```
#### Document: What happens if you remove the shebang line?
- nothing happened

---
## Task 2: Variables
1. Create `variables.sh` with:
    - A variable for your `NAME`
    - A variable for your `ROLE` (e.g., "DevOps Engineer")
    - Print: `Hello, I am <NAME> and I am a <ROLE>`
- Script:
  ```
  #!/bin/bash
  name="Dhannu"
  role="DevOps Engineer"
  echo "Hello, I am $name and I am a $role"
  
  ```
- Execution & output:
  ```
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim variables.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ chmod +x variables.sh 
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./variables.sh 
  ./variables.sh: line 4: Dhannu: command not found
  ./variables.sh: line 5: DevOps Engineer: command not found
  Hello, I am  and I am a 
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim variables.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./variables.sh 
  Hello, I am Dhannu and I am a DevOps Engineer

  --- using single quotes in name='Dhannu' ---
  
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim variables.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./variables.sh 
  Hello, I am Dhannu and I am a DevOps Engineer

  --- using single quotes in echo 'Hello, I am $name and I am a $role' ---
  
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim variables.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./variables.sh 
  Hello, I am $name and I am a $role
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim variables.sh
  ```
2. Try using single quotes vs double quotes — what's the difference?
- not working

---
## Task 3: User Input with read
1. Create `greet.sh` that:
    - Asks the user for their name using `read`
    - Asks for their favourite tool
    - Prints: `Hello <name>, your favourite tool is <tool>`
- Script:
  ```
  #!/bin/bash
  read -p "Enter your name: " NAME
  read -p "Enter your favourite tool: " TOOL
  echo "Hello $NAME, your favourite tool is $TOOL"
  
  ```
- Execution & output:
  ```
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim greet.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ chmod +x greet.sh 
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./greet.sh 
  ./greet.sh: line 6: read: `Enter your name: ': not a valid identifier
  ./greet.sh: line 7: read: `Enter your favourite tool: ': not a valid identifier
  Hello , your favourite tool is 
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim greet.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ chmod +x greet.sh 
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./greet.sh 
  Enter your name: Dhannu
  Enter your favourite tool: Github
  Hello Dhannu, your favourite tool is Github
  ```

---
## Task 4: If-Else Conditions
1. Create `check_number.sh` that:
    - Takes a number using `read`
    - Prints whether it is positive, negative, or zero
- Script:
  ```
  #!/bin/bash
  read -p "Enter a number: " num
  if [ "$num" -gt 0 ]; then
  	echo "The number is positive."
  elif [ "$num" -eq 0 ]; then
  	echo "The number is zero"
  else
  	echo "The number is negative."
  fi
  
  ```
- Execution & output:
  ```
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim check_number.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ chmod +x check_number.sh 
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./check_number.sh 
  Enter a number: 2
  ./check_number.sh: line 13: syntax error: unexpected end of file
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim check_number.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./check_number.sh 
  Enter a number: 3
  The number is positive.
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./check_number.sh 
  Enter a number: 36356
  The number is positive.
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./check_number.sh 
  Enter a number: 0
  The number is zero
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./check_number.sh 
  Enter a number: -43
  The number is negative.
  ```
2. Create `file_check.sh` that:
    - Asks for a filename
    - Checks if the file exists using `-f`
    - Prints appropriate message
- Script:
  ```
  #!/bin/bash
  read -p "Enter file to check: " filename
  
  if [ -f "$filename" ]; then
  	echo "File exists"
  else
  	echo "File don't exists"
  fi
  
  ```
- Execution & output:
  ```
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim file_check.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ chmod +x file_check.sh 
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./file_check.sh 
  Enter file to check: hello.txt
  File don't exists
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./file_check.sh 
  Enter file to check: hello.sh
  File exists
  ```

---
## Task 5: Combine It All
Create server_check.sh that:

1. Stores a service name in a variable (e.g., nginx, sshd)
2. Asks the user: "Do you want to check the status? (y/n)"
3. If y — runs systemctl status <service> and prints whether it's active or not
4. If n — prints "Skipped."
- Script:
  ```
  #!/bin/bash
  service="nginx"
  read -p "Do you want to check service status? (y/n): " reply
  if [ "$reply" == "y" ]; then
  	systemctl status $service
  elif [ "$reply" == "n" ]; then
  	echo "Skipped."
  else
  	echo "Wrong input.. please enter only (y/n)."
  fi
  
  ```
- Execution & output:
  ```
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim server_check.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ chmod +x server_check.sh 
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./server_check.sh 
  Do you want to check service status? (y/n): y
  ● nginx.service - A high performance web server and a reverse proxy server
       Loaded: loaded (/usr/lib/systemd/system/nginx.service; enabled; preset: enabled)
       Active: active (running) since Mon 2026-02-16 07:15:21 UTC; 2h 59min ago
         Docs: man:nginx(8)
      Process: 555 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
      Process: 605 ExecStart=/usr/sbin/nginx -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
     Main PID: 626 (nginx)
        Tasks: 3 (limit: 1008)
       Memory: 3.8M (peak: 4.3M)
          CPU: 34ms
       CGroup: /system.slice/nginx.service
               ├─626 "nginx: master process /usr/sbin/nginx -g daemon on; master_process on;"
               ├─627 "nginx: worker process"
               └─628 "nginx: worker process"
  
  Feb 16 07:15:20 ip-172-31-17-47 systemd[1]: Starting nginx.service - A high performance web server and a reverse proxy server...
  Feb 16 07:15:21 ip-172-31-17-47 systemd[1]: Started nginx.service - A high performance web server and a reverse proxy server.
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./server_check.sh 
  Do you want to check service status? (y/n): n
  Skipped.
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./server_check.sh 
  Do you want to check service status? (y/n): p
  Wrong input.. please enter only (y/n).
  
  ```



  
