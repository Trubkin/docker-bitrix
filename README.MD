<b>ОКРУЖЕНИЕ ДЛЯ ТЕСТОВОЙ РАЗРАБОТКИ</b>

для запуска окружения необходимо склонировать репозиторий: 

git clone https://github.com/Trubkin/docker-bitrix.git

cd docker-bitrix/ 

создать переменные окружения: 

cp .env_template .env

запуск: 

docker-compose up -d

проверка работоспособности:

echo "<?php phpinfo();" > ./sites/bitrix/index.php

открыть в браузере http://localhost

или: 

wget https://www.1c-bitrix.ru/download/scripts/bitrixsetup.php

и запускаем:

http://localhost/bitrixsetup.php

завершение работы:

docker-compose down --volumes

docker swarm:

docker swarm init

docker stack deploy -c .\stack.yml bitrix

Для отслеживания состояния контейнеров можно поднять Portainer:

docker volume create portainer_data

docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:2.9.3