# T03: Seguretat Lògica: recuperant accés a sistemes

## Recuperació de la contrasenya d'usuari

Amb el disc virtual facilitat pel client, creem una màquina virtual Linux sense disc i hi afegim el disc virtual proporcionat.

<img src="img/01.png" alt="Captura d'imatge on es mostren les característiques de la màquina virtual">

En iniciar la màquina, podem observar que hi ha un usuari anomenat **Miquel Valls**.

<img src="img/02.png" alt="Pantalla de login d’en Miquel Valls" width="550">

Reiniciem la màquina prement repetidament la tecla **Shift** per interrompre l’arrencada i accedir a les opcions avançades, des d’on entrarem en el mode de recuperació.

<img src="img/03.png" alt="Pantalla del mode de recuperació de Zorin OS" width="550">
<img src="img/04.png" alt="Pantalla del mode de recuperació de Zorin OS" width="550">

Al menú de recuperació, seleccionem l’opció **root** per accedir a la consola del superusuari.

<img src="img/05.png" alt="Pantalla del menú de recuperació" width="550">

Un cop dins, hem de muntar el sistema en mode lectura/escriptura amb la comanda `mount -rw -o remount /`, ja que, en cas contrari, no ens permetrà canviar la contrasenya i mostrarà un error com aquest:

```
Authenticacion token manipulation error
passwd: password unchanged
```

Després, fem un `cat /etc/passwd` per veure l’usuari de Miquel Valls i comprovem que el seu nom d’usuari és `miquel`.

<img src="img/06.png" alt="'cat /etc/passwd' per veure l’usuari d’en Miquel Valls" width="550">

Ara ja podem executar la comanda següent per canviar la seva contrasenya:

<img src="img/07.png" alt="Canvi de contrasenya d’en Miquel" width="450">

Assignem la nova contrasenya: **everpia2025**.

Finalment, reiniciem la màquina amb normalitat i ja podrem iniciar sessió sense problemes amb la nova contrasenya.

<img src="img/08.png" alt="Pantalla de login d’en Miquel Valls" width="350">

Verifiquem que podem accedir amb normalitat a l’usuari després del canvi de contrasenya.

<img src="img/09.png" alt="Pantalla d’inici de Zorin OS" width="550">

---

## Fortificació de l’accés al GRUB

Un cop hem comprovat com de ràpid és canviar la contrasenya, el client ens demana protegir l’equip de manera que l’accés al GRUB quedi protegit amb contrasenya, per tal d’evitar modificacions a la configuració del sistema.

La solució és **fortificar l’accés al GRUB**, establint un usuari i una contrasenya per evitar que algú amb accés físic a la màquina pugui modificar els paràmetres d’arrencada, entrar en mode de recuperació o accedir a la terminal com a root per fer canvis al sistema.

### 1. Generar una contrasenya xifrada per al GRUB

El primer pas és **generar una contrasenya xifrada per al GRUB** en format **hash**, amb la comanda:

```bash
grub-mkpasswd-pbkdf2
```

Però com que **afegir manualment el hash a un fitxer no és pràctic**, farem servir l’ordre **tee**, que ens permet **redirigir la sortida estàndard cap a un fitxer**. Per tant, escriurem:

```bash
grub-mkpasswd-pbkdf2 | tee hash.txt
```

<img src="img/10.png" alt="Comanda per a crear el hash" width="550">

Assignem la contrasenya: **everpia2025@**

### 2. Editar el fitxer de configuració del GRUB

Editem el fitxer `/etc/grub.d/40_custom` per afegir-hi l’autenticació. Incloem el hash generat anteriorment.

Obrim l’editor nano amb multibuffer:

```bash
sudo nano -F /etc/grub.d/40_custom
```

<img src="img/11.png" alt="Editant el fitxer /etc/grub.d/40_custom" width="550">

Premem `CTRL + R` i introduïm el nom del fitxer d’origen (`hash.txt`). Veiem el contingut del fitxer a la pantalla.

<img src="img/12.png" alt="Introduint el fitxer d’origen" width="550">

Copiem el bloc de text amb el hash. Ens situem a l’inici de la línia, premem `ALT + A`, anem fins al final (amb el cursor o `CTRL + E`) i copiem amb `ALT + 6`. Tanquem el fitxer amb `CTRL + X`.

De nou dins `/etc/grub.d/40_custom`, afegim al final les següents línies:

```bash
set superusers="nom_login"
password_pbkdf2 nom_login <hash_generat>
```

**Nota:**  
- `nom_login` és l’identificador per autenticar-nos al GRUB.  
- El hash s’enganxa a la segona línia després del nom d’usuari (`CTRL + U`).  
- Aquest usuari no cal que coincideixi amb un usuari del sistema operatiu.

<img src="img/13.png" alt="A dins de /etc/grub.d/40_custom" width="550">

Un cop fet, desem i sortim de nano.

### 3. Aplicar els canvis a la configuració del GRUB

Executem:

```bash
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

<img src="img/14.png" alt="Aplicant els canvis del GRUB" width="550">

Després reiniciem el sistema i comprovem que ens demana usuari i contrasenya abans de carregar el gestor d’arrencada.

<img src="img/15.png" alt="Pantalla de login en intentar entrar al gestor d’arrencada" width="550">

---

### EXTRA: demanar la contrasenya del GRUB només per editar o per mode recovery

Ara documentarem com fer que només es demani la contrasenya del GRUB quan volem editar-lo o iniciar el sistema en mode recovery.

1. Obrir la terminal com a root i utilitzar `gedit` per editar l’arxiu necessari:

   <img src="img/16.png" alt="Executant la comanda gedit" width="350">

3. Un cop dins, obrirem el fitxer `/etc/grub.d/10_linux`, que és on farem la modificació:

   <img src="img/17.png" alt="A dins del fitxer etc/grub.d/10_linux" width="550">

3. Dins l’arxiu hem de localitzar la línia on apareix l’opció `--class os` (sovint dins d’una definició de classe o d’una línia que comença amb `CLASS=`).

   <img src="img/18.png" alt="Editant el fitxer etc/grub.d/10_linux" width="750">
   
   Perquè la contrasenya del GRUB només es demani quan intentem editar una entrada o iniciar en mode recovery,
   afegiu l’opció `--unrestricted` just després de `--class os`, quedant així:

   <img src="img/19.png" alt="Editant el fitxer etc/grub.d/10_linux" width="750">
   
   Aquesta modificació fa que les entrades marcades com a "unrestricted" s’executin sense demanar autenticació;
   la resta d’operacions sensibles (com editar una línia del GRUB o accedir al mode recovery) seguiran exigint
   usuari i contrasenya.

5. Desa el fitxer i aplica els canvis a la configuració del GRUB:

   <img src="img/20.png" alt="Executant la comanda update-grub2" width="450">
   
   Un cop fet això, **reiniciem el sistema** i comprovem que **ja no es demana la contrasenya per arrencar la
   màquina de manera normal**, però sí quan intentem **editar el GRUB o accedir al mode de recuperació**.

   <img src="img/21.png" alt="Iniciant la màquina Zorin" width="550">

---

## Resultat

Amb aquest procediment, protegim el nostre equip contra accessos no autoritzats, tant pel que fa a la recuperació de contrasenyes com a la modificació de la configuració d’arrencada.

[Tornar a enunciat](README.md)
