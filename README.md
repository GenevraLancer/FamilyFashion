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

### Создание клиента из тестового проекта Vue-3 и настройка клиентского фрейморка Vue.js

Пробуем новый установщик [Vite](https://www.npmjs.com/package/vite)
```
npx create-vite-app client
cd client
npm i
```
Для запуска клиента
```
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
mkdir server
cd server
python3.8 -m venv env
source env/bin/activate
```
> NOTE: Ready to stop developing? Use the *deactivate* command to deactivate the virtual environment. To activate it again, navigate to the directory and re-run the source command - *source env/bin/activate*.

2. Установка [Flask](https://pypi.org/project/Flask/) и [flask-cors](https://flask-cors.readthedocs.io/en/3.0.4/)
> [В продакшне должны быть разрешены только запросы из домена, на котором размещено фронтенд-приложение](https://tproger.ru/translations/developing-app-with-flask-and-vue-js/)
```
(env) ➜ pip install Flask
(env) ➜ Flask --version
Python 3.8.5
Flask 1.1.2
Werkzeug 1.0.1
(env) ➜ pip install flask-cors
flask-cors-3.0.8
```
3. Добавление .gitignore в каталог server
```
env
*.db
```
### Запуск приложения app.py
1. Создание файла app.py в каталоге server
```
from flask import Flask, jsonify
from flask_cors import CORS

# configuration
DEBUG = True

# instantiate the app
app = Flask(__name__)
app.config.from_object(__name__)

# enable CORS
CORS(app)

# sanity check route
@app.route('/ping', methods=['GET'])
def ping_pong():
    return jsonify('pong!')

if __name__ == '__main__':
    app.run()
```

### Установка axios
Для отправки AJAX запросов между клиентом и сервером установим [axios](https://github.com/axios/axios)
```
cd webapp-client
npm install axios --save
+ axios@0.19.2
```
