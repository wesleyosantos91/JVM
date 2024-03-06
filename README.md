<div align="center">

  <img src="assets/logo.png" alt="logo" width="200" height="auto" />
  <h1>JVM</h1>
  
<!-- Badges -->
<p>
  <a href="https://github.com/wesleyosantos91/JVM/graphs/contributors">
    <img src="https://img.shields.io/github/contributors/wesleyosantos91/JVM" alt="contributors" />
  </a>
  <a href="">
    <img src="https://img.shields.io/github/last-commit/wesleyosantos91/JVM" alt="last update" />
  </a>
  <a href="https://github.com/wesleyosantos91/JVM/network/members">
    <img src="https://img.shields.io/github/forks/wesleyosantos91/JVM" alt="forks" />
  </a>
  <a href="https://github.com/wesleyosantos91/JVM/stargazers">
    <img src="https://img.shields.io/github/stars/wesleyosantos91/JVM" alt="stars" />
  </a>
  <a href="https://github.com/wesleyosantos91/JVM/issues/">
    <img src="https://img.shields.io/github/issues/wesleyosantos91/JVM" alt="open issues" />
  </a>
  <a href="https://github.com/wesleyosantos91/JVM/pulls/">
    <img src="https://img.shields.io/github/issues-pr/wesleyosantos91/JVM" alt="pull requests" />
  </a>
  <a href="https://github.com/wesleyosantos91/JVM/blob/main/LICENSE">
    <img src="https://img.shields.io/github/license/wesleyosantos91/JVM" alt="license" />
  </a>
</p>
   
<br />
</div>

<!-- About the Project -->
## :star2: Sobre o projeto:
<p>
    Este repositório destina-se a fornecer recursos e exemplos para estudar e entender a Máquina Virtual Java (JVM).</br>
    A JVM é um componente essencial da plataforma Java e é responsável por executar programas Java compilados em bytecode.
</p>

<!-- Screenshots -->
### :camera: Memória JVM:

<div align="center"> 
  <img src="assets/00-jvm-memoria.png" alt="logo" width="600" height="auto" />
</div>

#### Stack:
> A memória da pilha (stack) é usada para armazenar dados locais e referências a objetos para cada método em execução na JVM. Cada thread possui sua própria pilha de execução, onde são mantidos os registros de ativação e as variáveis locais. As variáveis locais e referências a objetos são removidas automaticamente quando o método é concluído, o que torna a memória da pilha eficiente para gerenciamento de memória temporária e rápida alocação e desalocação de recursos.
> - Área de memória usada para armazenar variáveis locais e informações de chamada de método.
> - Cada thread possui sua própria stack, que cresce e diminui à medida que métodos são chamados e retornados.
> - Armazena tipos de dados primitivos (int, float, etc.) e referências a objetos.
> - Tamanho geralmente menor que o heap.

> Exemplo de configuração da memória Stack:
<br> obs: essa configuração normalmente não é utilizada.

```bash
  java -Xss1m Main.java
```

Neste exemplo, -Xss1m define o tamanho da pilha como 1 megabyte. Você pode substituir 1m pelo tamanho desejado em megabytes.

#### Heap:
> O heap é a área de memória compartilhada entre todas as threads em uma aplicação Java, utilizada para armazenar objetos e arrays dinamicamente alocados. Ele é gerenciado pelo coletor de lixo (GC) da JVM, que é responsável por liberar a memória de objetos não utilizados para evitar vazamentos de memória. O heap é dividido em duas partes principais: a geração nova (young generation) e a geração antiga (old generation), que são utilizadas para otimizar o processo de coleta de lixo.
> - Área de memória usada para alocar objetos dinamicamente.
> - Compartilhado por todas as threads da aplicação.
> - Gerenciado pelo coletor de lixo.
> - Tamanho pode ser configurado e ajustado.

> Exemplo de configuração da memória Heap:

```bash
  java -Xms128m -Xmx512m Main.java
```

-Xms e -Xmx são parâmetros de linha de comando usados para especificar o tamanho inicial e máximo da memória alocada para a JVM (Java Virtual Machine).

-Xms: Este parâmetro especifica o tamanho inicial da memória que será alocada para o heap da JVM no momento em que a JVM é iniciada. Por exemplo, se você definir -Xms512m, isso significa que a JVM será iniciada com 512 megabytes de memória alocada para o heap.

-Xmx: Este parâmetro especifica o tamanho máximo da memória que a JVM pode alocar para o heap durante a execução do programa. Se você definir -Xmx1024m, isso significa que a JVM pode alocar até 1024 megabytes de memória para o heap durante a execução do programa.

#### Metaspace:
> A Metaspace é uma área de memória na JVM que substitui permanentemente a área de PermGen (geração permanente) nas versões mais recentes do Java. Ela é responsável por armazenar metadados relacionados a classes, como informações sobre classes carregadas, métodos, constantes e estruturas de dados internas da JVM. Ao contrário da PermGen, a Metaspace é dimensionada dinamicamente pela JVM e pode crescer ou diminuir conforme a necessidade, o que reduz a probabilidade de erros de alocação de memória relacionados à área de metadados.
> - Introduzido na versão 8 do Java.
> - Substituiu o PermGen.
> - Armazena metadados da JVM, como classes, métodos e strings.
> - Tamanho não é fixo e pode crescer dinamicamente.
> - Monitoramento de uso é importante para evitar OutOfMemoryError.

