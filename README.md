# `Test Incognia`

### Segue abaixo, todas as respostas para o teste do processo seletivo para Analista.

#### 1. Descreva os protocolos envolvidos e como são utilizados quando eu abro o navegador e acesso a página www.google.com. Não é necessário descrever os protocolos abaixo da camada de transporte e caso exista mais de uma opção de protocolo em alguma etapa, opte por uma e comente brevemente sua escolha. 

R- Ao acessar-mos uma página web como por exemplo www.google.com.br acontece por trás uma comunicação muito bem cadenciada, e regulada por uma pilha de protocolos (TCP/IP) que é baseada no modelo padrão (OSI) e quem permite hoje todas as comunicações entre hosts e servidores espalhados na internet. 
No primeiro momento, tudo começa na camada 5 do TCP/IP, onde existem vários protocolos dependendo de qual seja o serviço, e no caso do acesso a uma página web, são utilizados os protocolos HTTP e HTTPS.  Ao ser executado um comando conhecido como GET, o Host solicita a página ao server através do protocolo HTTP na camada 5 de aplicação. Esses dados são encapsulados e “transferidos” para camada 4 de transporte. Na camada de transporte, o datagrama recebe um cabeçalho contendo as portas de origem e portas de destino e é definido qual protocolo de transporte será utilizado na comunicação, onde os principais são os TCP e UDP. O protocolo TCP é um protocolo confiável e seguro, o qual garante que uma conexão entre cliente e servidor seja estabelecida (utilizando o 3-way-handshake) antes de começar uma troca de dados. O UDP não estabelece essa conexão e envia os pacotes mesmo sem ter certeza de que algum host vai receber de fato. Dessa forma o UDP passa a ser um protocolo mais rápido, o qual sempre vai ser escolhido quando se trata de aplicações que são toleráveis a erros, como por exemplo um VoIP ou streaming. Para um acesso a um site como do google, escolho os protocolos HTTPS, por ter uma camada de segurança a mais sobre o HTTP, e o TCP, por ter uma garantia na conexão e uma confiança na integridade dos dados, essenciais para o funcionamento de uma página web.
 
#### 2. Como funciona o 3-way-handshake?

R- O 3-way-handshake é uma característica do protocolo TCP, a qual garante e estabelece uma conexão entre um cliente e um servidor. Essa conexão acontece através de 3 comandos que acontecem antes do envio de fato dos dados. Funciona da seguinte forma:

Cliente           Servidor
SYN->  
	          <-SYN, ACK
ACK->

Dados
Dados
Dados

FIN->   
	         <-ACK
	         <-FIN
ACK->

A primeira parte é onde acontece a conexão em si em 3 passos, onde o cliente começa uma conversa solicitando assim a conexão, logo após começa a troca de dados em si, e a parte final é onde a conexão é finalizada, e aí pode ser finalizada tanto pelo cliente quanto pelo server.


#### 3. Quais as diferenças e particularidades do TCP e UDP e quais os usos de cada um?

R-
O TCP e UDP são protocolos de camada 4 da pilha TCP/IP,  e tem como função determinar a forma em que os pacotes serão transportados pela rede, porém cada um com suas peculiaridades.
O TCP é um protocolo orientado por conexão, ou seja, ele garante que a conexão vai ser estabelecida, antes de enviar os pacotes de dados. É um protocolo que trás confiabilidade, ou seja ele grante que os pacotes chegarão íntegros no seu destino. A forma de transmissão do mesmo é Full-Duplex, onde a comunicação pode ocorrer de ambos os lados ao mesmo tempo. Além disso, ele garante que os dados chegarão de forma ordenada, pois cada pacote que é gerado, possui um número sequencial E um dos principais pontos do protocolo é o controle de fluxo, onde ele se certifica que o pacote chegou no destino, ou seja, ele envia um pacote e o destino envia uma resposta informando que aquele pacote chegou integro. Dessa forma segue o fluxo e é enviado o pacote seguinte. Caso ele envie o pacote, e o destino não confirme nada, ele reenvia aquele pacote até receber a resposta do recebimento por parte do destino. Algumas aplicações que usam o TCP são: Conexão a websites, FTP, Protocolos de Email e etc.

