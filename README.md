# Домашнее задание к занятию 2 «Работа с Playbook» - Яковлев Артем

## Подготовка к выполнению

1. * Необязательно. Изучите, что такое [ClickHouse](https://www.youtube.com/watch?v=fjTNS2zkeBs) и [Vector](https://www.youtube.com/watch?v=CgEhyffisLY).
2. Создайте свой публичный репозиторий на GitHub с произвольным именем или используйте старый.
3. Скачайте [Playbook](./playbook/) из репозитория с домашним заданием и перенесите его в свой репозиторий.
4. Подготовьте хосты в соответствии с группами из предподготовленного playbook.

## Основная часть

1. Подготовьте свой inventory-файл `prod.yml`.
2. Допишите playbook: нужно сделать ещё один play, который устанавливает и настраивает [vector](https://vector.dev). Конфигурация vector должна деплоиться через template файл jinja2. От вас не требуется использовать все возможности шаблонизатора, просто вставьте стандартный конфиг в template файл. Информация по шаблонам по [ссылке](https://www.dmosk.ru/instruktions.php?object=ansible-nginx-install). не забудьте сделать handler на перезапуск vector в случае изменения конфигурации!
3. При создании tasks рекомендую использовать модули: `get_url`, `template`, `unarchive`, `file`.
4. Tasks должны: скачать дистрибутив нужной версии, выполнить распаковку в выбранную директорию, установить vector.
5. Запустите `ansible-lint site.yml` и исправьте ошибки, если они есть.
6. Попробуйте запустить playbook на этом окружении с флагом `--check`.
7. Запустите playbook на `prod.yml` окружении с флагом `--diff`. Убедитесь, что изменения на системе произведены.
8. Повторно запустите playbook с флагом `--diff` и убедитесь, что playbook идемпотентен.
9. Подготовьте README.md-файл по своему playbook. В нём должно быть описано: что делает playbook, какие у него есть параметры и теги. Пример качественной документации ansible playbook по [ссылке](https://github.com/opensearch-project/ansible-playbook). Так же приложите скриншоты выполнения заданий №5-8
10. Готовый playbook выложите в свой репозиторий, поставьте тег `08-ansible-02-playbook` на фиксирующий коммит, в ответ предоставьте ссылку на него.

---

## Ответ:

1. Готовый playbook находится здесь: [Playbook](https://github.com/temagraf/08-ansible-02-playbook/tree/master/playbook)

2. Скрин выполнения `ansible-lint site.yml` (ошибки были исправлены ранее):
![Screen1](https://github.com/temagraf/08-ansible-02-playbook/blob/main/img/2024-12-18_20-27-18.png)

3. Скрин запуска playbook с флагом `--check` - playbook завершает работу с ошибкой по причине отсутствия файла потому, что в этом режиме никаких изменений на окружении не производится:

![Screen2](https://github.com/temagraf/08-ansible-02-playbook/blob/main/img/2024-12-18_20-33-43.png)

4. Скрин запуска playbook на окружении, развернутого из Docker образов Centos7 с флагом `--diff`, изменения на системе произведены:

![Screen3](https://github.com/temagraf/08-ansible-02-playbook/blob/main/img/2024-12-19_00-46-08.png)

5. Скрин повторного запуска playbook с флагом `--diff` - playbook идемпотентен:

![Screen4](https://github.com/temagraf/08-ansible-02-playbook/blob/main/img/2024-12-19_00-47-42.png)


### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---
