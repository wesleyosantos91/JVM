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
## :star2: Sobre o projeto
<p>
    Este repositório destina-se a fornecer recursos e exemplos para estudar e entender a Máquina Virtual Java (JVM).</br>
    A JVM é um componente essencial da plataforma Java e é responsável por executar programas Java compilados em bytecode.
</p>

<!-- Screenshots -->
### :camera: Memória JVM

<div align="center"> 
  <img src="assets/00-jvm-memoria.png" alt="logo" width="600" height="auto" />
</div>

### Stack
> A memória da pilha (stack) é usada para armazenar dados locais e referências a objetos para cada método em execução na JVM. Cada thread possui sua própria pilha de execução, onde são mantidos os registros de ativação e as variáveis locais. As variáveis locais e referências a objetos são removidas automaticamente quando o método é concluído, o que torna a memória da pilha eficiente para gerenciamento de memória temporária e rápida alocação e desalocação de recursos.
> - Área de memória usada para armazenar variáveis locais e informações de chamada de método.
> - Cada thread possui sua própria stack, que cresce e diminui à medida que métodos são chamados e retornados.
> - Armazena tipos de dados primitivos (int, float, etc.) e referências a objetos.
> - Tamanho geralmente menor que o heap.

### Heap

> O heap é a área de memória compartilhada entre todas as threads em uma aplicação Java, utilizada para armazenar objetos e arrays dinamicamente alocados. Ele é gerenciado pelo coletor de lixo (GC) da JVM, que é responsável por liberar a memória de objetos não utilizados para evitar vazamentos de memória. O heap é dividido em duas partes principais: a geração nova (young generation) e a geração antiga (old generation), que são utilizadas para otimizar o processo de coleta de lixo.
> - Área de memória usada para alocar objetos dinamicamente.>
> - Compartilhado por todas as threads da aplicação.
> - Gerenciado pelo coletor de lixo.
> - Tamanho pode ser configurado e ajustado.


### Metaspace
> A Metaspace é uma área de memória na JVM que substitui permanentemente a área de PermGen (geração permanente) nas versões mais recentes do Java. Ela é responsável por armazenar metadados relacionados a classes, como informações sobre classes carregadas, métodos, constantes e estruturas de dados internas da JVM. Ao contrário da PermGen, a Metaspace é dimensionada dinamicamente pela JVM e pode crescer ou diminuir conforme a necessidade, o que reduz a probabilidade de erros de alocação de memória relacionados à área de metadados.
> - Introduzido na versão 8 do Java.
> - Substituiu o PermGen.
> - Armazena metadados da JVM, como classes, métodos e strings.
> - Tamanho não é fixo e pode crescer dinamicamente.
> - Monitoramento de uso é importante para evitar OutOfMemoryError.