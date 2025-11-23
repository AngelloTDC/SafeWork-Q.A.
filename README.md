# SafeWork — Plataforma Inteligente de Segurança e Bem-Estar no Trabalho

## 👥 Equipe

- **Angello Turano da Costa** – RM 556511  
- **Cauã Sanches de Santana** – RM 558317  
- **Gustavo de Souza Amorim** – RM 556999  

---

## 📌 Visão Geral

O **SafeWork** é uma plataforma voltada para **segurança, compliance e bem‑estar no trabalho**, desenvolvida como parte da **Global Solution FIAP** na disciplina de **Quality Assurance / DevOps**.

A solução integra:

- Monitoramento de uso de EPIs com visão computacional  
- Gestão de funcionários, setores, EPIs e regras de conformidade  
- Geração de alertas de não conformidade  
- Dashboards de indicadores de segurança  
- Check-in diário de bem‑estar dos colaboradores  

Este repositório concentra artefatos de **QA**, **DevOps** e **documentação** do projeto.

---

## 🔗 Links Importantes

- 🟢 **Repositório GitHub (Q.A.):**  
  https://github.com/AngelloTDC/SafeWork-Q.A.

- 🟣 **Azure DevOps – Projeto SafeWork:**  
  https://dev.azure.com/SafeWorkProject/SafeWork

- 📘 **Wiki (Documentação detalhada – Azure DevOps):**  
  Disponível na aba **Wiki** do projeto SafeWork no Azure DevOps.

- 📄 **Relatório Final em PDF:**  
  `SafeWork_Entrega_Final_v2.pdf` (recomendado armazenar em `/docs` neste repositório).

---

## 🧩 Funcionalidades (Resumo das Features)

- **F01 – Autenticação e Controle de Acesso**  
  Login seguro, controle de sessão, proteção de rotas internas e recuperação de senha.

- **F02 – Cadastro e Gestão de Funcionários**  
  Cadastro, edição, listagem e organização de colaboradores por setor.

- **F03 – Cadastro de EPIs e Regras de Conformidade**  
  Registro de EPIs e criação de regras obrigatórias por setor (base para a IA).

- **F04 – Upload de Mídia**  
  Envio de imagens/vídeos para auditoria e análise automática.

- **F05 – IA de Detecção de EPIs**  
  Uso de visão computacional para detectar ausência/uso incorreto de EPIs.

- **F06 – Alertas de Não Conformidade**  
  Geração automática e manual de alertas, com histórico para auditoria.

- **F07 – Dashboard de Compliance**  
  Indicadores, gráficos e KPIs por setor, período e tipo de evento.

- **F08 – Check‑in de Bem‑Estar do Funcionário**  
  Registro diário de humor, estresse e fadiga, com acompanhamento gerencial.

---

## 🧪 Qualidade e Testes

A qualidade foi garantida com apoio do **Azure DevOps Test Plans**, seguindo a proposta da disciplina de QA.

**Resumo dos testes:**

- ✅ 1 **Test Plan** principal: *SafeWork — Testes Funcionais*  
- ✅ 8 **Suites** (uma para cada Feature: F01 a F08)  
- ✅ 8 **Test Cases** detalhados, com:
  - Objetivo (Summary)  
  - Pré‑requisitos  
  - Steps + Expected Result  
  - Uso de **Param Values** (`<email>`, `<senha>`, `<setor>`, `<arquivo>`, `<periodo>`, `<humor>`, `<stress>`, `<fadiga>`)  

- ✅ Execução via **Web Runner**  
- ✅ **100%** dos Test Points com status **Passed**  
- ✅ Relatórios e gráficos gerados automaticamente em **Progress report** e **Chart**  

Todos os prints de evidência foram incluídos no PDF final e podem ser consultados também diretamente no Azure DevOps.

---

## 🔧 DevOps – Pipeline CI (Integração Contínua)

Foi configurada uma **pipeline de CI** no Azure DevOps Pipelines para:

- Compilar o projeto com Maven  
- Rodar testes automatizados (quando presentes)  
- Gerar e publicar artefatos `.jar` como resultado do build  

### YAML de referência

```yaml
trigger:
  - main

pool:
  vmImage: 'ubuntu-latest'

steps:
  - task: Maven@3
    inputs:
      mavenPomFile: 'pom.xml'
      goals: 'clean install'
      publishJUnitResults: true
      testResultsFiles: '**/surefire-reports/*.xml'
    displayName: 'Build com Maven'

  - task: CopyFiles@2
    inputs:
      SourceFolder: '$(System.DefaultWorkingDirectory)'
      Contents: '**/*.jar'
      TargetFolder: '$(Build.ArtifactStagingDirectory)'
    displayName: 'Copiar arquivos .jar'

  - task: PublishBuildArtifacts@1
    inputs:
      PathtoPublish: '$(Build.ArtifactStagingDirectory)'
      ArtifactName: 'safework-artifact'
      publishLocation: 'Container'
    displayName: 'Publicar Artefato'
```

> Mesmo sem CD (deploy automático), essa CI já atende ao foco da disciplina: **build automatizado, rastreabilidade de versões e apoio à qualidade**.

---

## ▶️ Como Rodar o Projeto (Exemplo para Backend Java)

> Ajuste conforme a estrutura do seu outro repositório de código, se necessário.

### Pré‑requisitos

- JDK 17  
- Maven  
- Banco de dados SQL rodando (ou H2 para ambiente local)  
- Git

### Passos

```bash
# Clonar o repositório de código (exemplo)
git clone https://github.com/AngelloTDC/SafeWork-Backend.git
cd SafeWork-Backend

# Build
mvn clean install

# Executar a aplicação
mvn spring-boot:run
```

Aplicação disponível em (exemplo):  
`http://localhost:8080`

---

## 🧰 Tecnologias Utilizadas

**Back-end & Lógica de Negócio**
- Java 17  
- Spring Boot  
- Spring Web / Spring MVC  
- Spring Data JPA  
- Spring Security (autenticação)  
- Maven  

**Banco de Dados**
- PostgreSQL / MySQL / SQL Server / H2  

**Visão Computacional / IA**
- OpenCV  
- YOLO (You Only Look Once)  

**DevOps / QA**
- Azure DevOps (Boards, Repos, Pipelines, Test Plans, Wiki)  
- Git  
- JUnit (para testes automatizados)  

**Ferramentas de Apoio**
- IntelliJ IDEA / VS Code  
- Postman / Insomnia  
- GitHub Desktop  

---

## 📘 Documentação

Toda a documentação detalhada do projeto SafeWork está disponível em:

- **Azure DevOps – Wiki:** visão geral do sistema, arquitetura, backlog, testes, pipeline e conclusão.  
- **PDF Final (Compliance, Quality Assurance & Tests):** `SafeWork_Entrega_Final_v2.pdf`, contendo prints, explicações e evidências completas.

---

## ✅ Status do Projeto

- 🔹 Requisitos de QA e DevOps atendidos  
- 🔹 Test Plan executado com 100% de aprovação  
- 🔹 Pipeline CI configurada e funcional  
- 🔹 Documentação final preparada para apresentação acadêmica
