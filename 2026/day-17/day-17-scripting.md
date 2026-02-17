# Day 17 Assignment – Shell Scripting: Loops, Arguments & Error Handling

## Task 1: For Loop
1. Create `for_loop.sh` that:
    - Loops through a list of 5 fruits and prints each one
- Script:
  ```
  #!/bin/bash
  for fruit in apple mango banana grapes kiwi
  do
  	echo "$fruit"
  done
  
  ```
- Execution & output:
  ```
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim for_loop.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ chmod +x for_loop.sh 
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./for_loop.sh 
  apple
  mango
  banana
  grapes
  kiwi
  ```

2. Create `count.sh` that:
    - Prints numbers 1 to 10 using a for loop
- Script:
  ```
  #!/bin/bash
  for i in {1..10}
  do
  	echo "$i"
  done
  
  ```
- Execution & output:
  ```
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim count.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ chmod +x count.sh 
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./count.sh 
  1
  2
  3
  4
  5
  6
  7
  8
  9
  10
  ```

---
## Task 2: While Loop
1. Create `countdown.sh` that:
    - Takes a number from the user
    - Counts down to 0 using a while loop
    - Prints "Done!" at the end
- Script:
  ```
  #!/bin/bash
  read -p "Enter a number to start countdown: " num
  count=0
  
  while [ $count -le $num ]
  do
  	echo "$count"
  	((count++))
  done
  echo "Done!"
  
  ```
- Execution & output:
  ```
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim countdown.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ chmod +x countdown.sh 
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./countdown.sh 
  ./countdown.sh: line 3: read: Enter a number to start countdown: : invalid number
  ./countdown.sh: line 6: [: 0: unary operator expected
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim countdown.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./countdown.sh 
  Enter a number to start countdown: 3
  0
  1
  2
  3
  Done!

  ```


---
## Task 3: Command-Line Arguments
1. Create `greet.sh` that:
    - Accepts a name as `$1`
    - Prints `Hello, <name>!`
    - If no argument is passed, prints "Usage: ./greet.sh "
- Script:
  ```
  #!/bin/bash
  if [ "$#" -ne 1 ]; then
	echo "Usage: ./greet.sh <arguments>"
  else
  	echo "Hello, $1"
  fi
  
  ```
- Execution & output:
  ```
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim greet.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ chmod +x greet.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./greet.sh 
  Usage: ./greet.sh <arguments>
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./greet.sh Dhannu
  Hello, Dhannu
  ```

2. Create `args_demo.sh` that:
    - Prints total number of arguments (`$#`)
    - Prints all arguments (`$@`)
    - Prints the script name (`$0`)
- Script:
  ```
  #!/bin/bash
  echo "Total number of arguments you passed: $#"
  echo "This arrguments you passed: $@"
  echo "Script name: $0"
  
  ```
  
- Execution & output:
  ```
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim args_demo.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ chmod +x args_demo.sh 
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./args_demo.sh 
  Total number of arguments you passed: 0
  This arrguments you passed: 
  Script name: ./args_demo.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./args_demo.sh arg1 arg2 arg3 arg4
  Total number of arguments you passed: 4
  This arrguments you passed: arg1 arg2 arg3 arg4
  Script name: ./args_demo.sh
  ```

---
## Task 4: Install Packages via Script
1. Create `install_packages.sh` that:
    - Defines a list of packages: `nginx`, `curl`, `wget`
    - Loops through the list
    - Checks if each package is installed (use `dpkg -s` or `rpm -q`)
    - Installs it if missing, skips if already present
    - Prints status for each package
Run as root: `sudo -i` or `sudo su`
- Script:
  ```
  #!/bin/bash
  for pkg in nginx curl wget
  do
  	if (dpkg -s $pkg &> /dev/null); then
  		echo "installed"
  		if [ "$pkg" == "nginx" ]; then systemctl status $pkg; fi
  	else
  		echo "installing.."
  		apt install $pkg > /dev/null
  		echo "installing successful"
  	fi
  done
  
  ```
