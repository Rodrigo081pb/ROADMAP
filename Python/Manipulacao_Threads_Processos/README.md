## Manipulação de Threads e Processos

- Conceitos Fundamentais

### 1.1 Concorrência vs Paralelismo

- Concorrência: Vários trechos de código podem ser executados em períodos sobrepostos timpo o time.sleep(tempo em número), mas não necessariamente ao mesmo tempo (depende de como o SO gerencia).

- Paralelismo: Vários trechos de código são executados exatamente ao mesmo tempo (requer múltiplos núcleos de CPU ou múltiplas máquinas).

### 1.2 O que é a Global Interpreter Lock?

- O é um mecanismo do interpretador CPython que permite apenas uma thread executar código Python de cada vez.

- Isso quer dizer que, mesmo com múltiplas threads, só uma delas consegue rodar instruções de Python num momento específico.

- Para tarefas I/O-bound (que passam muito tempo esperando rede, disco etc.), as threads podem ser vantajosas.

- Para tarefas CPU-bound (que usam muito processamento), o paralelismo com threads é limitado pela GIL. Nesse caso, a multiprocessing (vários processos) é mais interessante.

### 2.0 Sincronização de Threads

Quando threads compartilham recursos (variáveis, dados, arquivos), pode rolar concorrência e resultados inesperados. Pra evitar isso, usamos mecanismos de sincronização.

### 2.1 Pool de Threads (ThreadPoolExecutor)

- Pra gerenciar um grande número de tarefas em paralelo, o ThreadPoolExecutor (do módulo concurrent.futures) simplifica a criação e controle de múltiplas threads.