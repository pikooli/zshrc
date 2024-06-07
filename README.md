```
export ZSH="$HOME/.oh-my-zsh"
export JAVA_HOME="/Library/Java/JavaVirtualMachines/zulu-11.jdk/Contents/Home"
export ANDROID_HOME=$HOME/Library/Android/sdk
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/platform-tools
export PATH=$PATH:/Users/pascalzhang/.pyenv/versions/3.9.10c/lib/python3.9/site-packages
export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init --path)"

plugins=(git)

source $ZSH/oh-my-zsh.sh

# ========== git Alias ==========
alias git='LANG=en_US git'
alias gbd="git branch -D"
alias gp="git push"
alias gpl="git pull"
alias gs="git stash"
alias gsp="git stash pop"
alias grc="git rebase --continue"
alias gcc="git cherry-pick --continue"
alias gi="git remote -v"
alias gch="git cherry-pick"

alias drestart="docker-compose exec app npx pm2 restart all"

# ========== Mobile Alias ==========
alias mobileYarn="yarn; cd ios; pod install; cd .."
alias rios="npx react-native run-ios"
alias randroid="npx react-native run-android"


export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion


# =============== AUTO load nvm ==============
# NVM auto-switching based on .nvmrc file
# place this after nvm initialization!
autoload -U add-zsh-hook
load-nvmrc() {
  local node_version="$(nvm version)"
  local nvmrc_path="$(nvm_find_nvmrc)"

  if [ -n "$nvmrc_path" ]; then
    local nvmrc_node_version=$(nvm version "$(cat "${nvmrc_path}")")

    if [ "$nvmrc_node_version" = "N/A" ]; then
      nvm install
    elif [ "$nvmrc_node_version" != "$node_version" ]; then
      nvm use
    fi
  elif [ "$node_version" != "$(nvm version default)" ]; then
    echo "Reverting to nvm default version"
    nvm use default
  fi
}
add-zsh-hook chpwd load-nvmrc
load-nvmrc



# >>> conda initialize >>>
# !! Contents within this block are managed by 'conda init' !!
__conda_setup="$('/Users/pascalzhang/anaconda3/bin/conda' 'shell.zsh' 'hook' 2> /dev/null)"
if [ $? -eq 0 ]; then
    eval "$__conda_setup"
else
    if [ -f "/Users/pascalzhang/anaconda3/etc/profile.d/conda.sh" ]; then
        . "/Users/pascalzhang/anaconda3/etc/profile.d/conda.sh"
    else
        export PATH="/Users/pascalzhang/anaconda3/bin:$PATH"
    fi
fi
unset __conda_setup
```