O UDP é um protocolo bastante simples, pois ele é um protocolo sem conexão, e por consequência, ele é conhecido com oum protocolo não confável, pois não garantir que o pacote chegará integro no destino. Apesar de não ser confiável, ele é um protocolo bastante rápido, e bastante utilizado em aplicações tolerantes a perdas. 
Outra característica importante do UDP é que ele é 1->n, ou seja, ele conegue enviar dados de uma fonte para n destinos simultâneamente, trazendo assim uma eficiência muito grande, onde é possível transmitir uma grande quantidade de dados em um curto espaço de tempo. Algumas aplicações que usam o UDP são: VoIP, Streaming, Games e etc.

#### 4. Descreva o que é uma VPN, quais as classificações com relação a uso e cite exemplos para cada. 

R- 
O termo VPN (Virtual Private Network), utilizado para descrever o que seria uma conexão segura através de uma rede compartilhada, nos possibilita a segmentação dos dados privados do tráfego comum de outras redes, e apenas os receptores autorizados terão acesso aos mesmos. Um host terá acesso a uma rede local de uma empresa através da internet, por exemplo, e os dados que serão criptografados, serão lidos apenas pelos envolvidos autorizados.
Esse é o principal objetivo da VPN, a qual busca resolver o problema de como levar redes privadas das empresas para os colaboradores que estão remotos pela internet, de forma segura.
A VPN pode proporcionar algumas vantagens em ser utilizada, que são: Acesso remoto, proteção, privacidade, integridade e autenticidade.
Para usurfruir das melhores práticas de se utilizar uma VPN, temos vários tipos e classificações das mesmas, dependendo de cada casos de uso. Algumas delas são: PPTP, L2TP, IPSec, OpenVPN, IKEv2.
O protocolo PPTP foi o pioneiro em VPN, desenvolvido pela Microsoft, e entregue em larga escala por ser rápido e fácil de implementar. Apesar de contar com uma criptografia de 128bits, o protocolo é largamente conhecido por um protocolo não seguro. Entretanto ainda pode ser um protocolo útil, em casos que uma segurança inquebrável não é o objetivo, como Streaming e Torrent. 
L2TP, como o nome já fala, é um túnel de camada 2 e possui uma alta compatibilidade, possibilitanto a conexão de varios tipos de dispositivos, além de ser muito fácil de implementar. Uma grande desvantagem é que ele não fornece criptografia embarcada, porém podemos associar ao L2TP, a criptografia do IPSec de 256 bits. Dessa forma pode ser utilizado em aplicações que não requerem muita velocidade, porém alta segurança.
IPSec puro, é um protocolo bastante seguro, e que possui alguns benefícios. Além disso funciona para duas situações, o modo transporte (Host-to-Host) e o modo tunelamento (Lan-to-Lan). Entretanto podemos encontrar alguns problemas com firewalls e também pode não ser um protocolo tão rápido. Por causa da segurança que trás, o IPSec é indicado para o uso de conexão Site-to-Site.
OpenVPN é um protocolo desenvolvido pela comunidade, ou seja, de código aberto que trás uma flexibilidade muito boa para contornar firewall, além de ser um protocolo muito rápido. Por ser um protocolo seguro, estável e funcionar em várias plataformas, ele é recomendado por grande parte dos especialistas para usos como Games e torrent ou para contornar um firewall.
IKEv2 é um dos protocolos mais seguros, estáveis e extremamente rápido na reconexão, ou seja, se a VPN cair, o IKEv2 a sobe novamente muito rápido. É um protocolo altamente compatível e mais veloz do que outros protocolos. Mesmo sendo um protocolo muito complexo de implementar, é um dos mais indicados hoje para usos de empresas que pretendem disponibilizar suas redes ou sistemas para que funcionários as acessem de forma remota pela internet.

#### 5. Dado uma empresa que trabalha totalmente em home office, que estrutura você propõe para que os funcionários acessem serviços internos de maneira segura? Caso opte por mais de uma proposta, pontue as vantagens e desvantagens de cada uma e aponte qual você escolheria.

R-

#### 6. Comente sobre virtualização, containers e orquestradores de containers. O que é cada um, quais principais ferramentas do mercado, benefícios que trazem, sua experiência com cada um e outros pontos que achar interessante. 

