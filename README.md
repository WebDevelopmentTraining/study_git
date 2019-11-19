# study_git
## learning git &amp; github
---

Изучим простые команды git  
`Что такое git?`
---

Регистрация на сайте https://github.com/  
`Что такое github?`
--- 

Создаем репозиторий  
`Что такое репозиторий?`
--- 

Уже есть первый коммит  
![commit](http://i.imgur.com/Ny39tb7.png)
--- 
`Что такое commit?`
Можно нажать fork и увидем что у нас один коммит  
![fork](http://i.imgur.com/uPm4ziU.png)
--- 

Помимо коммитов есть еще бренчи (Branch)   
![Branch](http://i.imgur.com/It2lGTT.png) 

`Что такое branch? `
`Для чего?`
---
Далее склонируем репозиторий
Сначала копируем ссылку   
![копируем ссылку](http://i.imgur.com/baBzTBR.png) 
--- 

Далее открываем терминал (в windows powershell)
переходим в папку вашего проекта
и пишем команду
git clone + ссылка  
![git clone](http://i.imgur.com/qDElrcx.png) 
--- 

Открываем в редакторе кода наш проект

Изменяем readme файл

какие файлы изминились можно проверить командой `git status`
что именно изменилось можно посмотреть командой `git diff`
--- 

чтобы измененный файл добавить в коммит команда `git add README.md`
можно много файлов через пробел перечислить
После этого `git status` отображает имя файла зеленым цветом,то что он добавлен в коммит
--- 

создадим файл `.gitignore`
в нём пропишите  
```
/.gitignore   
/node_modules/
```

эти файлы и папки будут игнорироваться
чтобы закоммитить все фалйы в которых были произведены изменения используется команда  
`git add -A`
--- 

для того чтобы коммит зарегистрировать необходимо его подписать
командой `git commit` возможно откроется редактор мы пишем название и сохраняем
но лучше воспользоваться коммандой `git commit -m "Name commit"`

давайте проссмотрим какие коммиты локальные у нас сейчас есть, делается это командой `git log`

теперь отправляем этот коммит на сервер командой `git push`
Посмотрем в браузере насайте github что изменилось
--- 

чтобы посмотреть список branch (веток) пишем в терминале команду `git branch`  
у нас один branch master
---

чтобы создать новый branch используем команду  `git checkout -b [имя]`
принято вместо пробелов использовать тире

изменим какой-нибудь файл 
посмотрим статус `git status` видим снова измененные файлы
добавим их в коммит `git add -A`
и отрпавим commit `git commit -m "Name commit"`
запушим `git push`  
и он ругается, что текущая ветка не привязана к мастер
![git push branch](http://i.imgur.com/1KOTPDW.png)  
---
и сразу нам подсказывает что делать 
вводим эту команду и push завершается успешно
---

Давайте я вам расскажу про pull request  
`Что такое pull request?`

чтобы сделать pull request
нажимаем на кнопку New pull request или заходим в раздел Pull request и там нажимаем pull request
![pull request](http://i.imgur.com/SuqWmDY.png)

далее у нас есть две вкладки 
первая куда будет выполнен pull вторая откуда
 ---
![pull request](http://i.imgur.com/9kIQxGs.png) 
справа есть дополнительные инструменты 
если у нас команда занимается, можем назначить ревьювера и кто мёрджить пулл реквест чтобы небыло конфликтов если команда большая  
Можно добавить тег, прикрепить к проекту если они есть

---
далее нажимаем pull request и у нас есть актиный pull request

если назначены ревьюверы то им улетае уведомление, посмотрите pull request и примите, прокоментируйте или отклоните его

---

pull request у нас теперь сохранен во вкладке pull request и смерджить его может только ответственный за этот pull request

---

в pull request есть кнопка **Merge pull request** если мы её нажмем то последний commit ветки test-branch смержится с веткой master
если мы сдеалем еще один коммит в эту ветку то он будет последним и именно он смерджится с веткой мастер

---

Измени один файл и сделаем commit и push

у нас добавился еще один commit отлично!

и теперь если мы сделаем Merge то последни коммит будет слит с мастером

--- 

но подождите представим что нужно пофиксить что то в нашем коде, делаем исправления и можем выполнить fixup для коммита
коммит должен описывать какой новый функционал мы добавили, а fixup это если мы исправили какие-то ошибки

чтобы сделать fix app порядок действаий следующий

- фиксим баг
- добавляем в коммит файл или файлы `git add -A`
- берем хеш последнего коммита ![HEX commit](http://i.imgur.com/uNf3jtv.png) 
- добавляем fix up `git commit --fixup [вставляем хеш]`
- `git push`

---

В имени коммита появиться префикс fixup! остальная часть имени будет сохранена  
![fixup](http://i.imgur.com/wxMu9Ev.png)

---

возможностей тут много, ревьювер и вы сами можете выделить кусок кода и комментировать его

зайдем в последний коммит

нажимаем на плюсик, выделяем часть кода и пишем комментрий
![comment](http://i.imgur.com/WrReS8f.png)
этот коммент может быть просто комментом или review когда указывают на ошибки

---

теперь этот комментарий будет в pull request пока мы не внесем изменения в эту часть кода

---

можно предыдущий коммит обновлять  
для этого есть комманда `git commit --amend`
далее имя мы либо оставляем либо меняем

и делаем `git push -f` для того чтобы история переписалась (старый коммит будет заменен новым)

Обычный `git push` выдаст нам ошибку
![error push](http://i.imgur.com/I2D6q26.png)

---

Нажимам Merge pull request и после этого можем ветку удалить если она вам не нужна
![merge pull request](http://i.imgur.com/i98EWOH.png)

---
переходим в ветку мастер `git checkout master`
и скачиваем все изменения которые сделали на сайте `git pull`

--- 
готово на гит хаб и локально у нас одинаковые версии
