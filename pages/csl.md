# ParseCalcSymbol - parsowanie Symboli matematycznych

### Funkcja pobiera tekst i sprawdza czy operacja jest operacją jedną z poniższej listy:
## OPERACJE ARYTMETYCZNE
####  Operacje oznaczone {P} są rozwiązywane na etapie parsowania a nie lekserowania
  - ``` + ```  Dodawanie                       Addition        (a + b) JS,PHP
  - ``` - ```  Odejmowanie                     Subtraction     (a - b) JS,PHP
  - ``` / ```  Dzielenie                       Division        (a / b) JS,PHP
  - ``` * \| x \| · \| ⋅ ```  Mnożenie            Multiplication  (a * b) JS,PHP
  - ``` % ```  Reszta z dzielenia całkowitego  Modulus         (a % b) JS,PHP
  - ``` ++ ``` Zwiększenie o jeden (Pre)       Increment       (++a )  PHP     {P}
  - ``` -- ``` Zmniejszenie o jeden (Pre)      Decrement       (--a )  PHP     {P}
  - ``` ++ ``` Zwiększenie o jeden             Increment       (a++ )  JS,PHP  {P}
  - ``` -- ``` Zmniejszenie o jeden            Decrement       (a-- )  JS,PHP  {P}
  - ``` ** ``` Podniesienie do potęgi          Exponentiation  (a**2 ) JS
  - ``` // ``` Pierwiastek                     RootExtraction  (a//2 ) ------
### 
## Operacje PRZYPISANIA
####  Wszystkie przypisania są rozwiązywane na etapie parsowania a nie lekserowania
#####  Podane nazwy funkcji mogą się zmienić
  - ``` : ```  Przypisanie             Assignment  <all>       <all>           (a:b)
  - ``` :+ ``` Dopisanie                           <container> <all>           (a:+b) => (@push(a,b) \| a.push(b))
  - ``` :- ``` Odpisanie                           <container> <all>           (a:-b) => (@remove(a,b) \| a.remove(b))
  - ``` :*- ``` Odpisanie Wszystkich               <container> <all>           (a:-b) => (@removeAll(a,b) \| a.removeAll(b))
  - ``` :* ``` Zmultiplikowanie                    <container> <all>           (a:*b) 
  - ``` :+ ``` Dodanie                             <number>
  - ``` :- ``` Odjęcie                             <number>
  - ``` :* ``` Mnożenie                            <number>
  - ``` :/ ``` Dzielenie                           <number>
  - ``` :% ``` Reszta z dzielenia                  <number>                    ( a %: b) => (a: a % b)
  - ``` :. ``` Dopisanie tekstu                                                (a:.b) => (a: a.b)
  - ``` :# ``` Dopisanie kontenera                                             (a:#b) => (a: a#b)
### 
## Operacje na tekstach
  - ``` + ``` ``` . ``` Dopisanie tekstu               Addition \| Concatenation       (a+b \| a.b)   ```"Abc"+"Def" \| "Abc"."Def"```
###
####  Użycie ``` + ``` jest niejednoznaczne, więc może zwracać nieoczekiwane wartości przy konwertowaniu typów
### 
## Operacje na kontenerach 
  - ``` + ``` ```# ``` Dopisanie treści kontenera     Addition \| ContainerJoin     (a+b \| a#b) ``````1,2,3```+```4,5,6``` \| ```1,2,3```#```4,5,6``````
### 
####  Użycie ``` + ```  jest niejednoznaczne, więc może zwracać nieoczekiwane wartości przy konwertowaniu typów
### 
## Operatory logiczne
####  Zamiast operatora ``` == ``` można używać ``` = ```, gdyż nigdy w programie nie jest on używany jako przypisanie
####  Należy pamiętać, że w operatorach tak jak we wszystkich stałych językowych nie liczy się wielkość liter
####  Operatory  ``` AND \| OR \| XOR \| EOR \| ~ \| NOT``` Są używane także przy operacjach bitowych. 
####    Ich interpretacja domyślna jest bitowa, jednak zmienia się na logiczną, jeżeli operatory nie są typu <integer>, bądź jeżeli oznaczymy operatory jako logiczne
  - ``` && \| AND \| ∧ ```                    Logiczne i                             LogicAnd \| And      (a && b \| a AND b \| a ∧ b )
  - ``` || \| OR \| ∨ \| v ```                 Logiczne lub                           LogicOr \| Or        (a || b \| a OR b \| a ∨ b)    
  - ``` ⊻ \| XOR \| EOR \| <> \| != \| ~= ```    Logiczne XOR \| Logiczna nierówność     Inequality \| Xor    (a ⊻ b \| a XOR b \| a <> b \| a != b)
  - ``` ~ \| ! \| ¬ \| NOT```                  Logiczne zaprzeczenie                  LogicNot \| Not         
  - ``` = \| == \| ⇔ ```                     Logiczna równość                       Equality
  - ``` === \| ≡ ```                         Logiczna równość i identyczność typów  Identity
  - ``` !== \| ~== ```                       Nie identyczność                       Non-identity
  - ``` -> \| ⇒ \| → \| TO```                 Logiczna implikacja                    Implication
  - ``` > ```                               Większy niż                            Greater
  - ``` < ```                               Mniejszy niż                           Less
  - ``` >= \| => ```                         Większy, bądz równy                    GreaterOrEqual
  - ``` <= \| =< ```                         Mniejszy, bądz równy                   LessOrEqual
### 
## Operatory Bitowe
####  Należy pamiętać, że w operatorach tak jak we wszystkich stałych językowych nie liczy się wielkość liter
####  Operatory  ``` AND \| OR \| XOR \| EOR \| ~ \| NOT``` Są używane także przy operacjach logicznych. Jendak zachowanie Bitowe jest domyślne
  - ``` & \| AND ```        Bitowe i  (a & b \| a AND b )                            ByteAnd \| And         
  - ``` \| | OR ```         Bitowe lub (a \| b \| a OR b )                            ByteOr \| Or
  - ``` XOR \| EOR \| ^ ```  Bitowe XOR                                              Xor
  - ``` << ```             Przesunięcie w lewo                                     LeftShift
  - ``` >> ```             Przesunięcie w prawo                                    RightShift
  - ``` >>> ```             Przesunięcie w prawo bez znaku                         UnsignedRightShift
### 
### TODO: Operatory strumieni danych