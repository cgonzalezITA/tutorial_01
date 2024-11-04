- Install the ITA containerization tools repository

```
git clone $GIT_CONTAINERIZATIONTOOLS -b dev
```{{exec}}

- Add the execution permissions to the tools script files
```
cd containerizationTools
find tools -name "*.sh" -type f -exec chmod +x {} +
```{{exec}}

- Add alias to invoke the tools script files
```
cat << EOF >> ~/.bash_aliases
alias h='helm'
export _TOOLSFOLDER="/root/containerizationtools" 
alias _fGetFile='$_TOOLSFOLDER/fTools/_fGetFile.sh'
alias gPushAll='$_TOOLSFOLDER/gTools/gPushAll.sh'
alias gFreeze='$_TOOLSFOLDER/gTools/gFreeze.sh'
alias gCommit='$_TOOLSFOLDER/gTools/gCommit.sh'
alias gInfo='$_TOOLSFOLDER/gTools/gInfo.sh'
alias _dGetContainers='$_TOOLSFOLDER/dTools/_dGetContainers.sh'
alias dLogs='$_TOOLSFOLDER/dTools/dLogs.sh'
alias dCompose='$_TOOLSFOLDER/dTools/dCompose.sh'
alias dExec='$_TOOLSFOLDER/dTools/dExec.sh'
alias dGet='$_TOOLSFOLDER/dTools/dGet.sh'
alias dInspect='$_TOOLSFOLDER/dTools/dInspect.sh'
alias dRemove='$_TOOLSFOLDER/dTools/dRemove.sh'
alias kSecret-show='$_TOOLSFOLDER/kTools/kSecret-show.sh'
alias kExec='$_TOOLSFOLDER/kTools/kExec.sh'
alias kGet='$_TOOLSFOLDER/kTools/kGet.sh'
alias kFileCommand='$_TOOLSFOLDER/kTools/kFileCommand.sh'
alias _kGetNamespace='$_TOOLSFOLDER/kTools/_kGetNamespace.sh'
alias kSecret-create4Domain='$_TOOLSFOLDER/kTools/kSecret-create4Domain.sh'
alias kDescribe='$_TOOLSFOLDER/kTools/kDescribe.sh'
alias kLogs='$_TOOLSFOLDER/kTools/kLogs.sh'
alias _kGetArtifact='$_TOOLSFOLDER/kTools/_kGetArtifact.sh'
alias kSecret-createGeneric='$_TOOLSFOLDER/kTools/kSecret-createGeneric.sh'
alias kRemoveRestart='$_TOOLSFOLDER/kTools/kRemoveRestart.sh'
alias hFileCommand='$_TOOLSFOLDER/hTools/hFileCommand.sh'
EOF

. ~/.bash_aliases
```{{exec}}

- Just to play, let's get the pods of the local-path-storage namespace
```
kGet -n path
```{{exec}}

- Just to play, let's view the logs of the pod *local-path-provisioner*
```
kLogs -n path prov
```{{exec}}

- Congrats, now we can start deploying the Fiware Dataspace umbrella charts
