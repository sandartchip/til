
## Git hook
- 특정 상황에 특정 스크립트 실행 


#### post-receive

The post-receive hook runs **after the entire process is completed** and can be used to update other services or notify users. 
It takes the same stdin data as the pre-receive hook. 
Examples include emailing a list, notifying a continuous integration server, 
or updating a ticket-tracking system – you can even parse the commit messages to see if any tickets need to be opened, modified, or closed. 
This script can’t stop the push process, but the client doesn’t disconnect until it has completed, so be careful if you try to do anything that may take a long time.


#### pre-receive

The first script to run **when handling a push from a client is pre-receive.**

It takes a list of references that are being pushed from stdin; if it exits non-zero, none of them are accepted. 
You can use this hook to do things like make sure none of the updated references are non-fast-forwards, or to do access control for all the refs and files they’re modifying with the push.


This hook is invoked by git-receive-pack[1] when it reacts to git push and updates reference(s) in its repository. 
Just before starting to update refs on the remote repository, the pre-receive hook is invoked. Its exit status determines the success or failure of the update.

This hook executes once for the receive operation. It takes no arguments, but for each ref to be updated it receives on standard input a line of the format:

<old-value> SP <new-value> SP <ref-name> LF
where <old-value> is the old object name stored in the ref, <new-value> is the new object name to be stored in the ref and <ref-name> is the full name of the ref. When creating a new ref, <old-value> is the all-zeroes object name.

If the hook exits with non-zero status, none of the refs will be updated. If the hook exits with zero, updating of individual refs can still be prevented by the update hook.

Both standard output and standard error output are forwarded to git send-pack on the other end, so you can simply echo messages for the user.

The number of push options given on the command line of git push --push-option=... can be read from the environment variable GIT_PUSH_OPTION_COUNT, and the options themselves are found in GIT_PUSH_OPTION_0, GIT_PUSH_OPTION_1,…​If it is negotiated to not use the push options phase, the environment variables will not be set. If the client selects to use push options, but doesn’t transmit any, the count variable will be set to zero, GIT_PUSH_OPTION_COUNT=0.

See the section on "Quarantine Environment" in git-receive-pack[1] for some caveats.

https://www.codeit.kr/community/threads/14279
https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks
