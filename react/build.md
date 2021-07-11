## Сборка

В разработке хорошей практикой является хранить в репозитории только исходный код. Сборка и деплой происходит на специальных серверах в процессе CI/CD (Continuous Integration / Continuous Delivery)

По этому папки, которые генерируются в процессе сборки обычно добавляются в <code>.gitignore</code>. Пример таких папок: <code>node_modules</code>, <code>build</code>, <code>dist</code> и т.д.

В нашем случае, чтобы увидеть сайт в работе на GitHub Pages, все же нужно залить на GitHub результат сборки:

<ul>
  <li>Папка с собранными файлами должна называться <code>review_build</code> и лежать в корне проекта (задачи)</li>
  <li>Ее нужно сгенерировать в процессе сборки с помощью <code>webpack</code> (свойство <code>output.path</code> в настройках установить, как <code>path.resolve(__dirname, 'review_build')</code>)</li>
  <li><code>review_build</code> добавлять в <code>.gitignore</code> не нужно</li>
  <li>Если ты используешь <code>create-react-app</code>, то можно скопировать (переименовать) папку вручную</li>
</ul>
