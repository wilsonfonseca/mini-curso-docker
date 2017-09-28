!SLIDE center transition=scrollUp

# Kubernetes no Hackaday
![kubernetes](images/kubernetes-me.png)

!SLIDE transition=scrollUp
# Overview

### Partindo da concepção de seu projeto e chegando a execução no hackaday sem se preocupar com infraestrutura;

- O [Kubernetes](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/) é uma plataforma open-source para automação de deployment, scaling e gerenciamento centralizado de containers;

- O Projeto foi originalmente desenvolvido pela Google e posteriormente cedido a [Cloud Native Computing Foundation](https://www.cncf.io/);

!SLIDE transition=scrollUp
# Kubernete no UOL

A implementação do Kubernetes no UOL foi iniciada em 2016, atualmente o projeto disponibiliza os seguintes recursos:

- Auto Scalling;
- DNS automático;
- Load Balancer;
- ACL automática (o responsável libera seus acessos);
- Proxy HTTP para internet;
- Controle de acesso baseado em roles;
- Autenticação via Token;
- Registry interno para gerenciamento de imagens;
- Grafana;
- Kibana (retenção de 7 dias);
- Prometheus (retenção de 30 dias);
- Kubernetes DashBoard (Read only);
- Quotas de consumo;
- Scan de vulnerabilidades;

!SLIDE transition=scrollUp

# Por onde começar?

Pensando no Hackaday o ideal é entender qual o mínimo necessário para viabilizar o teste de cada projeto;

Esse "mínimo" seria composto pelo seguinte: 

- Criação de containers; 
- Armazenamento no Registry;
- Criação do projeto no Kubernetes com VIP;
- Acesso garantido para conexões com a rede de Staging e QA;

Para isso separamos essa informação em três passos simples:

1. Docker;
2. Kubernetes;
3. Debbuging;