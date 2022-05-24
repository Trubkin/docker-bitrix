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
