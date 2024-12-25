# **O que aprendi ao criar meu primeiro aplicativo de console em C#: o guia (não tão sério) para entender C#**  

Quando comecei a criar o "Screen Sound", achei que seria simples: “vou só registrar umas bandas, calcular umas médias, exibir uns menus... moleza!”. Mas C# me mostrou que é muito mais do que isso. Então, pegue sua xícara de café e venha comigo explorar os conceitos do C# de um jeito descontraído, mas cheio de exemplos e explicações.  

---

## **1. Tipagem em C#: o guia para não deixar o compilador bravo**  

C# é uma linguagem **fortemente tipada**, o que significa que você precisa dizer exatamente que tipo de dado está lidando. Por exemplo:  

```csharp
string mensagemDeBoasVindas = "Boas-vindas ao Screen Sound";
int nota = 5;
bool bandaRegistrada = true;
```

### **O que está acontecendo aqui?**
- `string`: Representa textos (letras, palavras, ou até mesmo um manifesto de 200 páginas, se você quiser).  
- `int`: Representa números inteiros.  
- `bool`: Representa um valor booleano (`true` ou `false`), perfeito para aquelas perguntas de "sim ou não".  

**Se você errar a tipagem, o compilador vai reclamar.** E quando o compilador reclama, você para tudo e arruma.  

#### Exemplo de erro:
```csharp
int numero = "não sou um número"; // Isso vai explodir seu código.  
```

---

## **2. Funções: o C# gosta de ordem e separação de tarefas**  

Funções são como pequenos trabalhadores do seu código. Elas fazem uma coisa, fazem bem (ou pelo menos deveriam) e voltam para casa.  

Aqui está uma função que exibe um título no console:  

```csharp
void ExibirTitulo(string titulo)
{
    string asteriscos = new string('*', titulo.Length);
    Console.WriteLine(asteriscos);
    Console.WriteLine(titulo);
    Console.WriteLine(asteriscos);
}
```

### **O que aprendemos aqui?**
- `void`: Indica que a função não retorna nada. Ela faz o trabalho e não te entrega nada de volta.  
- `string titulo`: Isso é um **parâmetro**, ou seja, o que você passa para a função trabalhar.  

#### Exemplo de uso:
```csharp
ExibirTitulo("Bem-vindo ao meu aplicativo!");
```

Saída no console:
```
***********************
Bem-vindo ao meu aplicativo!
***********************
```

**Nota pessoal:** Funções bem nomeadas evitam que você volte ao código e pense: "Por que diabos escrevi isso?".  

---

## **3. Dicionários: a melhor invenção depois da pizza**  

Dicionários em C# são como listas, mas com esteroides. Eles guardam dados em pares de **chave-valor**.  

Exemplo do meu código:  

```csharp
Dictionary<string, List<int>> bandasRegistradas = new Dictionary<string, List<int>>();

// Adicionando bandas
bandasRegistradas.Add("Metallica", new List<int> { 5, 4, 3 });
bandasRegistradas.Add("Manoel Gomes", new List<int>());
```

### **O que está rolando aqui?**
- `Dictionary<string, List<int>>`: Um dicionário onde:
  - A chave é uma `string` (o nome da banda).
  - O valor é uma lista de notas (`List<int>`).  
- `.Add()`: Adiciona um novo par chave-valor ao dicionário.  

#### Como acessar os dados:
```csharp
List<int> notas = bandasRegistradas["Metallica"];
Console.WriteLine($"Notas da banda Metallica: {string.Join(", ", notas)}");
```

Saída no console:
```
Notas da banda Metallica: 5, 4, 3
```

---

## **4. Laços (`for`, `foreach`, `while`): porque ninguém quer fazer tudo manualmente**  

Laços (ou loops) são úteis quando você precisa repetir algo. Em vez de escrever `Console.WriteLine` 500 vezes, você usa um laço para economizar tempo (e sanidade).  

Exemplo de um `foreach` no meu código:  

```csharp
foreach (string banda in bandasRegistradas.Keys)
{
    Console.WriteLine($"Banda registrada: {banda}");
}
```

### **O que acontece aqui?**
- `foreach`: Percorre todos os elementos de uma coleção (neste caso, as chaves do dicionário).  
- `bandasRegistradas.Keys`: Retorna todas as chaves do dicionário.  

#### Saída no console:
```
Banda registrada: Metallica
Banda registrada: Manoel Gomes
```

---

## **5. Validação: porque o usuário adora quebrar seu programa**  

Se você não validar as entradas do usuário, alguém vai digitar algo como "Banana" em um campo de notas. Para evitar isso, fiz verificações:  

```csharp
bool VerificaBanda(string nomeBanda)
{
    if (!bandasRegistradas.ContainsKey(nomeBanda))
    {
        Console.WriteLine($"A banda {nomeBanda} não está registrada!");
        return false;
    }
    return true;
}
```

### **Como funciona?**
- `ContainsKey`: Verifica se uma chave existe no dicionário.  
- `return`: Interrompe a execução e devolve o resultado da validação (`true` ou `false`).  

#### Exemplo de uso:
```csharp
if (VerificaBanda("Metallica"))
{
    Console.WriteLine("A banda existe! Vamos avaliá-la.");
}
```
---
### **Conclusão**  

Criar um aplicativo de console em C# foi mais do que apenas escrever código. Foi sobre entender como organizar ideias, estruturar dados e tratar cada detalhe com carinho.  😉
