# l4-da

## Requirements
- Docker

## Build instructions
- Clone this directory
- Run the following command:
   ``` bash
   docker build -t l4-da .  
    ``` 
   This installs a local image of l4-da within your docker.
   
## Running the docker instance
    ``` sh
    docker run -d -p 80:80 -p 443:443 --stop-timeout 600 l4-da 
    ```
- When it succeeds, you should see a hash at the bottom of STDOUT like this
- Open your web browser of choice, and connect to localhost
- default login details are "admin@admin.com" & "password"
- after login you will be prompted to change your password

## Testing your sCASP installation
- Go to the playground within the docassemble interface
- start a new interview file, naming it with any name you'd like
- copy and paste the following into the space provided:
  ```yaml
  mandatory : True
  question: |
    Do we have sCASP?
  subquestion: |
    ${ results }
  buttons:
    - Exit : exit
  ---
  code: |
    import subprocess
    results = subprocess.run(["/var/www/.ciao/build/bin/scasp"], capture_output=True).stdout.decode('utf-8')
  ```
- Save and run the interview
- you should see an output like the following:

``` sh
ERROR: No imput file specified!

Usage: scasp [options] InputFile(s)

s(CASP) computes stable models of predicate normal logic programs with contraints using a top-down evaluation algorihtm. Command-line switches are case-sensitive!

... so on & so forth
```



## ORIGINAL DOCASSEMBLE README BELOW

See the [docassemble web site] for a description of **docassemble**
and installation instructions.

To get help with using **docassemble**, join the [docassemble Slack
group].

[docassemble web site]: https://docassemble.org
[docassemble Slack group]: https://docassemble.org/docs/support.html
