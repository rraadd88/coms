## install travis

    sudo apt install ruby ruby-dev
    sudo gem install travis

## login with github auth

    travis logon --pro

## make a pypi secure password

    cd repository
    travis encrypt {pypi password without special chars}

## Pro tip
    1. Never change github and pypi pws during buiding.
