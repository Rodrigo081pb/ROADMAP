# Kubernets

- O que são Kubernetes ? 

    - É um orquestrador de containers open-source criado pela google

    - Ele serve para gerenciar o deploy, escalonamento, balanceamento de carga, atualizações e muito mais.

    - Em produção, Docker e Kubernetes costumam andar juntos (Apesar de existirem outras runtimes de containers compatíveis com o kubernetes)

## Arquiteturas do Kybernetes

- Cluster: Conjunto de máquinas (nodes) onde o Kubernetes distribui a carga.

- Master node (Control Plane): Composto pelo API Server, etcd (banco de dados de estado), Schedule(agendador (decide em qual node colocar o container)), e Controller Manager (Lida com replicação, controle de pods, etc)

- Worker Nodes: Onde os containers (pods) rodam de fato. Cada Worker node tem:
    - Kubelet : agente que conversa com o API Server.
    - Container Runtime (Docker, Containerd, etc.)
    - Kube Proxy: Gerencia a rede dos pods.

### Principal Objetos do Kubernets

- Pod: a menor unidade de deployment no Kubernetes. Geralmente tem um container ou um grupo pequeno de containers que precisam ficar juntos.

- ReplicaSet: garante que um número específico de réplicas de um pod esteja rodando.

- Deployment: gerencia ReplicaSets e atualizações de versão de forma declarativa.

- Service: provê um endpoint (um IP virtual e DNS) pra um conjunto de Pods, permitindo balanceamento de carga interno.

- Ingress: expõe serviços pra fora do cluster por HTTP/HTTPS.

- ConfigMap e Secret: gerenciam configurações e credenciais, respectivamente, de forma separada dos pods.

- PersistentVolume (PV) e PersistentVolumeClaim (PVC): tratam de armazenamento persistente de dados.