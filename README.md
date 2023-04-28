# procekt1-2
git init
touch skrypt.sh
#!/bin/bash

case "$1" in
  --date)
    echo "Today's date is $(date +"%Y-%m-%d")."
    ;;
  --logs)
    if [[ ! -z "$2" && "$2" =~ ^[0-9]+$ ]]; then
      for (( i=1; i<=$2; i++ )); do
        echo "This is log file $i created by skrypt.sh on $(date +"%Y-%m-%d")." > "log$i.txt"
      done
    else
      for (( i=1; i<=100; i++ )); do
        echo "This is log file $i created by skrypt.sh on $(date +"%Y-%m-%d")." > "log$i.txt"
      done
    fi
    ;;
  --help)
    echo "Usage: skrypt.sh [OPTION]"
    echo "Options:"
    echo "  --date          Display today's date"
    echo "  --logs [n]      Create n log files (default: 100)"
    echo "  --help          Display this help message"
    ;;
  *)
    echo "Invalid option. Use skrypt.sh --help for usage instructions."
    ;;
esac
[7:30 PM]
echo "log*.txt" > .gitignore
[7:30 PM]
git add skrypt.sh .gitignore
git commit -m "Initial commit"
[7:30 PM]
git checkout -b date-option
[7:30 PM]
#!/bin/bash

case "$1" in
  --date)
    echo "Today's date is $(date +"%Y-%m-%d")."
    ;;
  --logs)
    if [[ ! -z "$2" && "$2" =~ ^[0-9]+$ ]]; then
      for (( i=1; i<=$2; i++ )); do
        echo "This is log file $i created by skrypt.sh on $(date +"%Y-%m-%d")." > "log$i.txt"
      done
    else
      for (( i=1; i<=100; i++ )); do
        echo "This is log file $i created by skrypt.sh on $(date +"%Y-%m-%d")." > "log$i.txt"
      done
    fi
    ;;
  --help)
    echo "Usage: skrypt.sh [OPTION]"
    echo "Options:"
    echo "  --date          Display today's date"
    echo "  --logs [n]      Create n log files (default: 100)"
    echo "  --help          Display this help message"
    ;;
  *)
    echo "Invalid option. Use skrypt.sh --help for usage instructions."
    ;;
esac
#!/bin/bash

# Zadanie 1
 skrypt.sh -h
 skrypt.sh -l 30
 skrypt.sh -d
 skrypt.sh --init
 skrypt.sh --error 30
 skrypt.sh -e 30

# Zadanie 2
# Dodanie flag -h, -l, -d do skryptu
while getopts ":hl:d:e:-:" opt; do
  case ${opt} in
    h )
      echo "Użycie: skrypt.sh [FLAG]"
      echo "Flagi:"
      echo "-h, --help      Wyświetla pomoc"
      echo "-l, --logs      Tworzy pliki logów"
      echo "-d, --date      Wyświetla dzisiejszą datę"
      echo "-e              Tworzy pliki error"
      echo "--init          Klonuje całe repozytorium do katalogu w którym został uruchomiony oraz ustawia ścieżkę w zmiennej środowiskowej PATH"
      exit 0
      ;;
    l )
      echo "Tworzenie plików logów"
      num_logs=${OPTARG:-100}
      for i in $(seq 1 $num_logs); do
        echo "Nazwa pliku: log$i.txt, nazwa skryptu: skrypt.sh, data: $(date)" > log$i.txt
      done
      ;;
    d )
      echo "Dzisiejsza data: $(date)"
      ;;
    e )
      echo "Tworzenie plików error"
      num_errors=${OPTARG:-100}
      for i in $(seq 1 $num_errors); do
        mkdir -p error$i
        echo "Nazwa pliku: error$i.txt, nazwa skryptu: skrypt