R- 
Virtualização - É uma técnica de computação que tem como objetivo ocultar os recursos reais de uma máquina e suas complexidades do usuário final. Dessa forma somos capazes de rodar vários Sistemas operacionais dentro de uma mesma máquina, evitando assim ociosidade dos recursos, e aproveitando ao máximo toda sua capacidade. Essa abordagem nos dá a possibilidade de termos ambientes operacionais de diferentes usuários dentro de uma mesma máquina ao mesmo tempo.
	A arquitetura consiste em máquinas virtuais (VM) rodando cada uma com seu sistema operacional, podendo ser qualquer um e de tipos variados, todas as VMs rodando sobre um Hypervisor, como o VirtualBox por exemplo, e esse Hypervisor rodando sobre o sistema operacional padrão do host hospedeiro. Tudo isso por cima do mesmo Hardware.
	Em outras palavras, o Virtualização permite que usuários distintos rodem aplicações variadas, sobre sistemas operacionais variados e tudo sobre o mesmo hardware, compartilhando recursos. E tudo de forma transparente para o usuário.
	Diante disso, a utilização da virtualização trás vários benefícios para as empresas, como redução nos custos, tanto quanto custos de energia, custo de manutenção, custos operacionais, e muitos outros. Segurança, onde quando aplicada proncipalmente em Cloud, a virtualização recebe uma camada bastante efetiva de segurança, quando se trata dos recursos do próprio provider. Agilidade em manutenções, otimizações de processos e muitos outros.
	As principais ferramentas de mercado são o Xen, VMware e VirtualBox. Tenho atuado com esse tipo de abordagem desde meu início no meu emprego atual, a 10 anos atrás, utilizando muito a ferramenta do Xen, onde possuímos toda uma infra virtualizada em cima de dois blades e várias lâminas como hardware. Para outras aplicações, utilizo o VMware e Virtualbox, por serem gratuitos, e também em todos os laboratórios de estudos que venho fazendo. Já realizei laboratório de prover VMs no VirtualBox utilizando o Vagrante, de forma que possa automatizar a estrutura utilizada.

Containers - Uma técnica utilizada pela comunidade de TI em larga escala com foco no Desenvolvimento, testes e produção de sistemas e aplicações. Os containers são um tipo de virtualização a nível de sistemas operacionais onde nos proporciona a possibilidade de rodarmos vários sistemas operacionais sobre um unico sistema do host.
	Apesar de ser um tipo de virtualização, o container não funciona igual a virtualização, pois o mesmo utiliza o Kernel padrão do sistema principal, diferentemente da virtualização com VMs, onde cada uma possui seu sistema operacional completo inclusive kernel, fazendo com que o consumo de recursos seja de certa forma elevado.
Utilizando um exemplo de uma aplicação web, na Maquina virtual, iríamos rodar todos os processos e recursos do sistema dentro da próprima VM, como por ex o Nginx, PHP, Mysql e etc todas dentro da VM. Em caso de utilização de containers, todos esses serviços estariam rodando em containers distintos, onde cada um teria sua função no sistema, tornando assim os sistemas muito mais resilientes, eficientes e escaláveis.
	Ao falar de containers, é quase que obrigatório falarmos do Docker, uma ferramenta de código aberto, apoiada pela empresa Docker, que tem como objetivo o trabalho direto com containers. O Docker utiliza recursos do kernel do sistema como os Cgroups e namespaces para separar os processos ali presentes.
	Os containers possuem um poder incomparável quando aplicados no ambiente de produção, entretando a medida em que os números deles vão crescendo consideravelmente, é preciso gerenciar, controlar e monitorar esses ambientes, de forma eficaz, e é aí que entra o papel dos Orquestradores de containers. A Docker possui seu próprio orquestrador, o docker swarm, porém os mais utilizados em larga escala são o Openshift e o Kubernetes, desenvolvidos pela Google. 
	Uma das grandes funcionalidades dos orquestradores, é a possibilidade de provisionar ou apagar containers de forma automática de acordo com a demanda do sistema. Essa técnica é conhecida como clusters, onde podemos rodar centenas ou até dezenas de milhares de containers de forma orquestrada e usando o mesmo sistema de armazenamento, que são os volumes.
	Um exemplo de aplicação dessa solução, seria um ecommerce que fará uma super promoção durante uma blackfriday, e irá receber um volume extremamente grande de acessos durante essa janela. A solução de containers pode atender de forma muito eficiente a esse caso, pois com um orquestrador bem aplicado é possível provisionar quantos containers forem necessários para suportar as requisições, e tudo de forma automática. Esse é um dos grandes benefícios que os containers e orquestradores nos proporcionam.
	No meu trabalho atual não tivemos até então essa demanda de implementação de sistemas baseados em containers, porém tivemos uma aplicação em que por vontade própria, coloquei em container e hospedei em uma máquina provisionada na OCI. Criei a imagem da maquina, com todas as dependências ali declaradas no Dockerfile, subi a imagem para o docker hub, e rodei o container nessa VM na OCI, e dessa forma consegui provisionar a aplicação na nuvem, utilizando container. 
	Ao nível de estudos e laboratórios, ja realizei várias implantações de alguns sistemas na AWS e tbm na GCP, utilizando docker, Nginx, PHP, APache e etc. Fiz também laboratório utilizando kubernetes na GCP, e até utilizando minha proprima máquina utilizando o minikube e simulação de orquestração.

