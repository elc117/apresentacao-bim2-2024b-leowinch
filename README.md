
# AnotherThreadRace

## Atividade da aula 21

Copie o programa [ThreadRace.java](https://raw.githubusercontent.com/AndreaInfUFSM/elc117-2024b/main/classes/21/src/ThreadRace.java) para um arquivo nomeado AnotherThreadRace.java e renomeie a classe principal para AnotherThreadRace.  

Acrescente uma terceira classe de animal à corrida e ajuste o método main para executar o novo animal em uma nova thread. Para isso, você poderá criar uma classe derivada de Thread (como foi feito na classe Rabbit) ou implementar a interface Runnable (como foi feito na classe Turtle).


### Conteúdo de ThreadRace.java

```java
class Rabbit extends Thread {
	private String name;

	public Rabbit(String name) {
		this.name = name;
	}

	private void runLikeRabbit() {
		System.out.println(name + " is running fast");
	}

	public void run() {
		System.out.println(name + " rabbit is at the start of the race!");
		for (int pos = 10; pos > 0; pos--) {
			runLikeRabbit();
			System.out.println(name + " is at position " + pos);
		}
		System.out.println(name + " rabbit finished the race!");
	}
}

class Turtle implements Runnable {
	private String name;

	public Turtle(String name) {
		this.name = name;
	}

	private void runLikeTurtle() {
		System.out.println(name + " is running slow");
	}

	public void run() {
		System.out.println(name + " turtle is at the start of the race!");
		for (int pos = 10; pos > 0; pos--) {
			runLikeTurtle();
			System.out.println(name + " is at position " + pos);
		}
		System.out.println(name + " turtle finished the race!");

	}
}

class ThreadRace {
	public static void main(String[] args) {
		Rabbit r = new Rabbit("Snowball");
		Thread t = new Thread(new Turtle("Donatello"));
		r.start();
		t.start();
	}
}
```

### Nova classe de animal adicionada:

```java
class Dog implements Runnable {
    private String name;

    public Dog(String name) {
        this.name = name;
    }

    private void runLikeDog() {
        System.out.println(name + " is running energetically");
    }

    public void run() {
        System.out.println(name + " dog is at the start of the race!");
        for (int pos = 10; pos > 0; pos--) {
            runLikeDog();
            System.out.println(name + " is at position " + pos);
        }
        System.out.println(name + " dog finished the race!");
    }
}
```


### Mudança no método main

```java
class AnotherThreadRace {
    public static void main(String[] args) {
        Rabbit r = new Rabbit("Snowball");
        Thread t = new Thread(new Turtle("Donatello"));
        Thread d = new Thread(new Dog("Poeira")); // Nova Thread para Dog
        r.start();
        t.start();
        d.start(); // chamada do método start para Dog
    }
}
```

### Exemplos de saída:

#### Exemplo 1:
```
Donatello turtle is at the start of the race!
Snowball rabbit is at the start of the race!
Donatello is running slow
Poeira dog is at the start of the race!
Snowball is running fast
Poeira is running energetically
Snowball is at position 10
Snowball is running fast
Donatello is at position 10
Donatello is running slow
Donatello is at position 9
Donatello is running slow
Donatello is at position 8
Donatello is running slow
Donatello is at position 7
Donatello is running slow
Poeira is at position 10
Poeira is running energetically
Poeira is at position 9
Poeira is running energetically
Poeira is at position 8
Poeira is running energetically
Poeira is at position 7
Poeira is running energetically
Snowball is at position 9
Snowball is running fast
Donatello is at position 6
Donatello is running slow
Donatello is at position 5
Donatello is running slow
Donatello is at position 4
Donatello is running slow
Donatello is at position 3
Donatello is running slow
Donatello is at position 2
Poeira is at position 6
Poeira is running energetically
Poeira is at position 5
Snowball is at position 8
Snowball is running fast
Donatello is running slow
Donatello is at position 1
Poeira is running energetically
Poeira is at position 4
Donatello turtle finished the race!
Snowball is at position 7
Snowball is running fast
Snowball is at position 6
Snowball is running fast
Poeira is running energetically
Poeira is at position 3
Poeira is running energetically
Snowball is at position 5
Snowball is running fast
Snowball is at position 4
Snowball is running fast
Snowball is at position 3
Poeira is at position 2
Poeira is running energetically
Poeira is at position 1
Snowball is running fast
Snowball is at position 2
Snowball is running fast
Snowball is at position 1
Poeira dog finished the race!
Snowball rabbit finished the race!
```

#### Exemplo 2:

```
Donatello turtle is at the start of the race!
Poeira dog is at the start of the race!
Snowball rabbit is at the start of the race!
Donatello is running slow
Poeira is running energetically
Snowball is running fast
Poeira is at position 10
Poeira is running energetically
Snowball is at position 10
Snowball is running fast
Snowball is at position 9
Snowball is running fast
Snowball is at position 8
Snowball is running fast
Donatello is at position 10
Donatello is running slow
Poeira is at position 9
Poeira is running energetically
Snowball is at position 7
Snowball is running fast
Snowball is at position 6
Snowball is running fast
Snowball is at position 5
Snowball is running fast
Donatello is at position 9
Donatello is running slow
Poeira is at position 8
Poeira is running energetically
Poeira is at position 7
Poeira is running energetically
Snowball is at position 4
Snowball is running fast
Donatello is at position 8
Donatello is running slow
Donatello is at position 7
Donatello is running slow
Poeira is at position 6
Poeira is running energetically
Poeira is at position 5
Poeira is running energetically
Poeira is at position 4
Poeira is running energetically
Poeira is at position 3
Poeira is running energetically
Poeira is at position 2
Snowball is at position 3
Snowball is running fast
Snowball is at position 2
Snowball is running fast
Snowball is at position 1
Donatello is at position 6
Poeira is running energetically
Snowball rabbit finished the race!
Donatello is running slow
Donatello is at position 5
Donatello is running slow
Donatello is at position 4
Donatello is running slow
Donatello is at position 3
Donatello is running slow
Donatello is at position 2
Donatello is running slow
Donatello is at position 1
Poeira is at position 1
Donatello turtle finished the race!
Poeira dog finished the race!
```

### Conclusão:

É possível perceber o **não-determinismo** na execução desse programa devido a execução concorrente, onde as corridas são realizadas em threads separadas, fazendo com que cada execução gere uma sáida em ordem diferente e exista uma incerteza na execução, mesmo a lógica estando correta.

### Referências:
[Material da disciplina](https://github.com/andreaInfUFSM/elc117-2024b?tab=readme-ov-file)


