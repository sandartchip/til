
리눅스의 /etc/profile, /etc/bashrc ~/.bash_profile의 ~/.profile  ~/.bashrc 실행순서

OS에서는 /etc/profile, .bash_profile or .profile을 실행하고, 각 파일 내부에서 다른 파일을 실행한다.

 

1. /etc/profile

해당파일 안의 shell script
for i in /etc/profile.d/*.sh ; do

    if [ -r "$i" ]; then

        if [ "${-#*i}" != "$-" ]; then

            . "$i"

        else

            . "$i" >/dev/null 2>&1

        fi

    fi

done

 

2./etc/bashrc
 

3. ~/.bash_profile OR ~/.profile (.bash_profile 이 없으면 .profile을 실행. .bash_profile 이 1순위이고, 우선순위에 따라 1개만 실행된다.)

해당 파일안의 shell script
if [ -f ~/.bashrc ]; then

        . ~/.bashrc

fi

 

4. ~/.bashrc

bashrc는 bash에서 작업할 때마다 수행되는 파일로서, 환경변수의 개념이다.
