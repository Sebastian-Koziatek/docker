## POD
Pod to najmniejsza jednostka wykonawcza w Kubernetes. Pod zawiera jedną lub więcej aplikacji. Pody są z natury efemeryczne, jeśli pod (lub węzeł, w którym jest wykonywany) ulegnie awarii, Kubernetes może automatycznie utworzyć nową replikę tego poda, aby kontynuować operacje. Pody zawierają jeden lub więcej kontenerów (takich jak kontenery Dockera).

Pody zapewniają również zależności środowiskowe, w tym trwałe woluminy magazynu (magazyn trwały i dostępny dla wszystkich podów w klastrze) oraz dane konfiguracyjne potrzebne do uruchomienia kontenerów w pode.

### `Co robi Pod?`

Pody reprezentują procesy działające w klastrze. Ograniczając pody do jednego procesu, Kubernetes może raportować o kondycji każdego procesu działającego w klastrze. Strąki mają:

- unikalny adres IP (który pozwala im komunikować się ze sobą)
- stałe woluminy pamięci masowej (zgodnie z wymaganiami)
- informacje o konfiguracji określające sposób działania kontenera.

Chociaż większość `POD` zawiera jeden kontener, wiele z nich będzie mieć kilka pojemników, które ściśle ze sobą współpracują, aby wykonać żądaną funkcję.