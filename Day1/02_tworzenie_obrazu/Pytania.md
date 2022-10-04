## Pytania lekcja nr. 1 

#### 1. Czy pojedynczy obraz dockera możemy użyć na dowolnym komputerze hosta niezależenie od posiadanej architektury? 

#### 2. Jaki system plików zostanie użyty przez Dockera w łączeniu wielu warstw obrazu w pojedynczy system plików?
    a. Zunifikowany system plików <br>
    b. System plików NTFS <br>
    c. System plików EXT4 <br>
    d. Połączony system plików <br>

#### 3. Jeśli przyjąć założenie że obraz zawiera niezbędne pliki binarne, to które z wymienionych poleceń Dockera pozwala na uzyskanie dostępu do powłoki bash kontenera?
    a. docker shell -it <kontener> /bin/bash
    b. docker run -it <kontener> /bin/bash
    c. docker exec -it <kontener> /bin/bash
    d. docker spawn -it <kontener> /bin/bash
