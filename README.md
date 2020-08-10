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

### Настройка сервера
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
### Создание клиента и настройка клиентского фрейморка Vue.js

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
Смотрим, что отображается страница
> Local:    http://localhost:3000/
Выключаем CTRL+C

### Установка axios и vue-router
Для отправки AJAX запросов между клиентом и сервером установим [axios](https://github.com/axios/axios)
Для написания JS установим [saas]
```
cd client
npm install axios --save
+ axios@0.19.2
```
--save — указывает что добавляется зависимость которая войдет в финальный продукт. Пакет будет установлен локально, в папку node_modules, и будет добавлена запись в поле dependencies в package.json.
--save-dev (или -D) — указывает что добавляется зависимость разработки. Пакет будет установлен локально, в папку node_modules, и будет добавлена запись в поле devDependencies в package.json
Фрагмент package.json
```
"dependencies": {
    "axios": "^0.19.2",
    "vue": "^3.0.0-rc.1"
  },
  "devDependencies": {
    "@vue/compiler-sfc": "^3.0.0-rc.1",
    "vite": "^1.0.0-rc.1"
  }
```

Не боимся и ставим бета-версию [vue-router](https://github.com/vuejs/vue-router-next)
```
npm install vue-router@4.0.0-beta.3
```

### Создание и подключение компонента Ping.vue
В каталоге components создаем компонент Ping.vue
```
cd client/src/components
```
Заполняем компонент Ping.vue
```
<template>
    <div>
        <p>{{ hello }}</p>
    </div>
</template>

<script>
export default {
  name: 'Ping',
  data() {
    return {
      hello: 'Hello everyone!',
    };
  },
};
</script>
```

### Изменяем App.vue
Подключаем в App.vue новый компонент Ping.vue аналогично подключнному компоненту HelloWorld.vue
```
<template>
  <Ping/>
  <p/>
  <HelloWorld msg="1"/>
</template>

<script>
import Ping from './components/Ping.vue'
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    Ping,
    HelloWorld
  }
}
</script>
```

### Настраиваем vue-router
Создаем каталог ```client/src/router```
Создаем файл index.js и вставляем код
```
import { createRouter, createWebHistory} from 'vue-router'
import Home from '../views/Home.vue'
import Contact from '../views/Contact.vue'

const routerHistory = createWebHistory()

const router = createRouter({
    history: routerHistory,
    routes : [
    {
        path:'/',
        component: Home
    },
    {
        path:'/contact',
        component: Contact
    }
    ]
})

export default router
```

Вносим изменения в main.js
```
import { createApp } from 'vue'
import App from './App.vue'
import './index.css'
import router from './router'

const app = createApp(App)
app.use(router)
app.mount('#app')
```

Создаем каталог ```client/src/views``` и в нем два файла Home.vue и Contact.vue
saas еще криво работает, поэтому не используем теги стиля
```
<template>
    <h3>DFGGGG</h3>
</template>

<script />
```

Вносим изменения в App.vue
```
<router-link to="/">Home</router-link>
  <router-link to="/contact">Contact</router-link>
  <router-view/>
```

### Установка saas для работы с css
Устанавливаем загрузчик и saas, так как без загрузчика saas ставится странной версии 1.0.0, удаляем пока загрузчик
Делаем по мануалу https://www.youtube.com/watch?v=VPOVOlVQwB8 и проверяем что saas работает
```
npm install -D sass-loader sass
+ sass-loader@9.0.2
+ sass@1.26.10
npm uninstall saas-loader
```
Как [подсказка](https://medium.com/@serg.gavel/%D0%B8%D1%81%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-sass-scss-%D0%B2-%D1%84%D1%80%D0%B5%D0%B9%D0%BC%D0%B2%D0%BE%D1%80%D0%BA%D0%B5-vue-js-10542b3a1b09) по работе с css 
Ресурсы спиннера из мануала: https://loading.io/css

Решение первой проблемы - выровнять спиннер по центру экрана, не внося изменения в код самого спиннера. Пример кода:
```
<template>
    <div class="canvas-outer">
        <div class="canvas-inner">
        <div class="lds-hourglass"></div>
    </div></div>
</template>

<style lang="scss">
.canvas-outer{
    background-color:rgb(0,0,0,0.2);
    width: 100vw;
    height: 100vh;
    position: fixed;
    top: 50%;
    left: 50%;
    margin-right: -50%;
    transform: translate(-50%, -50%)
}
.canvas-inner{
    position:relative;
    top: 50%;
    left: 50%;
    margin-right: -50%;
    transform: translate(-50%, -50%)
}
.lds-hourglass {...}
```
### Взаимодействие фронтенда vue и бэкенда flask 
В компоненте Ping.vue изенить раздел script

```
<script>
import axios from 'axios';

export default {
  name: 'Ping',
  data() {
    return {
      msg: '',
    };
  },
  methods: {
    getMessage() {
      const path = 'http://localhost:5000/ping';
      axios.get(path)
        .then((res) => {
          this.msg = res.data;
        })
        .catch((error) => {
          // eslint-выключение следующей строки
          console.error(error);
        });
    },
  },
  created() {
    this.getMessage();
  },
};
</script>
```

### Еще больше красоты с бутстрап
bootstrap@4.5.2 еще не адаптирован для работы с фронтендом vue3, пробуем с vue-material@1.0.0-beta-14
```
npm install vue-material --save 
+ vue-material@1.0.0-beta-14
```


