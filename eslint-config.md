1. Установите LTS версию `nodejs` (https://nodejs.org/en/)
2. Установите ESlint как глобальный пакет `npm install -g eslint babel-eslint`. На macOS может понадобиться запуск этой программы с правами администратора `sudo npm install -g eslint`. При необходимости введите пароль от своей учетной записи
3. Добавьте файл с названием `.eslintrc.js` в корневую папку проекта с содержимым
```
module.exports = {
    parser: 'babel-eslint',
    env: {
        es6: true,
        node: true,
        jest: true,
        browser: true,
    },
    extends: ['eslint:recommended'],
    parserOptions: {
        ecmaVersion: 2018,
        sourceType: 'module',
    },
    rules: {},
};
``` 
4. Установите плагин для VSCode https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint
5. Перезагрузите VSCode
6. Теперь в редакторе будут подчеркиваться красным синтаксические ошибки в коде. Так же будут подчеркиваться те части кода, которые написаны не лучшим образом и могут привести к ошибкам