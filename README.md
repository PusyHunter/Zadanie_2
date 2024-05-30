#zaczynamy od inicjalizacji lokalnego repo oraz klonowania go do githuba

git init -b main

gh repo create

#dodajemy potrzebne pliki i comitujemy

git add .

git commit -m "Inicjalizacja repo Zadanie_2"

git push -u origin main

git add .github/workflows/ci.yml

git commit -m "Add CI workflow"

git push -u origin main

#w procesie w celu rozwiazania problemow dodano nowy klucz SSH oraz token

ssh-keygen -t ed25519 -C "ileanid12@gmail.com"

eval "$(ssh-agent -s)"

ssh-add /c/Users/ilean/.ssh/id_ed25519

ssh -T git@github.com


#przelaczono z modeli kontroli http na SSH

git remote set-url origin git@github.com:PusyHunter/Zadanie_2.git

#plik .yaml

Skanujemy obrazu Docker na podatności (CVEs). Parametry konfiguracji określają, że interesują nas tylko krytyczne i wysokie podatności, ignorując te w podstawowych warstwach i niezmienione.
Analizujemy plik wynikowy sarif.output.json za pomocą komendy grep, aby sprawdzić, czy są w nim krytyczne lub wysokie podatności. Jeśli takie są, proces jest przerywany (exit 1).

![image](https://github.com/PusyHunter/Zadanie_2/assets/98088572/4948fba9-9d19-4d35-b77c-77202257741c)

Generujemy metadane obrazu Docker:
images: Pełny identyfikator obrazu (używając GitHub Container Registry i nazwy repozytorium).
tags: Tagowanie obrazu jako "latest".
Budujemy i wypychamy obraz Docker:
context: Kontekst budowania (bieżący katalog).
push: Określa, że obraz ma być wypchnięty do rejestru po zbudowaniu.
tags: Użycie tagów wygenerowanych w poprzednim kroku (${{ steps.meta.outputs.tags }}).

![image](https://github.com/PusyHunter/Zadanie_2/assets/98088572/e9ff95c6-74ca-4e8f-a206-773bc02e73b6)

#Wyniki
![image](https://github.com/PusyHunter/Zadanie_2/assets/98088572/329be720-5d5f-4654-b0a7-086a86da171e)



