##  远程访问设置

打开ssh:

`.shh`

修改默认远程连接:

```
eval "$(ssh-agent -s)"
(工作账户)ssh-add id_rsa_dgxlsir
测试：ssh -T git@github-dgxlsir
(萝莉账户)ssh-add id_rsa_evil
测试：ssh -T git@github-evilwithlovely

```

sublime设置：

```
alias sublime='open -a "Sublime Text"'
```

