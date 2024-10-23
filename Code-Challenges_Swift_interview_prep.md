# **`Interview Prep`** 

`Preparation for interview to Junior Developer role`

## **`Code challenges (Swift version)`**

`Here are some code challenges to test the coding abilities for a Junior Developer:`

1. **`FizzBuzz`**

`Write a program that prints the numbers from 1 to 100, but for multiples of 3, print "Fizz" instead of the number, and for multiples of 5, print "Buzz" instead of the number. For numbers that are multiples of both 3 and 5, print "FizzBuzz".`

| for i in 1...100 {    if i % 3 \== 0 && i % 5 \== 0 {        print("FizzBuzz")    } else if i.isMultiple(of: 3) {        print("Fizz")    } else if i.isMultiple(of: 5) {        print("Buzz")    } else {        print(i)    }} |
| :---- |

2. **`Reverse String`**

`Write a function that takes a string as input and returns the string reversed.`  
`Example input: "hello" Example output: "olleh"`

| func reverseString(\_ input: String) \-\> String {    return String(input.reversed())}reverseString("hello") // return "olleh" |
| :---- |

`Ou usando apenas funções “nativas” de Array podemos:`

| func reverseString(\_ input: String) \-\> String {    var charArray \= \[Character\]() // Inicializar um array de Character vazio    for char in input {        charArray.insert(char, at: 0) // inserir cada Character no início do array    }    return String(charArray) // converte o array\[Character\] para uma String} |
| :---- |

3. **`Find the Maximum`**

`Write a function that takes an array of integers as input and returns the maximum value in the array.`

`Example input: [1, 2, 3, 4, 5] Example output: 5`

| func findMaximum(\_ input: \[Int\]) \-\> Int? {    return input.max()}findMaximum(\[1,2,3,4,5\]) // return 5 |
| :---- |

`Or:`

| func findMaximum(\_ input: \[Int\]) \-\> Int {    var maxVal \= input\[0\]    for i in 1..\<input.count {        if input\[i\] \> maxVal {            maxVal \= input\[i\]        }    }    return maxVal}findMaximum(\[1,2,3,4,5\]) // return 5 |
| :---- |

4. **`Unique elements`**

`Write a function unique() to return only the unique elements of an Array`  
`Resolution: use Array and Set`

| func unique(\_ input: \[Int\]) \-\> \[Int\] {    return Array(Set(input))}unique(\[1,5,5,5,5,2\]) // return \[5, 2, 1\] |
| :---- |

5. **`Same elements`**

`Write a true or false function to return if the 2 Arrays have the same elements`  
`Example1: [1, 2, 3] and [2, 1, 3] have the same content`  
`Example2: [1, 2] and [1, 2, 3] don't have the same content`

| func haveSameElements(\_ input1: \[Int\], \_ input2: \[Int\]) \-\> Bool {    return Set(input1) \== Set(input2)}haveSameElements(\[1,2,3\], \[2,1,3\]) // return truehaveSameElements(\[1,2\], \[1,2,3\]) // return false |
| :---- |

6. **`Safely access any element in an array without throwing an exception (Swift)`**

`Change the subscript operator. If the index is valid, it should return the element. If the index is invalid, it must return nil.`  
`Example: let array = [1, 2, 3], array[safe: 0] should return 1 ,array[safe: 3] should return nil`

| extension Array {    subscript(safe index: Int) \-\> Element? {        guard index \>= 0 && index \< count else {            return nil        }        return self\[index\]    }}let array \= \[1, 2, 3\]array\[safe: 0\]array\[safe: 3\] |
| :---- |

7. **`Palindrome`**

`Write a function that takes a string as input and returns true if the string is a palindrome, and false otherwise.`  
`Example input: "madam" Example output: true`

| // usar funçao “nativa” func isPalindrome(\_ input: String) \-\> Bool {    return input \== String(input.reversed())}isPalindrome("madam") // return true |
| :---- |

		`Ou: (usando apontadores)`

| func isPalindrome(\_ str: String) \-\> Bool {    let lowercasedStr \= str.lowercased()    var leftIndex \= 0    var rightIndex \= lowercasedStr.count \- 1        while leftIndex \< rightIndex {        let leftChar \= Array(lowercasedStr)\[leftIndex\]        let rightChar \= Array(lowercasedStr)\[rightIndex\]        if leftChar \!= rightChar {            return false        }        leftIndex \+= 1        rightIndex \-= 1    }    return true}isPalindrome("madam") // return true |
| :---- |

		`Ou: (com função recursiva)`

| func isPalindrome4(\_ str: String) \-\> Bool {    // Base case : string vazia ou com 1 caractere é um palindromo    if str.count \<= 1 {        return true    }        let primeiroCaractere \= String(str.prefix(1)) // primeiro caractere    let ultimoCaractere \= String(str.suffix(1)) // ultimo caractere        if primeiroCaractere \== ultimoCaractere {        // cria uma substring (middleString) sem o primeiro e sem o ultimo caractere        let middleString \= String(str.dropFirst().dropLast())        return isPalindrome4(middleString) // função recursiva    } else {        return false    }}isPalindrome4("madam") // return true |
| :---- |

8. **`Anagram`**

`Write a function that takes two strings as input and returns true if the strings are anagrams of each other, and false otherwise.`  
`Example input: "anna", "nana" Example output: true`

| func areAnagrams(\_ str1: String, \_ str2: String) \-\> Bool {    // se os tamanhos das strings são diferentes não são anagramas    if str1.count \!= str2.count {        return false    }    // ordena as strings    let sortedStr1 \= str1.sorted()    let sortedStr2 \= str2.sorted()    // se as strings "ordenadas" são iguais então são anagramas    return sortedStr1 \== sortedStr2}areAnagrams("anna", "nana") // retorna true |
| :---- |

9. **`Caesar Cipher`**

`Write a function that takes a string and an integer as input, and returns the string encrypted using a Caesar cipher with the given shift.`  
`Example input: "hello", 3 Example output: "khoor"`

| func caesarCipher(\_ str: String, \_ shift: Int) \-\> String {    let alphabet: \[Character\] \= \["a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k", "l", "m", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z"\]    var encryptedStr \= ""    for char in str.lowercased() {        let index \= alphabet.firstIndex(of: char)\!        let shiftedIndex \= (index \+ shift) % alphabet.count        encryptedStr.append(alphabet\[shiftedIndex\])    }    return encryptedStr}// Testar a funcaocaesarCipher("hello", 3) |
| :---- |

`Pode ser melhorado com uma função map que vai retornar um Array de caracteres já com o “shift” de posição. Ao fazer cast desse Array para String obtemos a palavra já com “shift”`

| func caesarCipher(\_ str: String, \_ shift: Int) \-\> String {    let alphabet: \[Character\] \= \["a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k", "l", "m", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z"\]    return String(str.lowercased().map { char \-\> Character in        let index \= alphabet.firstIndex(of: char)\!        let shiftedIndex \= (index \+ shift) % alphabet.count        return alphabet\[shiftedIndex\]    })}  |
| :---- |

// Testar a funcao  
caesarCipher("hello", 3)

10. **`Binary Search`**

`Write a function that takes a sorted array of integers and a target value as input, and returns the index of the target value in the array if it exists, and -1 otherwise.`  
`Example input: [1, 2, 3, 4, 5], 3 Example output: 2`

| func binarySearch(\_ array: \[Int\], \_ target: Int) \-\> Int {    var left \= 0    var right \= array.count \- 1    while left \<= right {        let mid \= (left \+ right) / 2        if array\[mid\] \== target {            return mid        } else if array\[mid\] \< target {            left \= mid \+ 1        } else {            right \= mid \- 1        }    }    return \-1}binarySearch(\[1, 2, 3, 4, 5\], 3) // retorna 2 |
| :---- |

11. **`Merge Sort`**

`Write a function that takes an array of integers as input and returns the array sorted using the merge sort algorithm.`  
`Example input: [5, 2, 8, 3, 1] Example output: [1, 2, 3, 5, 8]`

| func mergeSort(\_ array: \[Int\]) \-\> \[Int\] {   // Base case: se o array tem 1 or 0 elementos, já está ordenado    guard array.count \> 1 else { return array }       // encontrar o ponto do meio para dividir o array em 2 metades    let midIndex \= array.count / 2          let leftArray \= Array(array\[0..\<midIndex\]) // metade da esquerda    let rightArray \= Array(array\[midIndex..\<array.count\]) // metade da direita    let sortedLeft \= mergeSort(leftArray)    // ordenar recursivamente esta metade    let sortedRight \= mergeSort(rightArray)  // ordenar recursivamente esta metade    return merge(sortedLeft, sortedRight) // unir as 2 metades ordenadas}func merge(\_ left: \[Int\], \_ right: \[Int\]) \-\> \[Int\] {    var mergedArray \= \[Int\]()    var leftIndex \= 0    var rightIndex \= 0        while leftIndex \< left.count && rightIndex \< right.count { // percorre o left array e faz o append de elementos        if left\[leftIndex\] \< right\[rightIndex\] {            mergedArray.append(left\[leftIndex\])            leftIndex \+= 1        } else { // percorre o right array e faz o append de elementos            mergedArray.append(right\[rightIndex\])            rightIndex \+= 1        }    }        while leftIndex \< left.count {     // faz o append dos restantes elementos ainda presentes no left array        mergedArray.append(left\[leftIndex\])        leftIndex \+= 1    }        while rightIndex \< right.count {     // faz o append dos restantes elementos ainda presentes no right array        mergedArray.append(right\[rightIndex\])        rightIndex \+= 1    }        return mergedArray}mergeSort(\[5, 2, 8, 3, 1\]) // retorna \[1, 2, 3, 5, 8\] |
| :---- |

12. **`Find the First Duplicate`**

`Write a function that takes an array of integers as input and returns the first duplicate value in the array, and -1 if no duplicates exist.`  
`Example input: [1, 2, 3, 4, 5, 2] Example output: 2`

| func findFirstDuplicate(\_ input: \[Int\]) \-\> Int {    var numerosVerificados \= Set\<Int\>()        for numero in input {                if numerosVerificados.contains(numero) {            return numero        } else {            numerosVerificados.insert(numero)        }    }        return \-1}findFirstDuplicate(\[1, 2, 3, 4, 5, 2\]) // return 2 |
| :---- |

13. **`Validate IP Address`**

`Write a function that takes a string as input and returns true if the string is a valid IP address, and false otherwise.`  
`Example input: "192.168.0.1" Example output: true`

| func validateIPAdress(\_ ip: String) \-\> Bool {        let partes \= ip.split(separator: ".")        guard partes.count \== 4 else { return false }        for elemento in partes {                if let numero \= Int(elemento),           numero \>= 0 && numero \<= 255 {            // comparar a representacao String do numero com o numero (Int).            // Se forem diferentes quer dizer que tem um 0 antes. Por ex. "01" vai ser diferente de 1, pois            // a representacao Int de "01" será 1 e não 01\.            if String(numero) \!= elemento {                                return false            }        } else {            return false        }    }        return true}validateIPAdress("192.168.0.1") // return true |
| :---- |

14. **`Binary Gap`**  
    

| Write a function to find the largest gap between the 1's in the binary representation of an integer.Example input: 1041 (binary rep is 10000010001) Example output: 5func binaryGap(\_ input: Int) \-\> Int {        // converter o número para String    let binaryString \= String(input, radix: 2)        // inicializar as variáveis de gap e o index do ultimo 1    var maxGap \= 0    var lastIndexDeUm: Int?        // iterar sobre a string de binário do numero    for (index, char) in binaryString.enumerated() {        // verificar se o char é 1        if char \== "1" {            // se não for o primeiro 1 então calcula o gap            if let lastIndexDeUm {                                maxGap \= max(maxGap, index \- lastIndexDeUm \- 1)            }            lastIndexDeUm \= index        }    }        return maxGap    }binaryGap(1041) // retorna 5 |
| :---- |

15. **`string1 is a subsequence of string2`**

`Write a function that determine if string1 is a subsequence of string2`  
`Example input: ["bolo", "gulosobtberolocreme"] Example output: true`

| public func subStrings(\_ string1: String, \_ string2: String) \-\> Bool {     var i \= 0     var j \= 0    let s1Array \= Array(string1)     let s2Array \= Array(string2)     while i \< s1Array.count && j \< s2Array.count {         if s1Array\[i\] \== s2Array\[j\] {             i \+= 1         }          j \+= 1     }     return i \== s1Array.count }subStrings("bolo", "gulosobtberolocreme") // retorna true |
| :---- |

16. **`Find the Longest Increasing Subsequence`**

`Write a function that takes an array of integers as input and returns the longest increasing subsequence.`  
`Example input: [10, 22, 9, 33, 21, 50, 41, 60, 80] Example output: [10, 22, 33, 50, 60, 80]`

