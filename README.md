# FamilyFashion

It is project about fast delivery fashion items to family members, fast creation fasion family looks

### Установка серверного фреймворка Node.js и менеджера пакетов npm
Установка Vue-3 на macOS 10.15.5 (Catalina)

```
brew install node
node -v
v14.5.0
npm -v
6.14.5
```

### Создание тестового проекта Vue-3 и установка клиентского фрейморка Vue.js

Пробуем новый установщик [Vite](https://www.npmjs.com/package/vite)
```
npm init vite-app hello-vue3
cd hello-vue3
npm install
npm run dev
```

### Установка vue-devtools
Для браузера chrome установлена [бета-версия 6.0.0 beta 1](https://chrome.google.com/webstore/detail/vuejs-devtools/ljjemllljcmogpfapbkkighbhhppjdbg) которая работает с Vue-3

### Установка IDE IntelliJ IDEA (Community Edition)
[IntelliJ IDEA 2020.1.4 (Community Edition)](https://www.jetbrains.com/idea/download/)

### Установка python3.8
Хороший [туториал](https://sourabhbajaj.com/mac-setup/Python/)
```
brew install python
pip3 --version
pip 20.1.1
pip3 install virtualenv
virtualenv --version
virtualenv 20.0.27
```

### Настройка проекта FamilyFashion
1. Создание и активация виртуальной среды проекта virtual env
> [WARNING](https://docs.brew.sh/Homebrew-and-Python): When you brew install formulae that provide Python bindings, you should not be in an active virtual environment.
> Activate the virtualenv after you’ve brewed, or brew in a fresh terminal window. Homebrew will still install Python modules into Homebrew’s site-packages and not into the virtual environment’s site-package.
> Virtualenv has a --system-site-packages switch to allow “global” (i.e. Homebrew’s) site-packages to be accessible from within the virtualenv.

```
cd FamilyFashion
python3.8 -m venv env
source env/bin/activate
```
> NOTE: Ready to stop developing? Use the *deactivate* command to deactivate the virtual environment. To activate it again, navigate to the directory and re-run the source command - *source env/bin/activate*.

2. Установка Flask
```
(env) ➜ 
```
