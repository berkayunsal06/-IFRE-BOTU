import random

def sifre_olustur():
    return [str(random.randint(0, 9)) for _ in range(4)]

def karsilastir(sifre, tahmin):
    d = y = 0
    for i in range(4):
        if tahmin[i] == sifre[i]:
            d += 1
        elif tahmin[i] in sifre:
            y += 1
    return d, y

sifre = sifre_olustur()
hak = 10

print("BOT SIFREYI OLUSTURDU!")

while hak > 0:
    tahmin = input("Tahmin: ")
    if len(tahmin) != 4 or not tahmin.isdigit():
        print("4 basamakli gir.")
        continue

    d, y = karsilastir(sifre, list(tahmin))
    print("Dogru yer:", d, "Yanlis yer:", y)

    if d == 4:
        print("Bildin!")
        break

    hak -= 1
    print("Hak:", hak)

if hak == 0:
    print("Kaybettin. Sifre:", ''.join(sifre))
