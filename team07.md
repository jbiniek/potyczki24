# Witamy w finale!
Potyczki Młodych Adminów 2024

## Wstęp
Tegoroczne zadania są pomyślane jako dzień z pracy administratora w korporacji. Jest trochę codziennych, podstawowych czynności, trochę pomagamy mniej doświadczonym kolegom, jest znaczący nacisk na elementy związane z bezpieczeństwem, są też wyzwania i awarie, z którymi należy jak najszybciej się uporać bo kosztują naszą organizację pieniądze. Czasem jedna litera jest różnicą między pracą dobrze zrobioną, a niewytłumaczalnym (albo niewybaczalnym) błędem. Jak w prawdziwym życiu, zadań jest więcej niż czasu i warto odpowiednio priorytetyzować.

Powodzenia!

---

### "Zadanie 0"
Najlepiej napisany program i najlepiej wdrożony system jest tykającą bombą bez odpowiedniej dokumentacji. Nikt nie lubi jej pisać, ale jest kluczowa dla łatwości późniejszego utrzymywania i efektywnej współpracy - a także do sprawdzania zadań! Dlatego udokumentuj wszystkie zadania, co najmniej oznaczając te które zostały wykonane, bo **tylko te zostaną sprawdzone**. Niektóre zadania wymagają pisemnej odpowiedzi, umieść je też w dokumentacji.

Opisz kroki wykonane w celu realizacji zadania, szczególnie lokalizacje zasobów, użyte opcje i komendy - nie musisz tego robić bardzo dokładnie, ale w razie wątpliwości będą one działać na twoją korzyść. Na przykład jeśli zadanie nie zostało do końca wykonane, ale znacząca część kroków jest opisana poprawnie, zaliczymy za to częściowe punkty. Albo jeśli zadanie zostało wykonane, ale nie w sposób jaki był spodziewany, to opis będzie kluczem do uzyskania za nie punktów. To, co nie jest opisane, a nie jest oczywiste z interfejsu, będzie rozstrzygane na twoją niekorzyść.

