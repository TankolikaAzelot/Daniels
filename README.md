# Definējam funkciju, kas iegūs datus no lietotāja
def iegut_datus():
    vards = input("Ievadiet vārdu: ")
    uzvards = input("Ievadiet uzvārdu: ")
    loma = input("Ievadiet lomu (admin/viesis): ")
    vecums = int(input("Ievadiet vecumu: "))
    return vards, uzvards, loma, vecums

# Definējam funkciju, kas apvieno datnes un izdrukā informāciju
def apvienot_datnes():
    with open('admin.txt', 'a') as admin_datne, open('viesis.txt', 'a') as viesis_datne:
        vards, uzvards, loma, vecums = iegut_datus()
        rinda = f"{vards} {uzvards} {loma} {vecums}\n"

        if loma.lower() == 'admin':
            admin_datne.write(rinda)
        elif loma.lower() == 'viesis':
            viesis_datne.write(rinda)
        else:
            print("Nepareiza loma. Ievadiet 'admin' vai 'viesis'.")

# Izsaucam funkciju, lai iegūtu datus un ievadītu tos datnēs
apvienot_datnes()

# Aprēķinām vidējo administratora vecumu, visvecāko un visjaunāko administratoru
vecumi = []
with open('admin.txt', 'r') as admin_datne:
    for rinda in admin_datne:
        _, _, _, vecums = rinda.split()
        vecumi.append(int(vecums))

if vecumi:
    videjais_vecums = sum(vecumi) / len(vecumi)
    maksimalais_vecums = max(vecumi)
    minimalais_vecums = min(vecumi)

    print(f"Vidējais administratora vecums: {videjais_vecums}")
    print(f"Visvecākais administrators: {maksimalais_vecums} gadus")
    print(f"Visjaunākais administrators: {minimalais_vecums} gadus")
else:
    print("Nav datu par administratoriem.")

# Izdrukājam, cik ir administratoru un cik viesu
with open('admin.txt', 'r') as admin_datne, open('viesis.txt', 'r') as viesis_datne:
    admin_skaits = len(admin_datne.readlines())
    viesis_skaits = len(viesis_datne.readlines())

    print(f"Administratoru skaits: {admin_skaits}")
    print(f"Viesu skaits: {viesis_skaits}")
# Daniels
Programmesana 12.klase
