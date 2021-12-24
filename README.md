# Proiect-Unreal

Proiectul are ca scop citirea si modificarea automata a unor variabile la runtime.

In evenimentul BeginPlay este apelata functia PropertyLogger unde creeam un map de forma:
" map[nume] = proprietate ".
Acest map este umplut iterand prin toate proprietatile obiectului din care a fost apelata functia.

Variabilele tinta sunt scrise intr-un JSON sub forma: "variabila" : [valoare_minima, valoare_maxima], \
Functia MyFuzzer citeste acest JSON si le parseaza.\
Variabilele modificate sunt vizibile in-game printr-un mesaj debug.\
Momentan functioneaza doar cu valori intregi.

Initial am implementat totul pe o clasa Actor cu intentia de a mosteni catre orice alt obiect ca sa aiba functionalitatea, dar nu imi dau seama daca e usor de facut pe un proiect deja existent.
Ca urmare, am implementat si o clasa Fuzzer care opereaza identic, dar primeste pointer catre un obiect (deci poate fi apelata de orice obiect).
```
#include "Fuzzer.h"

void AMyCharacter::InheritedFuzzer() {
	Fuzzer fuzzer;
	fuzzer.myFuzzer(this);
}
```

### Vreau sa adaug:

- functionalitate pentru float, string
- un fel de a accesa proprietati ale proprietatilor (ex: sa accesam "UCharacterMovementComponent*" direct, ca sa nu depindem in blueprints de "SetMaxWalkSpeed"), probabil prin recursivitate 

Ca sa putem inlocui:
<img width="1031" alt="image" src="https://user-images.githubusercontent.com/32023303/147347800-652e8a54-b546-4365-adda-0dad51c17291.png"> 
Cu: \
<img width="224" alt="image" src="https://user-images.githubusercontent.com/32023303/147348034-d1487ef9-fb8d-4b34-8ead-aa638d212d47.png">
- o librarie existenta pentru manipulare JSON
- input-uri mai utile in blueprints ( fisierul de citit, fisier de scris )
- un caracter controlat automat pe un drum simplu, pe care putem folosi clasa Fuzzer (prin click, prin buton dedicat) pentru a ilustra mai clar rezultatul




### Link-uri utile:
https://www.reddit.com/r/unrealengine/comments/96eda7/can_i_access_variables_across_script_and_blueprint/ \
https://www.unrealengine.com/en-US/blog/unreal-property-system-reflection \
http://shootertutorial.com/2016/03/20/get-set-variables-by-name/ 
