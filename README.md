# ⚡ Simulador i Validador de Pseudocodi

Una eina web estàtica i lleugera dissenyada per analitzar la sintaxi, verificar el compliment estricte del sistema de tipus i simular l'execució interactiva d'algorismes escrits seguint la notació del **Nomenclàtor de Pseudocodi**.

S'executa íntegrament en el navegador (client-side), sense necessitat de servidors, terminals ni dependències externes. 🚀

---

## 🛠️ Característiques principals

* **🔍 Validació estàtica i comprovació de tipus:**
  * **Operador de divisió real (`/`):** Alerta d'error si s'intenta aplicar sobre operands de tipus `integer` (exigeix l'ús de `div` o de conversions prèvies amb `integerToReal`).
  * **Signatures estrictes de conversió:**
    * `codeToChar`: Comprova que el paràmetre sigui un enter (`integer`, codi ASCII).
    * `charToCode`: Exigeix un literal o variable de tipus caràcter (`char`).
    * `realToInteger`: Simula el truncament estricte de la part decimal cap a zero.
  * **Coherència en dades:** Comprova que les constants reals incloguin la notació decimal explícita (`.0`) i que els tipus enumerats no tinguin identificadors entre cometes dobles.

* **💻 Entorn d'execució interactiu:**
  * Lectures de dades tipades per consola (`readInteger()`, `readReal()`, `readChar()`, `readString()`, `readBoolean()`).
  * Escriptura pel canal estàndard (`writeString()`, `writeInteger()`, `writeReal()`, etc.).
  * Suport per a operadors algorítmics: `div`, `mod`, `=`, `≠`, `<`, `>`, `≤`, `≥`, `and`, `or`, `not`.

---

## 💡 Exemple d'ús

Enganxa aquest exemple a l'editor i prem **Valida i Executa ▶**:

```text
const
    L_TO_CC: real = 1000.0;
end const

algorithm volumeConversion
    var
        volume: integer;
    end var

    writeString("Input volume (in cc): ");
    volume := readInteger();

    writeString("The volume (in l) is: ");
    writeReal(integerToReal(volume) / L_TO_CC);
end algorithm
```

---

## 📚 Especificació del Nomenclàtor

### 1. Comentaris 📝
```text
{ comment }
```

### 2. Estructura general d'un algorisme 🏗️
```text
algorithm algorithmName
    {Define variables}
    var
        intVar: integer;
    end var

    {Initialize variables}
    intVar := 0;

    {Add as many instructions as you need}
end algorithm
```

### 3. Tipus bàsics de dades 🧩
* `integer`
* `char`
* `real`
* `boolean` (valors: `true`, `false`)
* `string`

### 4. Definició de variables i constants 📦
```text
var
    intVar: integer;
    charVar: char;
    realVar: real;
    booleanVar: boolean;
    stringVar: string;
end var

const
    INTEGER_CONST: integer = 20;
    CHAR_CONST: char = 'a';
    REAL_CONST: real = 12.9;
    BOOLEAN_CONST: boolean = true;
    STRING_CONST: string = "Hello!";
end const
```

### 5. Operadors ⚙️
* **Assignació:** `:=`
* **Lògics:** `and`, `or`, `not`
* **Comparació:** `=`, `≠`, `<`, `>`, `≤`, `≥`
* **Aritmètica entera:** `div` (quocient enter), `mod` (residu de la divisió)
* **Divisió real:** `/` (admet únicament operands de tipus `real`)

### 6. Funcions de canvi de tipus 🔄
```text
function integerToReal(varName: integer): real;
function realToInteger(varName: real): integer;
function charToCode(varName: char): integer;
function codeToChar(varName: integer): char;
```

### 7. Entrada i sortida (E/S) 📥📤

#### Variables i consola interactiva
```text
function readInteger(): integer;
function readReal(): real;
function readChar(): char;
function readString(): string;
function readBoolean(): boolean;

action writeInteger(in varName: integer);
action writeReal(in varName: real);
action writeChar(in varName: char);
action writeString(in varName: string);
action writeBoolean(in varName: boolean);
```

#### Fitxers 📁
```text
function openfile(fileName: string): file;
action closeFile(inout fileName: string);
function readIntegerFromFile(fileToRead: file): integer;
function readRealFromFile(fileToRead: file): real;
function readCharFromFile(fileToRead: file): char;
function readStringFromFile(fileToRead: file): string;
function readBooleanFromFile(fileToRead: file): boolean;
function isEndOfFile(fileToRead: file): boolean;
action writeIntegerToFile(inout fileToWrite: file, in varName: integer);
action writeRealToFile(inout fileToWrite: file, in varName: real);
action writeCharToFile(inout fileToWrite: file, in varName: char);
action writeStringToFile(inout fileToWrite: file, in varName: string);
action writeBooleanToFile(inout fileToWrite: file, in varName: boolean);
```

### 8. Tipus avançats i estructures 🧱

#### Vectors
```text
const
    NUM_ELEMENTS: integer = 10;
end const

var
    integerVector: vector[NUM_ELEMENTS] of integer;
    charVector: vector[NUM_ELEMENTS] of char;
    realVector: vector[NUM_ELEMENTS] of real;
    booleanVector: vector[NUM_ELEMENTS] of boolean;
    stringVector: vector[NUM_ELEMENTS] of string;
end var
```

#### Tuples (Registres)
```text
type
    tupleName = record
        realField: real;
        {Pots definir altres camps seguint l'esquema}
    end record
end type
```

#### Tipus enumerats
```text
type
    tStreamingPlatform = {NETFLIX, HBO, DAZN, EUROSPORT}
end type
```

#### Punters 🎯
```text
var
    pointerToIntName: pointer to integer;
    pointerToRealName: pointer to real;
end var
```

### 9. Estructures de control 🔀

#### Condicionals
```text
if i = j then
    i := j + 2;
end if

if i = j then
    i := j + 2;
else
    i := j - 2;
end if

switch variable
    case variable = value1 then
        {Instruccions}
    end case
    case variable = value2 then
        {Instruccions}
    end case
    case default then
        {Instruccions}
    end case
end switch
```

#### Iteratives 🔁
```text
while i < j do
    value1 := value2 + i;
    i := i + 1;
end while

for i := initialValue to finalValue do
    value1 := value2 + i;
end for

for i := initialValue to finalValue step 2 do
    value1 := value2 + i;
end for
```

### 10. Subprogrames: Funcions i Accions 🧩

#### Funcions
```text
function functionName(parName1: integer, parName2: integer): integer
    return parName1 + parName2;
end function
```

#### Accions i pas de paràmetres (`in`, `out`, `inout`)
```text
action actionName(in parName1: integer, out parName2: real, inout parName3: boolean)
    parName2 := 2.0 * integerToReal(parName1);
    parName3 := not parName3;
end action
```

---

## 📜 Llicència

Projecte distribuït sota la llicència [MIT](LICENSE).