### Zadanie 1
Na klastrze "potyczki" utwórz projekt "web-server" a w nim namespace "nginx". W tym namespace uruchom kontener “nginx” w najnowszej wersji. **5pkt**
- Utwórz usługę dzieki której można się odwołać do naszego nginx z całego klastra **5pkt**
- Chcemy zapewnić wysoką dostępność tej usługi - upewnij się, że cały czas będą działały co najmniej trzy repliki naszego kontenera **2pkt**
- Zapewnij dostępność usługi na internet. Nie masz czasu czekać aż administratorzy sieci udostępnią ci firmowy DNS, a potrzebujesz szybko przetestować dostępność, więc wymyśl jak zapewnić rozwiązywalny url wskazujący na IP hosta, na którym jest twój klaster "potyczki". **25pkt** (pełnym rozwiązaniem jest podanie adresu typu nginx.xxxx.xxxx.xx rozwiązywalnego przy pomocy DNS z internetu, pod którym zgłosi się działająca usługa);
![image](https://github.com/0273574/team-07/assets/59144349/0f19bac5-844a-4279-b565-8fee1288db2d)
![image](https://github.com/0273574/team-07/assets/59144349/faebc696-6b92-4e58-930a-a2d8af470034)
![image](https://github.com/0273574/team-07/assets/59144349/1a9fc3ec-0d23-4416-b9a2-7b9a2c1db4c7)
![image](https://github.com/0273574/team-07/assets/59144349/c4fd2235-19f6-4003-bbba-e4261ccb967a)


### Zadanie 2
 - Sprawdź czy host klastra "potyczki" spełnia wymagania (prerequisites) dla aplikacji Longhorn; doinstaluj ewentualne braki. **5pkt**
 - Z katalogu aplikacji wbudowanych Ranchera zainstaluj Longhorn w najnowszej stabilnej wersji na klastrze "potyczki", ustawiając w konfiguracji instalacyjnej 1 replikę i domyślny StorageClass. **5pkt**
 - Potwierdź status wszystkich podów Longhorna **7pkt**
   ![image](https://github.com/0273574/team-07/assets/59144349/e534d2b7-76f6-4218-8ea3-f51231494ecc)
   ![image](https://github.com/0273574/team-07/assets/59144349/e436c354-5e35-4330-86c6-f6a684f97be3)
   potwierdzenie statusu
   ![image](https://github.com/0273574/team-07/assets/59144349/9a43dce1-953c-49cc-9ef4-018dc1419292)



### Zadanie 3
Dodaj nowe repozytorium do katalogu aplikacji Ranchera. URL repo: https://rancher.github.io/rodeo **5pkt**

Zainstaluj aplikację Tetris z nowo dodanego repo. **5 pkt**

![image](https://github.com/0273574/team-07/assets/59144349/720b2c51-7ef5-46f2-8fa9-ac207fbe1626)
![image](https://github.com/0273574/team-07/assets/59144349/1e4d9160-d006-4c8e-a37b-423a03743655)

### Zadanie 4
Z katalogu aplikacji zainstaluj NeuVector w najnowszej stabilnej wersji. **10pkt**

Włącz funkcję Auto-scan **5 pkt**

![image](https://github.com/0273574/team-07/assets/59144349/f15ac556-a401-4161-99c6-4ffc49a024a6)
![image](https://github.com/0273574/team-07/assets/59144349/9b8d4af0-711c-434a-8c91-50cd03d927d3)

### Zadanie 5
Nasi deweloperzy chcą korzystać z publicznie dostępnych obrazów, ale mogą one zawierać groźne podatności. Dlatego chcemy najperw przeskanować rejestr, zanim zaczniemy z niego korzystać. Użyj NeuVector, żeby przeskanować sekcję nvbeta/* w rejestrze https://registry.hub.docker.com ; jako rozwiązan nie podajazwę image z największą ilością podatności. **7pkt**
![image](https://github.com/0273574/team-07/assets/59144349/cbad091b-f600-4eb8-b885-574278342387)


### Zadanie 6
Po dyskusjach z działem biznesowym doszliśmy do wniosku, że część usług możemy wygasić na noc, żeby zminimalizować koszty. Niestety przeskalowanie do 0 (czyli de facto usunięcie usunięcie poda) powoduje automatyczne usunięcie PersistentVolueClaim, co automatycznie usuwa też przypisany PersistentVolume. A chcemy zachować PersistentVolume i automatycznie podłączyć się do niego z powrotem przy uruchomieniu usługi rano. Jeden z tych deploymentów możliwych do wygaszania jest opisany w "nie-usuwaj.yaml". Zaproponuj rozwiązanie, które zapewni, że po przeskalowaniu do 0 i ponownym wznowieniu opisany deployment "znajdzie" PersistentVolume używany przez poprzednie repliki i się do niego podłączy.

**30 pkt** za odpowiedź teoretyczną wraz z odpowiednim przykładowym kodem yaml.

**30pkt** za odpowiednie zmodyfikowanie i zdeployowanie "nie-usuwaj.yaml" demonstrując działanie teoretycznego rozwiązania na klastrze "potyczki"; +**5 pkt** za użycie provisionera storage z Zadania 2.
--------------------------------------------------------------------------------------------------------------------------------------
Aby rozwiązać ten problem i zachować PersistentVolume po wygaśnięciu usługi, możemy skorzystać z mechanizmu PersistentVolumeClaim oraz opcji woluminów persistentVolumeClaim. Oto jak możemy to zrobić:

Utwórz PersistentVolumeClaim (PVC): Najpierw utwórz PersistentVolumeClaim, który będzie używany przez Deployment do żądania PersistentVolume. PVC powinien mieć stałą nazwę, aby można go było odnaleźć ponownie po wznowieniu usługi.
Przykładowa definicja PVC w pliku persistent-volume-claim.yaml:

Copy code
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: moj-pvc
spec:
  accessModes:
    
ReadWriteOnce
resources:
  requests:
    storage: 1Gi
Zaktualizuj Deployment:
Dodaj wolumin persistentVolumeClaim do definicji kontenera w Deployment, który będzie odwoływać się do PVC.
Upewnij się, że nazwa PersistentVolumeClaim w Deploymentzie odpowiada nazwie utworzonego PVC.
Przykładowa definicja Deploymentu w pliku deployment.yaml:

Copy code
apiVersion: apps/v1
kind: Deployment
metadata:
  name: moj-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: moja-aplikacja
  template:
    metadata:
      labels:
        app: moja-aplikacja
    spec:
      containers:
        
name: moj-kontener
        image: moje-obraz
        volumeMounts:
name: moj-wolumin
          mountPath: /mnt/data
  volumes:
name: moj-wolumin
    persistentVolumeClaim:
      claimName: moj-pvc
Zastosuj PersistentVolumeClaim i Deployment:
Zastosuj PVC i Deployment za pomocą polecenia kubectl apply.


kubectl apply -f persistent-volume-claim.yaml
kubectl apply -f deployment.yaml
Dzięki takiemu podejściu, po wygaśnięciu usługi i ponownym uruchomieniu, Deployment będzie automatycznie żądał tego samego PersistentVolume poprzez utworzony PVC, a PersistentVolume zostanie podłączony do nowego poda. W ten sposób zachowamy dane w PersistentVolume, nawet po wygaśnięciu i wznowieniu usługi.

--------------------------------------------------------------------------------------------------------------------------------------
### Zadanie 7
Twój niezbyt rozgarnięty kolega z pracy, Adrian, prosi cię o poradę: w klastrze mam pewien resource, ale nie wiem jak znaleźć yaml tego zasobu? Jak go podejrzeć?
**5pkt**, +**7pkt** za dodatkową metodę

--------------------------------------------------------------------------------------------------------------------------------------
kubectl get deployment nginx -n namespace -o yaml
--------------------------------------------------------------------------------------------------------------------------------------
### Zadanie
Adrian uruchomił aplikację składającą się z front-endu i bazy danych MySQL. Widzisz, że jego kontener MySQL jest uruchomiony na najprostszych domyślnych ustawieniach. Czy jest to zalecany sposób? Uzasadnij w kilku zdaniach (min. 20 słów dla pełnej punktacji).
**5pkt**, +**5pkt** jeśli uzasadnienie zawiera za i przeciw oraz sugestię poprawy

### Zadanie 8
Wytłumacz Adrianowi w kilku prostych zdaniach czym jest resource o nazwie Gateway w Kubernetes? (min. 20 słów dla pełnej punktacji)
**7pkt**
--------------------------------------------------------------------------------------------------------------------------------------
Uruchomienie kontenera MySQL na domyślnych ustawieniach nie jest zalecanym sposobem w środowiskach produkcyjnych z kilku powodów. Po pierwsze, domyślne ustawienia MySQL mogą być niewystarczające do zapewnienia odpowiedniej wydajności, bezpieczeństwa i niezawodności bazy danych w środowisku produkcyjnym. Po drugie, ustawienia domyślne mogą być podatne na ataki, ponieważ nie zapewniają odpowiedniego zabezpieczenia. Rekomenduje się dostosowanie konfiguracji MySQL do indywidualnych wymagań aplikacji, uwzględniając m.in. optymalizację wydajności, konfigurację zabezpieczeń oraz odpowiednią obsługę awarii. Sugerowaną poprawą jest dostosowanie ustawień MySQL do wymagań aplikacji, w tym m.in. konfiguracja odpowiednich parametrów wydajnościowych, wdrożenie mechanizmów zabezpieczeń (np. uwierzytelnianie, szyfrowanie) oraz wdrożenie strategii backupu i odzyskiwania danych.
Gateway w Kubernetes to obiekt, który definiuje punkt wejścia do klastra lub sieci. Służy do routowania ruchu sieciowego do odpowiednich usług w klastrze na podstawie określonych reguł. Może być wykorzystywany do zarządzania ruchem wewnątrz klastra lub do dostępu do aplikacji zewnętrznych z Internetu. Gateway może być skonfigurowany z różnymi funkcjonalnościami, takimi jak routing, load balancing, czy także ochrona dostępu do aplikacji.
Deployment jest wyżej w hierarchi niż ReplicaSet. Deployment zarządza ReplicaSetami i zapewnia funkcje takie jak deklaratywne zdefiniowanie oczekiwanego stanu aplikacji, aktualizacja wersji aplikacji i obsługa skalowania. ReplicaSet natomiast zapewnia mechanizmy zarządzania replikami podów i jest często używany jako część Deploymentu, ale może być również używany samodzielnie do zarządzania replikami.
--------------------------------------------------------------------------------------------------------------------------------------
### Zadanie 9
Adrian jest bardzo skonfundowany dlaczego są dwa różne resource w Kubernetes, które "robią to samo" czyli zarządzają zestawem identycznych podów: Deployment i ReplicaSet. Wyjaśnij mu na czym polega różnica między tymi resource'ami. (min. 20 słów dla pełnej punktacji)
**7pkt**

### Zadanie 10
Dokonaj aktualizacji klastra "potyczki" to nowszej wersji Kubernetes tak, żeby zminimalizować jej wpływ na dostępność uruchomionych workloadów. **10pkt**

### Zadanie 11
Firma zatrudniła właśnie dwóch nowych pracowników, jako administrator środowiska Kubernetes twoim zadaniem jest utworzyć dla nich konta użytkowników o nazwach w formacie imie.nazwisko i poprawnie przypisać im uprawnienia:
- Nowym dyrektorem IT został Muhammed Yassuff i nalega, żeby mieć podgląd na działanie całego środowiska (uprawnienia get, list, watch).
- Przyjęliśmy także świeżego praktykanta, któremu na razie powierzyliśmy tylko utrzymanie (tj. pełna kontrola) projektu "web-server". Nazywa się on Muhhamad Yussuff.

**5 pkt** za utworzenie dwóch lokalnych użytkowników, po **7 pkt** za poprawne przypisanie uprawnień do każdego z nich (**+5** dodatkowych punktów za rozwiązanie bez żadnej pomyłki i nie nadanie dyrektorowi prawa do podglądu sekretów)

--------------------------------------------------------------------------------------------------------------------------------------
tworzenie uzytkownika muhammed.yassuff w panelu, pozniej stworzenie roli ktora ma uprawnienia do "get, list, watch", dodanie mu tej roli
tworzenie uzytkownika muhammed.yussuff w panelu, poznie przypisanie mu pelnej kontroli do namespacu web-server w ustawieniach projektu
![image](https://github.com/0273574/team-07/assets/59144349/a5fa0b1d-2ff9-4ae1-b2d5-2e18e7591c98)
rola ktora zostałą nadana dala uzytkowwnika muhammed.yassuff
![image](https://github.com/0273574/team-07/assets/59144349/6f45aa23-fc2c-44be-913d-5c1399c8424d)
tutaj dodaje sie uzytkownika do projektu
![image](https://github.com/0273574/team-07/assets/59144349/76723148-b6ca-4581-a079-de3a2934da67)



--------------------------------------------------------------------------------------------------------------------------------------

### Zadanie 12
Jeden z workloadów na klastrze "potyczki", Deployment o nazwie "mysql", nie działa poprawnie. Deweloperzy napisali yaml, ale winią Adriana bo on go zdeployował na klastrze i na pewno coś popsuł bo yaml przecież był ok. Znajdź przyczynę błędu i napraw go. **30 pkt**
--------------------------------------------------------------------------------------------------------------------------------------
wydaje mi sie ze ten deployment wczesniej dzialal zle lecz po zrobieniu zadania 17, zaczal dzialac poprawnie
--------------------------------------------------------------------------------------------------------------------------------------

### Zadanie 13
Nasz workload "nginx" z projektu "web-server" (Zadanie 1) jest prawdopodobnie atakowany z internetu! Użyj NeuVector, żeby zwizualizować wszystkie połączenia sieciowe w klastrze i zapisz zrzut ekranu do dokumentacji (**5 pkt**), oraz przechwyć i zapisz pakiety z ruchu przychodzącego do "nginx" (**10 pkt**). Jeśli Zadanie 1 jest niewykonane, możesz przechwycić pakiety innego poda (udokumentuj który). Możesz sztucznie wygenerować zapytania, żeby mieć co przechwycić.
--------------------------------------------------------------------------------------------------------------------------------------
![image](https://github.com/0273574/team-07/assets/59144349/044cb848-7ea7-48db-8aeb-742168873ae4)
plik z przechwyconymi pakietami został dodany do plików o dość skomplikowanej nazwie jaką wygenerował system, jest dopisane ze jest to plik do tego zadania.


analiza pakietów polega na tym, aby wychwycić kto o jakiej porze wysyłał jakie dane do strony, jak wyglądał proces handhshake TCP, można podejrzeć na jakich portach odbyła się komunikacja, gdyż serwer jest otwarty na porcie 80 lecz klient łączy się z nim po porcie dynamiczny z zakresów 49152 do 65535, bardzo przydatnym narzędziem do analizy przechwyconych pakietów jest wireshark
--------------------------------------------------------------------------------------------------------------------------------------

+**7 pkt** za opis na czym polega analiza pakietów i podanie przykładowego narzędzia do takiej analizy (min. 20 słów dla pełnej punktacji)

### Zadanie 14
Adrian próbuje zdeployować nowy workload i chyba tym razem rzeczywiście coś zepsuł bo za nic nie chce się to uruchomić. Napraw i uruchom adrian-nginx.yaml w nowym namespace o nazwie "adrian". **40 pkt**
--------------------------------------------------------------------------------------------------------------------------------------
po zmienieniu portu, oraz zmienieniu sciezki do httpget i okresleniu namespace w ktorym ma znajdowac sie pod, uruchomił się i działa
![image](https://github.com/0273574/team-07/assets/59144349/08745612-044b-4587-819d-77b07a0501b9)
--------------------------------------------------------------------------------------------------------------------------------------



### Zadanie 15
Przy pomocy NeuVector utwórz regułę blokującą połączenia wychodzące z nginx (Zadanie 3) na zewnątrz klastra i przełącz w tryb aktywnej ochrony (Protect). (**10 pkt**) Wyeksportuj regułętr jako CRD w ybie Protect i załącz do dokumentacji (**5 pkt**). Potwierdź działanie reguły logując się do shella poda nginx i wykonując polecenie curl suse.com  (**7 pkt**). Zablokuj również samo polecenie curl w tym podzie i potwierdź działanie reguły logując się do shella. (**10 pkt**). Dopuszczalne potwierdzenia to zrzuty ekranu lub skopiowane w całości komunikaty shella wraz z poleceniem, które je wyzwoliło - dołącz do dokumentacji.
--------------------------------------------------------------------------------------------------------------------------------------

blokowanie aplikacji tetris
![image](https://github.com/0273574/team-07/assets/59144349/fc15cd4e-e7f0-413c-af73-68092e9f3acc)
![image](https://github.com/0273574/team-07/assets/59144349/d1d0ffde-bd7a-4ba5-880b-6fefc8f16749)
![image](https://github.com/0273574/team-07/assets/59144349/d8f69fba-05b2-4b7e-9e72-51ebf160dfc7)

--------------------------------------------------------------------------------------------------------------------------------------

### Zadanie 16
Jedna z naszych Service nie może się połączyć ze wskazanym Deployment'em. Uruchom "serwis.yaml" w nowym namespace "serwis" i napraw przyczynę problemu. Rozwiązaniem jest Service wskazujący poprawnie na Pod'a nginx zdeployowanego przez "serwis.yaml". **35 pkt**

--------------------------------------------------------------------------------------------------------------------------------------
po nadaniu do pliku yaml namespacu w ktorym ma utworzyc sie serwis wraz z deploymentem, wszytsko razem wstało i na strone da się wejść
![image](https://github.com/0273574/team-07/assets/59144349/f8420121-06c4-4353-82d0-efef94a6d190)
![image](https://github.com/0273574/team-07/assets/59144349/0cde3bca-4eef-4d78-9536-0e11ad0a474b)

--------------------------------------------------------------------------------------------------------------------------------------


### Zadanie 17
Kolejna instancja mysql sprawia problemy, Adrian od trzech dni przez nią nie śpi bo trzyma klaster i przecież wszystko sprawdził. Uruchom baza.yaml w nowym namespace "baza" i doprowadź do poprawnego załadowania się bazy danych. **25 pkt**

 --------------------------------------------------------------------------------------------------------------------------------------
literówka w:
env:
          - name: MYSQL_ROT_PASSWORD
            value: secretpass
![image](https://github.com/0273574/team-07/assets/59144349/0c0f5f5e-4695-40cc-81fa-10f47df4ebbd)

 --------------------------------------------------------------------------------------------------------------------------------------
### Zadanie 18
Adrian chciał uruchomić aplikację "hello-world", ale nawet to mu nie działa. Znajdź przyczynę problemu i uruchom hello-world. **20 pkt**

 --------------------------------------------------------------------------------------------------------------------------------------
nie wiem gdzie jest problem, gdyz w logach pods pokazuje ze image działa pomyślnie, myślałem nad "Deployment does not have minimum availability." lecz nie znalazłem odpowiedzi
