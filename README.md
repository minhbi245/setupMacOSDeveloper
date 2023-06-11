# setupMacOSDeveloper
1. Machine
1.1. System Preferences
Trackpad > Tap to click
Keyboard > Key Repeat > Fast (all the way to the right)
Keyboard > Delay Until Repeat > Short (all the way to the right)
1.2. Text Editor
Format > Plain text
Options > uncheck all
1.3. Sample Workspace
~/dev/docs – contains general documents
~/dev/repo – contains all repositories
~/dev/projects – contains project’s resource, documents, etc…
~/dev/ios, ~/dev/android, ~/dev/ruby…

2. Command line tools
* First of all run that command:

defaults write com.apple.finder AppleShowAllFiles YES; killall Finder

sudo chown -R $(whoami):admin '/usr/local' (for all macOS) | sudo chown -R $(whoami) /usr/local/* (For the new macOS)

2.1. Xcode Command Line Tools
install
xcode-select --install

2.2. Oh My Zsh
install
`sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`

config shell profile
laterly, do not modify ~/.zshrc, only modify ~/.bashrc

touch ~/.bashrc
echo 'source ~/.bashrc' >> ~/.zshrc

2.3. Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

- Grant permission
sudo chown -R $USER /Users/khanhnvm/Library/Caches/Homebrew

2.4. Version Manager
2.4.1 Ruy
brew install rbenv
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
source ~/.bashrc
rbenv install 3.0.0
rbenv global 2.3.1        # ~ default
rbenv local 2.4.0-dev     # specific for current directory
rbenv shell 2.2.5        # after this, shell will run with ruby 2.2.5

2.4.2 PHP Environment
curl -L -O https://github.com/phpbrew/phpbrew/raw/master/phpbrew
chmod +x phpbrew
./phpbrew init        # this will create ~/.phpbrew dir
mv phpbrew ~/.phpbrew/
echo 'export PATH=~/.phpbrew:$PATH' >> ~/.bashrc
echo '[[ -s ~/.phpbrew/bashrc ]] && source ~/.phpbrew/bashrc' >> ~/.bashrc
source ~/.bashrc
phpbrew install 7.0

2.4.3 NodeJS, NVM
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
echo 'export NVM_DIR="$HOME/.nvm"' >> ~/.bashrc
echo 'source "$(brew --prefix nvm)/nvm.sh"' >> ~/.bashrc
echo '[[ -r $NVM_DIR/bash_completion ]] && . $NVM_DIR/bash_completion' >> ~/.bashrc
source ~/.bashrc
nvm install 7.2.0
nvm use 7.2.0                # select node for this shell
nvm alias default 7.2            # select node for any shell
brew install node            # /usr/local/node

2.4.4. Python – pyenv (~rbenv)
brew install pyenv
echo 'eval "$(pyenv init -)"' >> ~/.bashrc
source ~/.bashrc
pyenv install 2.7.12
pyenv global 2.7.12        # ~ default
pyenv local 2.7.12         # specific for current directory
pyenv shell 2.7.10        # after this, shell will run with python 2.7.10
