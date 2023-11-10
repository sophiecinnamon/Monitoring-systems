## Среда
Для начала необходимо подготовить среду, в которой можно будет проводить дальнейшие эксперименты. 
(https://github.com/projectdiscovery/nuclei - сканер уязвимостей с простым синтаксисом настройки на основе YAML).
Создание виртуальной машины на базе ОС Linux, желательно 22.04, nginx сервер в качестве объекта и nuclei сканер в качестве субъекта
Пользователю необходимо выдать sudo права.
---

Для установки nginx сервера необходимо выполнить следующие команды:
```bash
sudo apt update && sudo apt upgrade -y # полное обновление ПО
sudo apt install nginx # установка nginx
systemctl status nginx # проверка nginx, статус должен быть active
```
После установки nginx станет доступен через браузер.

Для установки nuclei сканера необходимо выполнить следующие действия:
```bash
# для nuclei нужен golang версии 1.20
wget https://go.dev/dl/go1.20.7.linux-amd64.tar.gz # скачать версию go, оптимальную для nuclei
sudo tar -C /usr/local -xzf go1.20.7.linux-amd64.tar.gz # распаковать
echo "export PATH=$PATH:/usr/local/go/bin:~/go/bin" >> ~/.bashrc # сохранить путь к go для всех последующих сессий
source ~/.bashrc # для этой сессии
go version # проверить что go установился

# непосредственно установка nuclei
go install -v github.com/projectdiscovery/nuclei/v2/cmd/nuclei@latest
nuclei -h # проверить что nuclei установился
```
---
Наша среда - это защищаемый ресурс (nginx сервер) и атакующий субъект (nuclei сканер) находящиеся на одном хосте.

##
