# k8sService
## Подготовка
* Установить minikube можно по [ссылке](https://kubernetes.io/ru/docs/tasks/tools/install-minikube/)
```bash
# Запуск
minikube start --vm-driver=virtualbox
# Добавление ingress
minikube addons enable ingress
```

## Выполнение
### Сборка образа

```bash
# build
cd /src
docker build --no-cache -t paveldriver0/learning:1.0 .
# login in docker-hub
docker login
# push images
docker push paveldriver0/learning:1.0
```

### Deploy и просмотр активности
```bash
# применение настроек
minikube kubectl -- apply -f .
# проверка состояния
minikube kubectl -- get all
# проверка состояния ingress
minikube kubectl -- get ing
# получение адреса для доступа к сервису
minikube service simple-service --url
# полученный ip следует внести в /etc/hosts
sudo sh -c "echo '192.168.1.1 arch.homework' >> /etc/hosts"
# проверка доступа через ingres
curl -H 'Host: arch.homework' http://arch.homework
```





