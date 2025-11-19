#  Salesforce Case Técnico – Solicitação de Alterações Cadastrais

Este repositório contém a solução para o case técnico de Desenvolvedor Salesforce.  
O objetivo é implementar um sistema onde **estudantes solicitam alterações cadastrais** e **colaboradores analisam e aprovam** as solicitações antes que as mudanças sejam aplicadas ao registro do aluno (Contact).

---

##  Visão Geral

O sistema implementa:

- Formulário para criação de solicitações por estudantes  
- Área interna para colaboradores aprovarem ou rejeitarem  
- Atualização automática dos dados do Contact quando aprovado  
- Histórico da solicitação  
- Notificações de status

---

##  Funcionalidades

###  StudentChangeRequestForm (LWC)
Formulário para que o aluno submeta uma nova solicitação.

###  ChangeRequestApprovalList (LWC)
Lista exibida aos colaboradores com solicitações pendentes.

###  ChangeRequestDetail (LWC)
Tela de aprovação com botões **Aprovar** e **Rejeitar**, exibindo dados antigos e novos.

###  Apex Controllers e Services
- `ChangeRequestController` – criação e consulta de solicitações  
- `ChangeRequestApprovalService` – processamento da aprovação  
- `ContactUpdateService` – atualiza o Contact com os dados aprovados  

###  Testes Apex
Cobertura mínima de **85%**.

###  Objeto Customizado
`Change_Request__c`  
Usado para armazenar solicitações de alteração.

---

##  Modelagem de Dados

### Objeto: `Change_Request__c`

| Campo | Tipo | Descrição |
|------|------|-----------|
| Student__c | Lookup(Contact) | Aluno solicitante |
| Request_Type__c | Picklist | Tipo da alteração |
| New_Value__c | Long Text Area | Valor proposto |
| Old_Value__c | Long Text Area | Valor atual |
| Status__c | Picklist | Pendente / Aprovado / Rejeitado |
| Reason__c | Text | Motivo |
| Reviewer__c | Lookup(User) | Colaborador revisor |

---

##  Fluxo do Processo

1. **Estudante** cria uma solicitação pelo LWC.  
2. Solicitação fica com status **Pendente**.  
3. **Colaborador** visualiza a lista de solicitações pendentes.  
4. Colaborador aprova ou rejeita.  
5. Se **aprovado**, o sistema atualiza automaticamente o Contact.  
6. Notificações são enviadas ao aluno.

---

##  Segurança

### Estudante
- Pode criar e visualizar apenas suas solicitações.

### Colaborador
- Pode visualizar, aprovar e rejeitar todas as solicitações.

---

## Tecnologias Utilizadas
Salesforce Apex

Lightning Web Components

SOQL

Flow Builder

Salesforce DX

## Critérios de Avaliação
Qualidade e organização do código

Arquitetura da solução

Modelagem de dados

Testes unitários

Qualidade da documentação

Boas práticas de LWC e Apex

##  Como Instalar

### 1. Criar pacote de implantação
Adicione todos os componentes do projeto em um conjunto de implantação.

### 2. Deploy do Código para avaliação de codificação e estrutura de projeto
1. Faça um fork deste repositório.
2. Desenvolva sua solução no repositório criado pelo fork.
3. Certifique-se de que o repositório esteja público.
4. Limite de 5 commits.
5. Envie a URL do seu repositório para o e-mail ana.neneve@pucpr.br:

## Complementar
1. Criar página no experience Cloud para entrada de solicitações de estudantes.
2. A arquitetura sugerida acima não é a ideal, será considerada visão de arquitetura melhorada e funcional como pontuação extra.

## Obs.
- Mantenha a org ativa e funcional para próxima etapa de apresentação funcional do case técnico desenvolvido.
