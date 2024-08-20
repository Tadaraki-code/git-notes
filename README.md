# Работа в терминале.

Для начала разберёмся как работать в терминале.
Для того что бы перемещаться по директориями используй команду **Cd _имя директории_** 
*Например:* "Cd Photo" такая команда переместит тебя в директорию Photo.
Чтобы вернуться в домашнюю директорию используй **~** в этом символе по умолчанию храниться ссылка на домашнюю директорию.

Чтобы узнать в где ты находишься используй команду **pwd**, в командной строке появиться путь к директории в которой ты находишься. 

Чтобы посмотреть что есть в директории используй команду **ls**, эта команда покажет тебе список всех файлов директории. Если добавить флаг **ls -a** то можно будет увидеть скрытые файлы.

Для того чтобы создать файл используй команду **touch "Имя файла"**.

Для того чтобы создать директорию используй команду **mkdir "Имя директорию"**.

Чтобы удалить файл используй команду **rm "Имя файла"**, чтобы удалить директорию используй команду **rmdir "название директории"**, если в директории есть файлы и ты точно хочешь удалить их вместе с файлами используй комаду **rm -r "название директории"** 
Помни удаление таким способом необратимо!

Используй команду **cat "Имя файла** чтобы прочитать содержимое файла.

# Работа с Git.

Чтобы начать использовать Git для начала нужно инициализировать репозиторий, для этого используй команду **git init** находясь в том репозитории который ты хочешь инициализировать.
После выполнения этой команды в репозитории появиться файл .git, проверить это можно с помощью команды **ls -a**.
Если ты хочешь "разгитить" репозиторий просто удали .git, сделать это можно так **rm .git**.
Репозиторий готов к использованию. Теперь создавай,изменяй и удаляй файлы которые нужно.

После того как ты сделал всё что хотел с файлами, их нужно подготовить к коммиту, для этого используй команду **git add "Имя файла"** или ты можешь подготовить к коммиту сразу все файлы командой
**git add --all**

Для того чтобы убедиться что всё идёт хорошо используй команду **git status**, если имена файлов зелёные ты всё делаешь правильно!

Пора делать коммит! Для того чтобы это сделать используй команду **git commit -ь 'комментарий'**
Если всё прошло хорошо,то поздравляю, коммит удался-все изменения сохранены.

**Запомни последовательность: Добавляешь изменения --> git add "Имя файла" --> git commit**

Чтобы посмотреть все сделанные коммиты используй команду **Git log**.

# Работа с GitHub.

До этого мы работали только с локальным репозиторием, который храниться на твоём компьютере. Теперь пора работать с GitHub.

Для начала тебе понадобится аккаунт на GitHub. После того как ты завёл аккаунт, нужно сгенерировать  SSH-key. 
Для этого используй команду **ssh-keygen -t rsa -b 4096 -c "Почта которую ты использовал при регистрации на GitHub"**

Если всё прошло удачно, то теперь у тебя есть приватный и публичный ключи, сейчас нам понадобится публичный код, переходи в в директорию .ssh и прочитай c помощью **cat** файл с расширений .pub.
То что тебе выведет в консоль является твоим публичным кодом, его необходимо добавить на GitHub, в настройках найди раздел SHH and GPG keys, там в разделе SHH добавь свой публичный код.

Теперь тебе нужно связать свой компьютер и GitHub, для этого используй команду **ssh -T git@github.com** и пиши **yes**.

Если всё хорошо то ты увидишь следующий текст **You've successfully authenticated, but GitHub does not provide shell access.**. Если ты увидел это значит всё хорошо.

Теперь создай удалённый репозиторий на GitHub, для этого перейди в свой профиль на GitHub,зайди в раздел с твоими репозиториями и создай новый репозиторий. 

После того как ты создал удалённый репозиторий тебе нужно его связать его с твоим локальным репозиторием, для этого используй команду **git remote add origin SSH-ссылка на созданный тобой репозиторий**
Для того чтобы проверить всё ли прошло хорошо используй команду **git remote -v** находясь в локальном репозитории.

Остался последний шаг, запушить файлы, в первый раз надо будет использовать команду **git push -u origin main или master**, дальше можно будет писать только **git push**

Ещё есть команда **git clone**, но об этом в другой раз)

# Хеш
У каждого коммита есть свой хеш-код который содержит в себе данные о том: когда был сделал коммит, содержание файлов репозитория на момент коммита и ссылку на предидущий или родительский коммит.
У хеша есть несколько свойст.
1. Если получать хеш для одного и тогоже набора данных то он всегда будет одинаков.
2. Если в данные были добавлены мельчайшие изменения то хеш измениться.
Все хеши и таблицы совпадений(хеш > информация о коммите) git сохроняет в служебном файле, эти файлы находяться в скрытой папке .git в репозитории.
Специальная команда для вывода сокрощёной версии лога коммитов.