#### 7. Comente o que é Infrastructure as code, quais os prós e contras do seu uso e faça uma proposta básica de como gerenciar um ambiente na nuvem como um código (ferramentas, versionamento, fluxos de mudança…). Se atente aos pontos que considerar importante para que tudo funcione bem a longo prazo

R- A Infrastructure as code surgiu a partir da necesidade de evolução do formato em que empresas de tecnologias trabalhavam, onde o time de dev era totalmente separado do time de Ops, e nesse processo se gerava muitos problemas indesejáveis com a entrega do produto, mesmo todos tendo um objetivo final. Nesse processo, foi idealizado por Patrick Debois, uma nova proposta de trabalho, onde os times trabalhavam de forma integrada, fazendo entregáveis juntos e proporcinando uma melhor acertividade, segurança e velocidade no produtos em produção. Essa abordagem hoje é conhecida por DevOps. 
	Só é possível fazer tudo isso, a partir da possibilidade de construir ambientes padronizados e de forma rápida, e é em cima disso que a IaC foi idealizada e implementada, e largamente utilizada hoje nos ambientes de desenvolvimento e de produção das organizações. A prática do versionamento que se tinha em ambiente dev, onde você pode gerenciar todas as versões daquele código e acessar versões anteriores de forma rápida e poder tomar decisões em cima disso, e trazer isso também para o ambiente de infraestrutura, onde a tempos atrás era feita de forma totalmente artesanal, isso integrado a utilização de virtualização, containers, cloud e toda essa linha evolutiva, trás uma evolução gigante em resultados ao negócio da organização.
	Resumindo, o IaC, é a possibilidade de entregar ambientes padronizados, a partir de um arquivo de definição, onde temos toda a parametrização do que fará parte daquele ambiente, e com essa declaração, podemos disponibilizar rapidamente, ambientes indepotentes e de diferentes versões.
	Portanto a IaC nos proporcina também a possibilidade de automatizar processor de uma esteira de produção utilizando a Entrega contínua da infra baseada em código. Para isso existem ferramentas que fazem esse gerenciamento dos códigos, testes e deploys e forma automatizadas, que são as ferramentas de CI/CD. Essa abordagem amplamente utilizada em times de deves, agora também é  implantada com códigos de ambientes de Infraestruturas.
  Na [página inicial](https://github.com/athoslimaa/web-incognia-test) desse repositório temos um exemplo básico versionado, de uma infraestrutura provisionada na AWS utilizando a ferramenta Terraform para gerenciar todo o processo, e em paralelo com a AWS Provider, que faz a interface entre o Terraform e a AWS. Como continuação poderíamos adicionar outras ferramentas para auxiliar nesse gerenciamento, como por exemplo o Ansible, que faria o papel de toda configuração das máquinas da infra de forma conjunta e rápida.


#### 8. Dado uma empresa com um parque de computadores dividido em Linux, MacOS e Windows, proponha uma forma de gerenciar esses computadores de forma centralizada, pense em mudanças de software, coleta de informações, hardening e afins. Caso opte por mais de uma proposta, pontue as vantagens e desvantagens de cada uma e aponte qual você escolheria. 

R-




