# Programação Orientada à Objetos

## Classe

Uma classe é um molde (template) para criação de objetos, nela serão definidos **atributos**, que são os dados, e **métodos** onde serão registrados os comportamentos.

~~~java
public class Pessoa {
	...
}
~~~

## Objeto

Um objeto é uma instância de uma classe, armazena um espaço na memória e possui estado e comportamento.

~~~java
public class Main {
	public static void main(String[] args) {
	    Pessoa p1 = new Pessoa();
	}
}
~~~

## Atributos

São variáveis de uma classe que representam o estado do objeto.

~~~java
public class Pessoa {
	int x = 10;
}

public class Main {
	public static void main(String[] args){
		Pessoa p1 = new Pessoa();
		System.out.println(p1.x); //10
	}
}
~~~

## Métodos

Métodos são funções associadas a uma determinada classe, definem o comportamento do objeto.

~~~java
public class Pessoa {
	function void bemvindo(String nome){
		System.out.println("Bem-vindo, " + nome);
	}
}

public class Main {
	public static void main(String[] args){
		Pessoa p1 = new Pessoa();
		p1.bemvindo("Ana"); //Bem-vindo, Ana
	}
}
~~~

## Construtores

Construtores são métodos especiais para inicialização de objetos.

~~~java
public class Pessoa {
	int x;
	public Pessoa(){
		x = 5;
	}
}

public class Main {
	public static void main(String[] args){
		Pessoa p1 = new Pessoa();
		System.out.println(p1.x);//5
	}
}
~~~

## Palavra-chave this

A palavra *this* serve para referenciar o objeto atual

~~~java
public class Pessoa {
	int x;
	public Pessoa(int x){
		this.x = x;
	}
}

public class Main {
	public static void main(String[] args){
		Pessoa p1 = new Pessoa(10);
		System.out.println(p1.x);//10
	}
}
~~~

## Modificadores de Acesso

Controlam o nível de acesso

| modifier  | class  | package | subclass | global |
| :-------: | :----: | :-----: | :------: | :----: |
|  public   | acessa | acessa  |  acessa  | acessa |
| protected | acessa | acessa  |  acessa  |   x    |
|  default  | acessa | acessa  |    x     |   x    |
|  private  | acessa |    x    |    x     |   x    |

## Modificadores que não são de acesso

Não controlam visibilidade, mas adicionam outras características as classes.

### Final

Modifica o atributo para que não possa ocorrer uma sobreescrita.

~~~java
public class Pessoa {
	final int x = 5;
}

public class Main {
	public static void main(String[] args){
		Pessoa p1 = new Pessoa();
		p1.x = 10;//erro
	}
}
~~~

### Static

Quando um atributo ou método recebe o `static` ela pertence a classe, e não ao objeto. Logo, pode ser compartilhado por todos os objetos.

~~~java
public class Pessoa {
	static metodo(){
		System.out.println("Algo estático pode ser chamado sem criar um objeto.");
	}
}

public class Main {
	public static void main(String[] args){
		metodo();
	}
}
~~~

## Abstract

Um método abstract pertence a uma classe abstrata, não possui um "corpo". O corpo será providenciado por uma subclasse.

~~~java
abstract class Pessoa {  
  public abstract void mensagem(); // abstract method
}

//Herança
class Funcionario extends Pessoa {
  public void mensagem() { 
    System.out.println("Mensagem do Funcionário...");
  }
}
~~~

## Encapsulamento

Encapsular os dados significa proteger os dados para que não sejam acessados por qualquer um. Para isso:
- As variáveis e atributos de uma classe devem ser declarados como `private`;
- Os dados devem ser acessados através de métodos `get` e `set`, para retornar ou atualizar uma informação.

~~~java
public class Pessoa {
	private String nome;
	
	public String getNome() {
		return nome;
	}
	
	public String setNome(String nome) {
		this.nome = nome;
	}
}

public class Main {
	public static void main(String[] args){
		Pessoa p1 = new Pessoa();
		p1.setNome("Rui");
	}
}
~~~

## Herança

Conceito necessário para herdar atributos e métodos de outra classe, para isso é necessário que essas classes sejam definidas como "pai" e "filha".
- Uma classe filha é chamada de subclasse, recebe a herança
- Uma classe pai é chamada de superclasse, fornece a herança

No Java essa ligação é atribuída pela palavra `extends`

~~~java
public class Toyota {
	private String empresa = "Toyota";
	public void buzina(){
		System.out.println("Biii-biii!");
	}
	
	public getEmpresa(){
		return empresa;
	}
}

public class Carro extends Toyota {
	private String carro;
	
	public String getCarro() {
		return carro;	
	}
	
	public String setCarro(String carro) {
		this.carro = carro;
	}
}

public class Main {
	public static void main(String[] args) {
		Carro c1 = new Carro();
		c1.setCarro = "Prius";
		c1.getEmpresa(); //Toyota
		c1.buzina();//Biii-biii!
	}
}
~~~

## Polimorfismo

Polimorfismo significa ter muitas formas, ocorre quando tem muitas classes que são relacionadas uma com as outras através de herança, e ocorra ume sobrescrita nas classes filhas.

