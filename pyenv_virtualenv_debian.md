
## Instalación de paquetes base

sudo apt install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python3-openssl git

## clonar proyecto (estar con el root)

git clone https://github.com/pyenv/pyenv.git ~/.pyenv

## Variables de entorno

nano ~/.bashrc

export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init --path)"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"

source ~/.bashrc

## Instalar pyenv-virtualenv

git clone https://github.com/pyenv/pyenv-virtualenv.git $(pyenv root)/plugins/pyenv-virtualenv


## Referencias

https://medium.com/@derejehinsermu2/install-pyenv-and-pyenv-virtualenv-linux-debian-7568751e2f6e
https://www.liquidweb.com/kb/how-to-install-pyenv-virtualenv-on-ubuntu-18-04/