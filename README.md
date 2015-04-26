# My mac provisioning

## Thanks

* http://t-wada.hatenablog.jp/entry/mac-provisioning-by-ansible
* http://mawatari.jp/archives/mac-provisioning-by-homebrew-and-ansible

## First time

```bash
# Install Xcode from AppStore
sudo xcodebuild -license
xcode-select —install
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew update
brew install ansible

mkdir ~/.mac-provisioning && cd $_
curl -O https://raw.githubusercontent.com/akiyoshi83/.mac-provisioning/master/hosts
curl -O https://raw.githubusercontent.com/akiyoshi83/.mac-provisioning/master/localhost.yml
HOMEBREW_CASK_OPTS="--appdir=/Applications"; ansible-playbook -i hosts -vv localhost.yml
```

```bash
cd ~
mv .mac-provisioning .mac-provisioning.back
git clone https://github.com/akiyoshi83/.mac-provisioning.git
mv .mac-provisioning.back/*_info .mac-provisioning/
rm -Rf .mac-provisioning.back
```

# Next time

```bash
# some edit
vim localhost.yml
# execute
HOMEBREW_CASK_OPTS="--appdir=/Applications"; ansible-playbook -i hosts -vv localhost.yml
```
