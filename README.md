# flask-mongo-cluster

1. Склонировать проект
2. Перейти в swarm mode - docker swarm init
3. Запустить реплику приложения через stck - docker stack deploy --compose-file docker-app-compose.yml flask-app 
5. При необходимости срегулировать кол-во реплик приложения (по стандарту - 3) - docker service scale flask-app_flask=ЧИСЛО
6. Запустить кластеризованный вариант mongodb (3 реплики - 1-read-write, 2-read) - docker-compose -f docker-mongo-compose.yml up -d (В случае если контейнер mongo-setup постоянно перезапускается, или отрабатывает с ошибкой, убедитесь что git config --global core.autocrlf false - тк shell-скрипты очень чувствительны к маркираторам. В случае если и это не помогло, просто пересоздайте фаил setup.sh с содержимым оригинала и поместите его в mongo/scripts) 
7. Приложение доступно по адресу - http://localhost:8080/


Ссылка docker-приложения: https://hub.docker.com/r/teamcitywasamistake/flask-mongo
