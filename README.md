# Dokumentacja

<table>
    <tr>
        <td>Temat</td>
        <td>Dokumentacja</td>
    </tr>
    <tr>
        <td>Docker</td>
        <td><a href="https://docs.docker.com/" title="Doker dokumentacja">Link</td>
    </tr>
    <tr>
        <td>CNCF Cloud Native Interactive Landscape</td>
        <td><a href="https://landscape.cncf.io/" title="CNCF">Link</td>
    </tr>
    <tr>
        <td>CNCF Cloud Native Interactive Landscape</td>
        <td><a href="https://landscape.cncf.io/" title="CNCF">Link</td>
    </tr>
    <tr>
        <td>Swagger</td>
        <td><a href="https://petstore.swagger.io/" title="Swagger">Link</td>
    </tr>
</table>

__________________________________________________________________________

# DOCKER INSTALACJA
## Linux 
Install Docker Desktop on Linux

<table>
    <tr>
        <td><a href="https://docs.docker.com/desktop/install/ubuntu/" title="Ubuntu">Ubuntu</td>
        <td><a href="https://docs.docker.com/desktop/install/ubuntu/" title="Ubuntu">Debian</td>
        <td><a href="https://docs.docker.com/desktop/install/ubuntu/" title="Fedora">Fedora</td>
    </tr>
</table>

## Windows 
Install Docker Desktop on Windows
Zalecana jest instalacja dockera wraz z WSL2

<table>
    <tr>
        <td><a href="https://docs.docker.com/desktop/install/ubuntu/" title="Windows">Windows</td>
        <td><a href="https://learn.microsoft.com/pl-pl/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package" title="Windows">WSL2</td>
    </tr>
</table>

## MacOS
Install Docker Desktop on Mac

<table>
    <tr>
        <td><a href="https://docs.docker.com/desktop/install/mac-install/" title="MacOS">MacOS</td>
        <td><a href="https://docs.docker.com/desktop/mac/apple-silicon/" title="Windows">MacOS ARM Apple CPU</td>
    </tr>
</table>

__________________________________________________________________________


# Docker komendy
### Zarządzanie kontenerami
<table>
    <tr>
        <td><b>Komenda (docker) </b></td>
        <td><b>Opis</b></td>
    </tr>
    <tr>
        <td>start</td>
        <td>uruchamia istniejący kontener</td>
    </tr>
    <tr>
        <td>stop</td>
        <td>zatrzymuje kontener</td>
    </tr>
    <tr>
        <td>run</td>
        <td>tworzy nowy kontener i uruchamia go</td>
    </tr>
    <tr>
        <td>ls </td>
        <td>wyświetla listę działających kontenerów</td>
    </tr>
    <tr>
        <td>logs</td>
        <td>pokazuje logi kontenera</td>
    </tr>
    <tr>
        <td>kill</td>
        <td>zabija działanie kontenera</td>
    </tr>
    <tr>
        <td>rm</td>
        <td>kasuje kontener</td>
    </tr>
</table>

### Obrazy

<table>
    <tr>
        <td><b>Komenda (docker image)</b></td>
        <td><b>Opis</b></td>
    </tr>
    <tr>
        <td>build</td>
        <td>zbuduj obraz</td>
    </tr>
    <tr>
        <td>push</td>
        <td>wysyła obraz do repozytorium</td>
    </tr>
    <tr>
        <td>history</td>
        <td>wyświetla historie obrazu</td>
    </tr>
    <tr>
        <td>inspect</td>
        <td>wyświetla informacje o obrazie</td>
    </tr>
    <tr>
        <td>rm</td>
        <td>kasuje obraz</td>
    </tr>
</table>

__________________________________________________________________________
# Linki

### Oficjalna dokumentacja:
- <a href="https://www.docker.com/">docker</a> - dokumentacja dockera
- <a href="https://hub.docker.com/">DockerHub</a> - ropzytorium obrazów dockera
- <a href="https://kubernetes.io/">kubernetes</a> - dokumentacja 
- docker compose <a href="https://docs.docker.com/compose/compose-file/compose-file-v2/" title="docker-compose version 2"> Version:2</a></td> i <a href="https://docs.docker.com/compose/compose-file/compose-file-v3/" title="docker-compose version 3">Version:3 </a>
- <a href="https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html"> Yaml </a> na podstawie ansible 

### Docker in cloud:
- <a href="https://cloud.google.com/compute/docs/containers"> Google cloud platform </a> - Darmowe do wypróbowania
- <a href="https://cloud.digitalocean.com"> Digital Ocean</a> - Darmowe 200$ / 2 miesiace (limitowany deploy k8s)
- 
### Użyteczne linki: 

1. Docker best practice by  <a href="https://dev.to/techworld_with_nana/top-8-docker-best-practices-for-using-docker-in-production-1m39">TechWorld with Nana</a>
2. Basics of Container Isolation by Sushil Kumar <a href="https://blog.devgenius.io/basics-of-container-isolation-5eabdb258409v">blog.devgenius.io </a>
3. Kubernetes services by Kim Wuestkamp <a href="https://medium.com/swlh/kubernetes-services-simply-visually-explained-2d84e58d70e5">medium.com</a> 


4Fun
- <a href="https://github.com/storax/kubedoom?fbclid=IwAR1dFVhMiIQ8xH6mJ_IBjUNjbOUf4-0VtnO9E85QJJCicBqZjPBTLHERIwg">Doom</a> na kubernetesie
- `docker run -it jturpin/hollywood hollywood` - pokaż jak cięzko pracujesz!
  

Brakująca lekcja - Konfiguracja `LetsEncrypt` do zabezpiczenia swojego registry - <a href="https://ivhani.medium.com/setting-up-a-docker-registry-with-https-letsencrypt-and-basic-authentication-htpasswd-3ea1961a4144"> link </a>