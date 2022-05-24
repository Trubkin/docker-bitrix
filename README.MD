окружение для тестовой разработки

для запуска окружения необходимо склонировать репозиторий https://github.com/Trubkin/docker-bitrix.git

cd docker-bitrix/ 

создать переменные окружения: 

cp .env_template .env

запуск: 

docker-compose up -d

проверка работоспособности:

echo "<?php phpinfo();" > ./sites/bitrix/index.php

открыть в браузере http://localhost