> Exemplo de configuração da memória Metaspace:
<br> obs: essa configuração normalmente não é utilizada.

```bash
  java -XX:MaxMetaspaceSize=256m Main.java
```

### GC - Garbage Collection (Coletor de lixo)

> O Garbage Collection (GC) é um processo automático da JVM (Java Virtual Machine) responsável por identificar e liberar memória de objetos que não estão mais sendo utilizados pela aplicação. Isso evita vazamentos de memória, que podem levar a problemas de desempenho e estabilidade.

#### O que GC pode evitar:

##### Memory Leak:
> Imagine que você tem uma torneira que fica pingando água constantemente, mas você nunca fecha. Com o tempo, a água vai se acumulando e eventualmente transborda, causando desperdício. Da mesma forma, um "memory leak" ocorre quando um programa continua alocando memória sem liberá-la, o que pode levar a problemas de desempenho ou até mesmo ao travamento do programa.

##### Dangling Pointer:
> Agora, imagine que você anote o endereço de um lugar em um papel, mas esse lugar é demolido antes que você tenha a chance de usá-lo. Se você olhar para o papel, você ainda terá o endereço, mas ele não leva a lugar nenhum. Isso é como um "dangling pointer", que ocorre quando um programa usa um endereço de memória que já foi liberado, resultando em comportamento imprevisível ou até mesmo falhas.

#### Tipos de algoritimos GC:

##### Java 8
- Parallel GC (default)
  - Projetado para alto rendimento (throughput) em sistemas multiprocessados
  - Divide o heap em regiões e coleta cada região em paralelo usando várias threads.
  - Adequado para aplicações que necessitam de alto throughput e não sofrem muito com pausas curtas na garbage collection.
- Serial GC
  - Coletor de lixo mais simples, utiliza apenas uma thread.
  - Adequado para aplicações single-threaded ou com recursos limitados, pois tem baixo overhead.
- CMS GC
  - Coletor de lixo "concurrent", permitindo que a aplicação continue executando durante a coleta de lixo.
  - Minimiza o tempo de parada da aplicação, mas pode ter um impacto maior no rendimento geral.
  - Adequado para aplicações sensíveis à latência que necessitam de pausas curtas e previsíveis na garbage collection.

> Exemplo usando o Parallel GC:

```bash
  java -XX:+UseSerialGC Main
```

> Exemplo usando o Serial GC:

```bash
  java -XX:+UseSerialGC Main
```

> Exemplo usando o CMS GC:

```bash
  java -XX:+UseConcMarkSweepGC Main
```

##### Java 11
- G1 GC (default)
  - Coletor de lixo de última geração, oferecendo melhor performance e escalabilidade.
  - Divide o heap em regiões de diferentes tamanhos e coleta cada região de forma independente.
  - Adapta-se dinamicamente às necessidades da aplicação, priorizando regiões com maior probabilidade de conter objetos inutilizados.
  - Adequado para uma ampla gama de aplicações, desde aplicações single-threaded até aplicações multiprocessadas com cargas de memória variáveis.
- Serial GC
  - (Mesma descrição do Java 8)
- Shenandoah GC (experimental)
  - Coletor de lixo experimental projetado para aplicações com grandes conjuntos de dados.
  - Utiliza um algoritmo de "copying", copiando objetos sobreviventes para uma nova região do heap e liberando a memória da região antiga.
  - Pode ser benéfico para aplicações que alocam e desalocam grandes quantidades de dados, mas pode ter um overhead maior em comparação ao G1 GC.
- ZGC (experimental)
  - Coletor de lixo experimental focado em baixa latência.
  - Utiliza um algoritmo de "region-based memory management", gerenciando o heap em regiões e coletando cada região individualmente.
  - Projetado para minimizar o tempo gasto em pausas durante a coleta de lixo, geralmente abaixo de 1 milissegundo.
  - Adequado para aplicações críticas à latência, como sistemas em tempo real ou processamento de alta frequência, mas requer testes rigorosos devido ao seu estado experimental.

> Exemplo usando o G1 GC:

```bash
  java -XX:+UseG1GC Main
```

> Exemplo usando o Shenandoah GC (experimental):

```bash
  java -XX:+UseShenandoahGC Main
```

> Exemplo usando o ZGC (experimental):

```bash
  java -XX:+UseZGC Main
```

##### Java 17
- G1 GC (default)
  - (Mesma descrição do Java 11)
- Serial GC
  - (Mesma descrição do Java 8)
- Shenandoah GC (experimental)
  - (Mesma descrição do Java 11)
- ZGC (experimental)
  - (Mesma descrição do Java 11)

##### Java 21
- G1 GC (default)
  - (Mesma descrição do Java 11)
- Serial GC
  - (Mesma descrição do Java 8)
- Shenandoah GC (experimental)
  - (Mesma descrição do Java 11)
- ZGC (experimental)
  - (Mesma descrição do Java 11)