~~~java
public class Quadrupede {
	private int patas = 4;
	public void som(){
		System.out.println("Grr, grr!");
	}
	
	public int getPatas() {
		return patas;
	}
}

public class Cachorro extends Quadrupede {
	public void som() {
		System.out.println("Au, au!");
	}
}

public class Main {
	public static void main(String[] args) {
		Cachorro c1 = new Cachorro();
		c1.som();//Au, au!
	}
}
~~~

## Palavra-chave super

A palavra-chave `super` é usado para referenciar a classe do pai de uma subclasse. Assim, se tiver um polimorfismo na subclasse, pode-se escolher chamar a o método da superclasse.

~~~java
public class Animal {
  String type = "Animal";
}

public class Cachorro extends Animal {
  String type = "Cachorro";

  public void exibirTipo() {
    System.out.println(super.type);
  }
}

public class Main {
  public static void main(String[] args) {
    Cachorro c1 = new Cachorro();
    c1.exibirTipo();
  }
}
~~~

## Classes Internas

Como acessar classes aninhadas

~~~java
public class Externa {
  int x = 10;

  public class Interna {
    int y = 5;
  }
}

public class Main {
  public static void main(String[] args) {
    Externa e = new Externa();
    Externa.Interna i = Externa.new Interna();
    System.out.println(Interna.y + Externa.x);
  }
}
~~~

## Abstração de Classes e Métodos

Abstração de dados é o processo de esconder certos detalhes e mostrar apenas o essencial para o usuário. Abstração pode ser obtida por classes abstratas ou interfaces.
- **Classe Abstrata:** é uma classe restrita que não pode ser usada para criar objetos diretamente, para acessá-la é necessário o uso da herança.
- **Método Abstrato:** Apenas pode ser usado dentro de uma classe abstrata, não tem corpo, será providenciado através de uma subclasse (fruto de herança).

~~~java
abstract class Animal {
  public abstract void som();
  public void dormir() {
    System.out.println("Zzz");
  }
}

public class Porco extends Animal {
  public void som() {
    System.out.println("Oinc, oinc!");
  }
}

public class Main {
  public static void main(String[] args) {
    Porco p = new Porco();
    p.som();
    p.dormir();
  }
}
~~~

## Interfaces

Outro jeito de obter abstração em Java é através das interfaces, essas interfaces são classes abstratas que armazenam métodos que não possuem corpo, apenas é declarado a sua estrutura.

~~~java
interface Animal {
  public void som();
  public void reproducao();
  public void expectativa();
}
~~~

Para acessar estas interfaces é necessário usar a palavra reservada `implements`.

~~~java
public class Cachorro implements Animal {
	public void som() {
		System.out.println("Au, au!");
	}
	public void reproducao(){
		System.out.println("Cachorro geralmente tem de 1 até 8 filhotes.");
	};
	public void expectativa(){
		System.out.println("Cachorro geralmente vive de 10 até 15 anos.");
	};
}

public class Main {
	public static void main(String[] args) {
		Cachorro c = new Cachorro();
		c.som();
		c.reproducao();
		c.expectativa();
	}
}
~~~

## Classe Anônima

É uma classe que não possui nome, é criada e usada ao mesmo tempo. Pode ser muito utilizada como um jeito rápido para fazer sobrescrita de métodos sem ter a necessidade de criar uma nova classe ou interface. 

~~~java
public class Animal {
  public void som() {
    System.out.println("Grr, grr!");
  }
}

public class Main {
  public static void main(String[] args) {
	  Animal a = new Animal() {
	      public void som() {
	        System.out.println("Miau!");
	      }
    };
    a.som();
  }
}
~~~


## Enums

É uma classe especial para criar uma grupo de constantes, que são variáveis imutáveis como aquelas que são declaradas com a palavra reservada `final`.

~~~java
enum Pais {
	br,
	us,
	es,
	jp,
	it
}

public class Main {
  public static void main(String[] args) {
    Pais p = Pais.br;

    switch(p) {
	    case br:
	        System.out.println("Brasil");
	        break;
	    case us:
	        System.out.println("Estados Unidos da América");
	        break;
	    case es:
	        System.out.println("Espanha");
	        break;    
	    case jp:
		    System.out.println("Japão");
	        break;
		case it:
	        System.out.println("Itália");
	        break;
	    default:
		    System.out.println("Nenhum");
    }
  }
}
~~~

Enums também pode ter construtores, o construtor é chamado automaticamente quando a constante é criada.

~~~java
enum Time {
  BFR("Botafogo de Futebol e Regatas"),
  CRF("Clube de Regatas do Flamengo"),
  FFC("Fluminense Football Club"),
  CRVG("Clube de Regatas Vasco da Gama"),
  CBF("Confederação Brasileira de Futebol");

  private String nome;

  private Time(String nome) {
    this.nome = nome;
  }
  
  public String getNome() {
    return nome;
  }
}

public class Main {
  public static void main(String[] args) {
    Time t = Time.BFR; 
    System.out.println(t.getNome()); //Botafogo de Futebol e Regatas
  }
}
~~~