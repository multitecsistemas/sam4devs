# Bem vindo

Bem vindo à documentação para desenvolvedores do ERP SAM.

!!! info "Saiba Mais"
	Para conhecer mais, visite o site oficial do [SAM](https://multitecsistemas.com.br). 

## Introdução

----

Este documento tem como finalidade apresentar as diferentes formas de cutomização de processos e integração com os recursos e funcionalidades do ERP SAM, por exemplo, ao inserir um registro no sistema há a posiblidade de inferir neste processo realizando críticas/retrições. O SAM é um sistema totalmente adaptável e pode se enquadrar perfeitamente às regras do seu négocio, além de se integrar perfeitamente a outros sistemas atuais do mercado. Aqui veremos como realizar estas customizações de processos e integrações.

## Recomendações

----

O SAM utiliza como parte de seus componentes algumas bibliotecas e frameworks, antes de começar recomendamos que você leia e entenda um pouco mais sobre elas.

- [VUE.js](https://br.vuejs.org/v2/guide/index.html)
- [ApexCharts](https://apexcharts.com/docs/installation/)
- [Quasar](https://quasar.dev/)
- [Swing](https://docs.oracle.com/javase/tutorial/uiswing/start/about.html)

## Linguagens Utilizadas

----

As customizações e integrações com o SAM são contruidas a partir da linguagem Groovy. O Groovy é uma linguagem de programação orientada a objetos desenvolvida para a plataforma Java como alternativa à linguagem de programação Java. Ele possui características de Python, Ruby e Smalltalk. Utiliza uma sintaxe similar à de Java, é compilada dinamicamente para bytecode Java e integra-se transparentemente com outros códigos e bibliotecas Java.

!!! summary "Visite a documentação do [Groovy](https://groovy-lang.org/documentation.html)."

Os componentes gráficos renderizados na web são construidos com HTML, CSS e JavaScript, podendo ou não utilizar os componentes dos frameworks que vimos a cima. Já os componentes gráficos rederizados em desktop são construidos com Swing.

## Como funciona

----

Todas as customizações e integrações podem ser construidas a partir do próprio SAM, nele você encontrará uma ferramenta já integrada e pronta para uso chamada SAMDEV, porém, também podemos criá-las a partir de qualquer outro editor de textos, editor de códigos ou IDE de sua preferencia.

*[IDE]: Integrated development environment (Ambiente de desenvolvimento integrado)


Além do SAMDEV disponibilizamos dois projetos já integrados com as IDEs Eclipse e NetBeans, faça o download abaixo.

- [Eclipse](https://s3-sa-east-1.amazonaws.com/br.com.samdev/templates/eclipse-samdev.zip)
- [NetBeans](https://s3-sa-east-1.amazonaws.com/br.com.samdev/templates/template_projeto_formula_revenda.zip)

## Requisitos

----

Para instalar do SAM e utilizar do SAMDEV ou outros Editores/IDEs, devemos instalar os seguintes requisitos:

- [Java SE Development Kit 15.0.2](https://www.oracle.com/java/technologies/javase/jdk15-archive-downloads.html)
- [PostgreSQL Database 10.18 +](https://www.oracle.com/java/technologies/javase/jdk15-archive-downloads.html)

!!! note "Nota"
	Visite nosso repositório para visualizar alguns exemplos que iremos explorar por aqui. 
	[https://github.com/multitecsistemas/sam4](https://github.com/multitecsistemas/sam4)
