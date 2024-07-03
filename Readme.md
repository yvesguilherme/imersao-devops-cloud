# DevOps 4 devs

Repositório que contém o conteúdo do evento DevOps 4 devs

![Logo devops4devs](https://events-fullcycle.s3.amazonaws.com/events-fullcycle/media/images/2f1208672dd84cc694ea273caec51b36.png)

## Anotações

- Control Plane
  - Api server: Ponto central de comunicação com o kubernetes.
  - ETCD: Banco chave/valor onde todas as informações do kubernetes são armazenadas nele (não é acessado direto, precisa ser acessado com o Api server).
  - Scheduler: Responsável por receber todas as especificações de containers que eu quero executar no cluster e definir aonde será executado.
  - Controller manager: Centralizador dos controladores do kubernetes
  - Cloud controller manager: Faz a comunicação do cluster kubernetes com recursos do cloud provider

- Worker Node
  - Kube proxy: Faz toda a comunicação de rede com o cluster kubernetes
  - Kubelet: Responsável por garantir a execução dos containers
    - Ele que comunicará com o container runtime para garantir a execução dos containers 

- Pod
  - Menor objeto dentro do cluster kubernetes
  - É nele que é executado os containers
  - Dentro do pod pode haver um ou mais containers
  - Todos os containers compartilham endereço de rede dentro do cluster kubernetes, sistema de arquivos, etc.
- ReplicaSet
  - Gerencia a execução dos pods
  - Garantir que a quantidade de réplicas especificadas de um determinado pod será garantida em execução no ambiente
  - Escalabilidade e resiliência é garantida quando se tem o replicaSet
- Deployment
  - Gerencia os replicaSets
  - Quando há uma nova versão do pod, ele cria outro replicaSet e não apaga o antigo, pois caso ocorra algum erro, os pods podem ser gerenciados no replicaSet anterior
- Labels e Selectors
  - Label
    - Elemento chave/valor que marca o objeto no cluster kubernetes
      - ex.: LABEL { app: web-color, versao: v2, ambiente: homolog }
  Selector
    - É a seleção de objetos baseada em algumas labels
        - ex.: SELECTOR { app: web-color, versao: v2, ambiente: homolog }
- Service
  - Ponto único de comunicação de uma aplicação e faz o balanceamento de réplicas caso haja mais de uma
  - Ex.: Endereço para que uma aplicação B se comunique com a aplicação A
    - Tipos
      - ClusterIP: Ponto único de comunicação com os pods mas internamente no cluster kubernetes (se quer acessar os pods internamente no cluster kubernetes)
      - NodePort: Cria um acesso externo para os pods, assim você consegue acessar fora do cluster. **Ele faz o acesso externo de uma maneira específica, elegendo uma porta que esteja entre o range 30000-32767**
      - LoadBalancer: Cria um loadBalancer do cloud provider e expõe um ip público