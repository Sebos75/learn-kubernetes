# learn-kubernetes
Informacje dotyczące Kubernetes

time: ||
last lession: https://kubernetespopolsku.c.cloudowski.com/sezon-1/s01e01

Kubernetes - charakterystyka:
- balansowanie ruchu,
- samoczynne naprawianie (restart kontenerów),
- zarządzanie informacjami poufnymi i konfiguracją (hasła tokeny).


Dokumentacja: https://kubernetes.io
Kurs "Kubernetes po polsku: https://kubernetespopolsku.c.cloudowski.com
Samouczyki po polsku na stronie Kubernetes: https://kubernetes.io/pl/docs/tutorials 

## Informacje ogólne

Kubernetes to przenośna, rozszerzalna platforma oprogramowania open-source służąca do zarządzania zadaniami i serwisami uruchamianymi w kontenerach, która umożliwia deklaratywną konfigurację i automatyzację.

**Minikube** - narzędzie pozwalające na uruchomienie małego klastra na własnym komputerze, więcej: [Minikube](minikube.md)
### Definicje

**Klaster** - to zestaw maszyn roboczych, nazwyanych węzłami, na których uruchamianę są aplikacje w kontenerach. Każdy klaster musi posiadać jeden węzeł.
**Pod** na węzłach umieszczane są pody, pod do zestaw kontentów klastra.

Warstwa sterowania (The container orchestration layer) zarządza węzłąmi roboczymi i podami należącymi do klastra. W Środowisku produkcyjnym warstwa sterowania rozłożona jest zazwyczaj na kilka maszyn, a klaster uruchomiony jest na wielu węzłach (większa niezawodność i odporność na awarie).

**K8s** - skrót od Kubernetes, powstał przez zastąpienie 8 wewnętrznych liter nazwy: k********s. Sama nazwa pochodzi z greki i oznacza sternika. Google otworzyło ten porjekt w 2014 roku.
W odróżnieniu od maszyn wirtualnych kontenery nie mają osobnego systemu operacyjnego oraz nie wymagają Hepervisor'a.

#### Częsci składowe warstwy sterowania
**kube-apiserver** - udostępnia API, służy jako front-end warstwy sterowania (api jest skalowane horyzontalnie)

**etcd** - magazyn typu klucz-wartość (kay/value store), zapewniający spójność i wysoką dostpność, używany do przechowywania wszystkich danych o klastrze Kubernetes.

**kube-scheduler** - śledzi tworzenie nowych podów i przypisuje im węzły, na których powinny być uruchomione. Istnieje wiele kontrolerow, np.:
- node controller, job controller, endpoints controller itd.


**cloud-controller-mananger** - zarządza usługami realizowanymi po stornie chmur obliczeniowych. Nie jest uruchamiany w środowisku lokalnym.

**kube-controller-manger** - odpowiedzialny za uruchamianie kontrolerów 

#### Składniki węzłow
Składniki węzłow uruchamiane są na każdym węźle, utrzymują pody w działaniu i ustawiają środowisko uruchomieniowe Kubernetes.
**kubelet** - działa na każdym węle klastra, odpowiada za uruchamianie kontenerów w ramach poda.

**kube-proxy** - utrzymuje reguły sieciowe na węźle, umożliwia komunikowanie się wewnątrza i na zewnątrz klastra.


#### Dodatki (Addons)
Opcjonalne elemnty dostępne dla klastra, podstawowe to:
- DNS,
- Interfejs użytkownika (Dashboard)
- Monitorowanie zasobów w kontenerach (Container Resource Monitoring) zapisuje metryki w bazie danych i udostępnia interfejs do przeglądania tych danych.




### Komendy




