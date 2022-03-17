> 遇到的问题

配置了多个sshkey 以后，每次启动都要先启动ssh-agent

> 解决方法：

可以在用户 (~)的目录下去创建  .profile 使启动git bash的时候自动启动ssh-agent



1. 进入用户目录  shift + F10  ==> s 启动git bash
2. pwd 确认当前目录
3.  `touch ~/.profile`    .开头的文件没法直接创建
4. 添加以下这段代码
```
env=~/.ssh/agent.env
agent_load_env () { test -f "$env" && . "$env" >| /dev/null ; }
agent_start () {
    (umask 077; ssh-agent >| "$env")
    . "$env" >| /dev/null ; }
agent_load_env
# agent_run_state: 0=agent running w/ key; 1=agent w/o key; 2= agent not running
agent_run_state=$(ssh-add -l >| /dev/null 2>&1; echo $?)
if [ ! "$SSH_AUTH_SOCK" ] || [ $agent_run_state = 2 ]; then
    agent_start
    ssh-add
elif [ "$SSH_AUTH_SOCK" ] && [ $agent_run_state = 1 ]; then
    ssh-add
fi
unset env
```

保存以后重启git bash