- Execution & output:
  ```
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim install_packages.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ chmod +x install_packages.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ sudo ./install_packages.sh 
  installed
  ● nginx.service - A high performance web server and a reverse proxy server
       Loaded: loaded (/usr/lib/systemd/system/nginx.service; enabled; preset: enabled)
       Active: active (running) since Tue 2026-02-17 06:05:44 UTC; 37min ago
         Docs: man:nginx(8)
      Process: 557 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
      Process: 612 ExecStart=/usr/sbin/nginx -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
     Main PID: 627 (nginx)
        Tasks: 3 (limit: 1008)
       Memory: 3.9M (peak: 4.4M)
          CPU: 31ms
       CGroup: /system.slice/nginx.service
               ├─627 "nginx: master process /usr/sbin/nginx -g daemon on; master_process on;"
               ├─628 "nginx: worker process"
               └─629 "nginx: worker process"
  
  Feb 17 06:05:44 ip-172-31-17-47 systemd[1]: Starting nginx.service - A high performance web server and a reverse proxy server...
  Feb 17 06:05:44 ip-172-31-17-47 systemd[1]: Started nginx.service - A high performance web server and a reverse proxy server.
  installed
  installed
  ```
---
## Task 5: Error Handling
1. Create `safe_script.sh` that:
- Uses `set -e` at the top (exit on error)
- Tries to create a directory `/tmp/devops-test`
- Tries to navigate into it
- Creates a file inside
- Uses `||` operator to print an error if any step fails

Example:
```
mkdir /tmp/devops-test || echo "Directory already exists"
```
- Script:
  ```
  #!/bin/bash
  set -e
  mkdir /tmp/devops-test || echo "Directory already exists"
  touch /tmp/devops-test/demo-file.txt
  
  ```
- Execution & output:
  ```
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim safe_script.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ chmod +x safe_script.sh 
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./safe_script.sh

  ----Directory createad----
  
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./safe_script.sh 
  mkdir: cannot create directory ‘/tmp/devops-test’: File exists
  Directory already exists
  ```
2. Modify your `install_packages.sh` to check if the script is being run as root — exit with a message if not.
- Script:
  ```
  #!/bin/bash
  if [ "$EUID" -ne 0 ]; then echo "Run as root"; exit 1; fi
  for pkg in nginx curl wget
  do
  	if (dpkg -s $pkg &> /dev/null); then
  		echo "installed"
  		if [ "$pkg" == "nginx" ]; then systemctl status $pkg; fi
  	else
  		echo "installing.."
  		apt install $pkg > /dev/null
  		echo "installing successful"
  	fi
  done
  
  ```
- Execution & output:
  ```
  ubuntu@ip-172-31-17-47:~/demo-scripts$ vim install_packages.sh
  ubuntu@ip-172-31-17-47:~/demo-scripts$ ./install_packages.sh 
  Run as root
  ubuntu@ip-172-31-17-47:~/demo-scripts$ sudo ./install_packages.sh 
  installed
  ● nginx.service - A high performance web server and a reverse proxy server
       Loaded: loaded (/usr/lib/systemd/system/nginx.service; enabled; preset: enabled)
       Active: active (running) since Tue 2026-02-17 06:05:44 UTC; 37min ago
         Docs: man:nginx(8)
      Process: 557 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
      Process: 612 ExecStart=/usr/sbin/nginx -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
     Main PID: 627 (nginx)
        Tasks: 3 (limit: 1008)
       Memory: 3.9M (peak: 4.4M)
          CPU: 31ms
       CGroup: /system.slice/nginx.service
               ├─627 "nginx: master process /usr/sbin/nginx -g daemon on; master_process on;"
               ├─628 "nginx: worker process"
               └─629 "nginx: worker process"
  
  Feb 17 06:05:44 ip-172-31-17-47 systemd[1]: Starting nginx.service - A high performance web server and a reverse proxy server...
  Feb 17 06:05:44 ip-172-31-17-47 systemd[1]: Started nginx.service - A high performance web server and a reverse proxy server.
  installed
  installed
  ```
