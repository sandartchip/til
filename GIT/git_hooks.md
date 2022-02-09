
## Git hook
- 특정 상황에 특정 스크립트 실행 

### 개요 (About Webhooks)
- 웹훅을 사용하면 GitHub.com의 특정 이벤트를 구독하는 GitHub Apps 또는 OAuth Apps와 같은 통합을 구축하거나 설정할 수 있다. 
- 이러한 **이벤트 중 하나가 트리거되면 HTTP POST 페이로드를 웹훅의 구성된 URL로 보낸다. **
- 웹훅을 사용하여 외부 문제 추적기를 업데이트하거나 CI 빌드를 트리거하거나 백업 미러를 업데이트하거나 프로덕션 서버에 배포할 수 있다. 당신은 상상력에 의해 제한될 뿐입니다.

#### Event
- 웹 후크를 구성할 때 UI 또는 API를 사용하여 페이로드를 보낼 이벤트를 선택할 수 있다. 
- 기본적으로 웹훅은 푸시 이벤트에만 가입된다. 구독 이벤트 목록은 언제든지 변경할 수 있다.
- 각 이벤트는 조직 및/또는 리포지토리에서 발생할 수 있는 특정 작업 집합에 해당한다. 
- 예를 들어 이슈 이벤트를 구독하는 경우 이슈를 열거나 닫거나 레이블을 지정하는 등의 작업을 수행할 때마다 세부 페이로드를 받게 된다.

### 이벤트 

### Ping 이벤트 
- 새 웹 후크를 만들면 웹 후크를 올바르게 설정했음을 알리는 간단한 핑 이벤트를 보낸다. 
- 이 이벤트는 저장되지 않으므로, 이벤트 API endpoint을 통해 검색할 수 없다.

ping 이벤트 webhook 페이로드에 대한 자세한 내용은 ping 이벤트를 참조하십시오.


### Webhook 만들기 
- 웹훅을 구축하는 방법과 GitHub에서 웹훅이 청취할 이벤트를 선택하고 웹훅 페이로드를 수신하고 관리할 서버를 설정하는 방법을 배우십시오.

- 웹훅을 만드는 과정은 두 단계로 이루어진다. 
- 먼저 GitHub를 통해 웹훅이 어떻게 동작하기를 원하는지 설정할 필요가 있다: 어떤 이벤트를 청취해야 하는지. 그런 다음 페이로드를 수신하고 관리하도록 서버를 설정합니다.

- 웹 후크 REST API를 사용하면 리포지토리, 조직 및 앱 웹 후크를 관리할 수 있다. 
- 이 API를 사용하여 웹훅에 대한 웹훅 delivery을 나열하거나 외부 앱이나 서비스에 통합될 수 있는 웹훅에 대한 개별 delivery을 가져와 다시 전송할 수 있다. 
- REST API를 사용하여 웹 후크의 구성을 변경할 수도 있다. 예를 들어 페이로드 URL, 컨텐츠 유형, SSL 확인 및 암호를 수정할 수 있다. 자세한 내용은 다음을 참조하십시오.

### 로컬호스트를 인터넷에 노출하기 
- 이 자습서의 목적을 위해 로컬 서버를 사용하여 GitHub에서 메시지를 수신합니다. 
- 따라서 먼저 로컬 개발 환경을 인터넷에 노출해야 합니다. 
- 이를 위해 ngrok을 사용할 것입니다. ngrok은 모든 주요 운영 체제에서 무료로 사용할 수 있습니다. 자세한 내용은 ngrok 다운로드 페이지를 참조하세요.

#### STEP 1
- ngrok을 설치한 후, 4567 포트를 개방한다. 4567 포트는 서버가 메세지를 받을 포트 번호이다. 
- 

----------------------------------------

### Webhook 이벤트 그리고 페이로드 
- 각 웹 후크 이벤트에 대해 이벤트 발생 시기, 페이로드 예제 및 페이로드 개체 매개 변수에 대한 설명을 검토할 수 있다.

- 웹 후크를 구성할 때 UI 또는 API를 사용하여 페이로드를 보낼 이벤트를 선택할 수 있다. 
- 처리할 특정 이벤트만 구독하면 서버에 대한 HTTP 요청 수가 제한된다. 
- 또한 모든 현재 및 미래 이벤트를 구독할 수 있다. 기본적으로 웹훅은 푸시 이벤트에만 가입됩니다. 구독 이벤트 목록은 언제든지 변경할 수 있습니다.

#### Webhook 페이로드 개체 공통 속성
- 각 웹훅 이벤트 페이로드에는 이벤트에 고유한 속성도 포함된다. 
- 개별 이벤트 유형 섹션에서 고유한 속성을 찾을 수 있다

## Key        | Type   | Description 
action	      string	   Most webhook payloads contain an action property that contains the specific activity that triggered the event.
sender	      object	   The user that triggered the event. This property is included in every webhook payload.
repository	  object	   The repository where the event occurred. Webhook payloads contain the repository property when the event occurs from activity in a repository.
organization	object	  Webhook payloads contain the organization object when the webhook is configured for an organization or the event occurs from activity in a repository owned by an organization.
installation	object	The GitHub App installation. Webhook payloads contain the installation property when the event is configured for and sent to a GitHub App. For more information, see "Building GitHub App."

- 웹 후크 이벤트의 고유 속성은 이벤트 API를 사용할 때 페이로드 속성에서 찾을 수 있는 것과 동일합니다. 
- 한 가지 예외는 푸시 이벤트입니다. 푸시 이벤트 webhook 페이로드와 이벤트 API의 페이로드 속성은 서로 다릅니다. 웹훅 페이로드에는 더 자세한 정보가 포함되어 있습니다.

#### Delivery headers 
- 웹 후크의 구성된 URL endpoint으로 전달되는 HTTP POST 페이로드에는 다음과 같은 특수 헤더가 포함됩니다.

#### 헤더, 설명
X-GitHub-Event	     : Name of the event that triggered the delivery.
X-GitHub-Delivery	   : A GUID to identify the delivery.
X-Hub-Signature	     : This header is sent if the webhook is configured with a secret. This is the HMAC hex digest of the request body, and is generated using the SHA-1 hash function and the secret as the HMAC key. X-Hub-Signature is provided for compatibility with existing integrations, and we recommend that you use the more secure X-Hub-Signature-256 instead.
X-Hub-Signature-256	 : This header is sent if the webhook is configured with a secret. This is the HMAC hex digest of the request body, and is generated using the SHA-256 hash function and the secret as the HMAC key.


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

post-receive 훅은 모든 과정들이 완료 되었을 때 그리고 다른 서비스가 업데이트 되었을 때 실행된다. 

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
이 훅은, git-receive-pack 으로부터 유발된다. 그 저장소의 push와 updates 에 반응할 때 . 

Just before starting to update refs on the remote repository, the pre-receive hook is invoked. 
리모트 리파지토리에 update ref를 하기 전에, pre-receive 훅이 발생한다. 


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
