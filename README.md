- 👋 Hi, I’m @Albin119814
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Albin119814/Albin119814 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import random

# Första spelarens attribut
spelare1 = {
    "Namn": "",
    "Hälsa": 100,
    "Sköld": 50,
    "Vapen": "",
    "Skada": 0
}

# Andra spelarens attribut
spelare2 = {
    "Namn": "",
    "Hälsa": 100,
    "Sköld": 50,
    "Vapen": "",
    "Skada": 0
}

# Funktion för att välja vapen
def valj_vapen():
    vapen_lista = ["Hagelgevär", "Pistol", "Snipergevär", "Granatkastare"]
    valt_vapen = random.choice(vapen_lista)
    return valt_vapen

# Funktion för att utföra ett anfall
def attackera(angripare, försvarare):
    skada = random.randint(10, 20)
    if försvarare["Sköld"] > 0:
        försvarare["Sköld"] -= skada
        if försvarare["Sköld"] < 0:
            försvarare["Hälsa"] += försvarare["Sköld"]
            försvarare["Sköld"] = 0
    else:
        försvarare["Hälsa"] -= skada
    angripare["Skada"] += skada

# Funktion för att skriva ut spelarstatus
def skriv_status(spelare):
    print("Namn:", spelare["Namn"])
    print("Hälsa:", spelare["Hälsa"])
    print("Sköld:", spelare["Sköld"])
    print("Vapen:", spelare["Vapen"])
    print("Total skada:", spelare["Skada"])

# Huvudprogrammet
print("Välkommen till Fortnite-simulatorn!")
spelare1["Namn"] = input("Ange namn för spelare 1: ")
spelare2["Namn"] = input("Ange namn för spelare 2: ")

spelare1["Vapen"] = valj_vapen()
spelare2["Vapen"] = valj_vapen()

while True:
    print("------------------")
    print("Spelare 1 är", spelare1["Namn"])
    print("Spelare 2 är", spelare2["Namn"])
    print("------------------")

    attackera(spelare1, spelare2)
    attackera(spelare2, spelare1)

    skriv_status(spelare1)
    skriv_status(spelare2)
    
    svar = input("Vill ni fortsätta spelet? (ja/nej): ")
    if svar.lower() == "nej":
        break

print("Spelet är slut. Tack för att ni spelade!")
