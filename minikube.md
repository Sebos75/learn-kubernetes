## Minikube

Oficjalna strona: https://minikube.sigs.k8s.io/docs/

Narzędzie pozwalające na sprawdzenie możliwości Kubernetesa na komputerze lokalnym. Wymaga wirtualizacji (Hypervisor) lub kontenera (Dockera).

### Instalacja

1. Zainstalować zgodnie z instrukcją: https://minikube.sigs.k8s.io/docs/start
2. Sprawdzić poprawność instalacji: `minikube version`
3. Uruchomić: `minikube start`
   W celu instalacji w VirtualBox: `minikube start --driver=virtualbox`
4. Dostępne będzie narzędzie `kubectl` - menadżer klastra

### Komendy

Uwaga `kubectl` nie jest domyślnie instalowany i należy go poprzedzać komendą `minikube` lub dodać alias: `alias kubectl="minikube kubectl --`

wylistowanie podów:
`kubectl get pods`
`kubectl get po`
wilistowanie z odświeżaniem (wait)
`kubectl get po -w`

Dashboard:
`minikube dashboard`

Lista serwisów:
`kubectl get services`
`kubectl get services nazwa_serwisu`

Uruchomienie serwisu w przeglądarce:

`minikube service nazwa_serwisu`

Przekierowanie portu serwisu:
`kubectl port-forward service/nazwa_sewisu 7080:8080`

Przekierowanie portu poda:
`kubectl port-forward pod/nazwa_poda 2368 2368`

podłaczenie się przez ssh
`minikube ssh`, potem np. `docker ps`

#### Zarządzanie klastrem

pauza/wyłączenie:
`minikube pause`
`minikube unpause`

zatrzymanie klastra
`minikube stop`

zmiana domyślego limitu pamięci
`minikube config set memory 9001`

lista zainstalowanych serwisów
`minikube addons list`

utworzenie drugiego klastra, ze starszym wydaniem
`minikube start -p aged --kubernetes-version=v1.16.1`
usunięcie wszystkich klastów
`minikube delete --all`

#### kubectl

ogólna składnia dostępna jest tutaj: https://kubernetes.io/docs/reference/kubectl/

tworzenie nowego poda:
`kubectl create -f nazwa_definicji.yaml`

informacja o podzie:
`kubectl describe pod nazwa_poda`

usunięcie poda:
`kubectl delete pod nazwa_poda`

podgląd logów:

```
kubectl logs -f nazwa_poda
kubectl logs -f -c nazwa_kontenera nazwa_poda // gdy wiele kontenerów
```

uruchomienie komendy w kontenerze poda:
`kubectl exec -it nazwa_poda -c nazwa_kontenera -- bash`

wylistowanie replikasets:
`kubectl get replicaset`
`kubectl get rs`

skalowanie replikasets:
`kubectl scale rs nazwa_replicaset --replicas=5`

usunięcie obiekltu replicasets:
`kubectl delete rs nazwa_replicasets`
