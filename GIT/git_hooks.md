
## Git hook
- 특정 상황에 특정 스크립트 실행 

#### Installing a Hook

The hooks are all stored in the hooks subdirectory of the Git directory. 
git hook은 Git 디렉토리의 하위 디렉토리로 저장된다.

In most projects, that’s .git/hooks. When you initialize a new repository with git init, Git populates the hooks directory with a bunch of example scripts, 
many of which are useful by themselves; 

but they also document the input values of each script. 
All the examples are written as shell scripts, with some Perl thrown in, but any properly named executable scripts will work fine – you can write them in Ruby or Python or whatever language you are familiar with. If you want to use the bundled hook scripts, you’ll have to rename them; their file names all end with .sample.

To enable a hook script, put a file in the hooks subdirectory of your .git directory 
that is named appropriately (without any extension) and is executable.
From that point forward, it should be called. We’ll cover most of the major hook filenames here.

## Client-Side Hooks

#### pre-commit hook 
pre-commit hook is run first, before you even type in a commit message.

pre-commit은 당신이 커밋 메세지를 타이핑하기 전에 실행된다. 

It’s used to inspect the snapshot that’s about to be committed, to see if you’ve forgotten something, to make sure tests run, or to examine whatever you need to inspect in the code.
그것은 찍는데 사용된다, . 

Exiting non-zero from this hook aborts the commit, although you can bypass it with git commit --no-verify. You can do things like check for code style (run lint or something equivalent), check for trailing whitespace (the default hook does exactly this), or check for appropriate documentation on new methods.

#### prepare-commit-msg 

The prepare-commit-msg hook is run before the commit message editor is fired up but after the default message is created. 

prepare-commit-msg hook은 커밋 메세지 에디터가 fire up 되었으나 기본 메세지가 create 된 후에 사용된다. 

It lets you edit the default message before the commit author sees it. This hook takes a few parameters: the path to the file that holds the commit message so far, the type of commit, and the commit SHA-1 if this is an amended commit. This hook generally isn’t useful for normal commits; rather, it’s good for commits where the default message is auto-generated, such as templated commit messages, merge commits, squashed commits, and amended commits. You may use it in conjunction with a commit template to programmatically insert information.

#### commit-msg 
The commit-msg hook takes one parameter, which again is the path to a temporary file that contains the commit message written by the developer. If this script exits non-zero, Git aborts the commit process, so you can use it to validate your project state or commit message before allowing a commit to go through. In the last section of this chapter, we’ll demonstrate using this hook to check that your commit message is conformant to a required pattern.

After the entire commit process is completed, the post-commit hook runs. It doesn’t take any parameters, but you can easily get the last commit by running git log -1 HEAD. Generally, this script is used for notification or something similar.



## Server-Side Hooks

In addition to the client-side hooks, you can use a couple of important server-side hooks as a system administrator to enforce nearly any kind of policy for your project. 
These scripts run before and after pushes to the server.
The pre hooks can exit non-zero at any time to reject the push as well as print an error message back to the client; 
you can set up a push policy that’s as complex as you wish.

#### post-receive

The post-receive hook runs **after the entire process is completed** and can be used to **update other services or notify users.** 
It takes the same stdin data as the pre-receive hook. 

Examples include emailing a list, notifying a continuous integration server, 
or updating a ticket-tracking system – you can even parse the commit messages to see if any tickets need to be opened, modified, or closed. 
This script can’t stop the push process, but the client doesn’t disconnect until it has completed, so be careful if you try to do anything that may take a long time.


#### pre-receive

The first script to run **when handling a push from a client is pre-receive.**

클라이언트로부터의 push 컨트롤 하는 첫 번째 스크립트. 

It takes a list of references / that are being pushed from stdin; 

표준 입력으로부터 pushed 된 reference들의 리스트를 가지고 있다. 

if it exits non-zero, none of them are accepted. 
You can use this hook to do things / like make sure none of the updated references / are non-fast-forwards, or to do access control for all the refs and files they’re modifying with the push.
당신은, 이 훅을 .


This hook is invoked by git-receive-pack[1] when it reacts to git push and updates reference(s) in its repository. 
이 훅은, git-receive-pack 으로부터 유발된다. 그 repository의 push와 updates 에 대응할 때

Just before starting to update refs on the remote repository, the pre-receive hook is invoked. 

Its exit status determines the success or failure of the update.

This hook executes once for the receive operation. It takes no arguments, but for each ref to be updated it receives on standard input a line of the format:

<old-value> SP <new-value> SP <ref-name> LF
where <old-value> is the old object name stored in the ref, <new-value> is the new object name to be stored in the ref and <ref-name> is the full name of the ref. When creating a new ref, <old-value> is the all-zeroes object name.

If the hook exits with non-zero status, none of the refs will be updated. If the hook exits with zero, updating of individual refs can still be prevented by the update hook.

Both standard output and standard error output are forwarded to git send-pack on the other end, so you can simply echo messages for the user.

The number of push options given on the command line of git push --push-option=... can be read from the environment variable GIT_PUSH_OPTION_COUNT, and the options themselves are found in GIT_PUSH_OPTION_0, GIT_PUSH_OPTION_1,…​If it is negotiated to not use the push options phase, the environment variables will not be set. If the client selects to use push options, but doesn’t transmit any, the count variable will be set to zero, GIT_PUSH_OPTION_COUNT=0.

See the section on "Quarantine Environment" in git-receive-pack[1] for some caveats.

https://www.codeit.kr/community/threads/14279
https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks
