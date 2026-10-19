# Desafio Criativo: Planejando Automações com N8N Usando Apenas Bons Prompts

Nesta atividade, será planejado uma automação N8N a partir de um prompt claro e estruturado.

## Passo 1: Defina a automação desejada

Nesta etapa, você vai descrever qual processo deseja automatizar e quem será beneficiado por ele.

### O que fazer:

Responda:
• Qual tarefa repetitiva você deseja automatizar?
• Quem utilizará ou será impactado pela automação?
• Qual resultado final deve acontecer?

```text
Quero criar uma automação no N8N para o processo de triagem, agendamento de entrevistas e onboarding (coleta de dados e assinaturas de termos) de novos voluntários de forma automatizada e segura.

Público ou responsável:
Coordenadores de RH/Voluntariado da ONG (avaliadores) e os cidadãos candidatos a voluntários.

Resultado esperado:
Centralização dos dados dos candidatos em uma planilha protegida, filtragem automática entre aprovados e reprovados através de uma interface de visualização imutável, agendamento autônomo de entrevistas com links do Google Meet, envio de formulário de onboarding com validação estrita de dados e geração automatizada do Termo de Adesão em PDF enviado por e-mail para arquivamento no Google Drive, mantendo total conformidade com a LGPD.
```

## Passo 2: Adicione contexto e regras

Nesta etapa, você vai informar os sistemas envolvidos, as etapas do fluxo e as restrições importantes.

### O que fazer:

Responda:
• Quais ferramentas ou serviços participam da automação?
• Quais etapas devem acontecer em sequência?
• Existe alguma regra, validação ou exceção?

```text
Ferramentas envolvidas:
- Google Sheets (Como banco de dados central oculto)
- Google Looker Studio (Para visualização imutável dos dados pelos responsáveis)
- Google Forms (Dois formulários: um interno de Decisão do Avaliador e um externo de Onboarding do voluntário)
- Google Agenda (Páginas de Agendamento/Appointment Slots e Google Meet)
- Google Docs (Modelos de documentos e recursos de conversão para PDF)
- Google Drive (Armazenamento seguro dos documentos assinados)
- Gmail (Para notificações aos candidatos)

Fluxo desejado:
1. O n8n recebe os dados dos sites de vagas via Webhook/API e insere em uma aba protegida do Google Sheets (conectada ao painel Looker Studio).
2. O responsável analisa os candidatos no painel do Looker Studio e usa um Google Form Interno para registrar a sua decisão ("Aprovado para Entrevista", "Suplente" ou "Reprovado").
3. Se "Reprovado", o n8n envia um e-mail acolhedor de agradecimento. Se "Aprovado", o n8n envia um e-mail com o link da Página de Agendamento do Google Agenda.
4. O candidato agenda o horário da entrevista. O Google Agenda cria o evento e gera a sala do Google Meet de forma nativa.
5. Pós-entrevista, o responsável altera o status do candidato para "Selecionado". O n8n dispara um e-mail com o link do Google Forms de Onboarding.
6. O voluntário preenche o formulário de Onboarding. O n8n captura as respostas, preenche as tags em um modelo do Google Docs (Termo de Adesão), gera o PDF final e envia para o e-mail do voluntário como cópia formal.
7. O n8n salva o PDF do termo assinado/aceito em uma pasta restrita no Google Drive da ONG e atualiza o status do voluntário na planilha principal para "Ativo".

Regras importantes:
- Os responsáveis da ONG não podem editar a planilha principal diretamente, apenas visualizar os dados via painel ou formulário de decisão para evitar alteração acidental de dados.
- O Google Forms de Onboarding deve conter validações estritas via Regex para CPF, Telefone e E-mail.
- O formulário de inscrição inicial deve conter um checkbox obrigatório de consentimento de uso de dados em conformidade com a LGPD.
- Os dados de candidatos reprovados/suplentes devem ter um consentimento para permanência em Banco de Talentos por até 6 meses. Uma rotina de Cron/Schedule no n8n deve apagar permanentemente da planilha os dados de candidatos recusados com mais de 6 meses de registro.
```

## Passo 3: Monte o prompt final

Nesta etapa, você vai unir todas as peças construídas anteriormente em um único prompt completo.

### O que fazer:

Revise:
• O objetivo da automação está claro?
• As etapas estão em ordem?
• As regras e restrições foram informadas?

```text
Atue como um especialista em N8N.

Crie uma automação para o processo completo de triagem, agendamento de entrevistas e onboarding de novos voluntários para uma ONG, focando no menor custo possível através do uso exclusivo do ecossistema Google Workspace.

Público:
Coordenadores de RH/Voluntariado da ONG e candidatos a voluntários.

Ferramentas envolvidas:
Google Sheets, Google Looker Studio, Google Forms, Google Agenda (com Google Meet), Google Docs, Google Drive e Gmail.

Fluxo:
1. Captura de dados de candidatos de sites de vagas externos e inserção em aba protegida do Google Sheets (exibida em modo leitura no Google Looker Studio).
2. Monitoramento de respostas de um Google Form interno de Decisão (Aprovado para Entrevista, Suplente ou Reprovado).
3. Disparo de e-mail de rejeição acolhedor para reprovados ou envio de link do Google Agenda para agendamento automático de entrevista dos aprovados.
4. Envio automatizado de um Google Forms de Onboarding pós-entrevista para os candidatos finais escolhidos (ou acionamento de suplentes em caso de desistência).
5. Preenchimento automatizado de um modelo de Termo de Adesão no Google Docs a partir dos dados validados do formulário, conversão em PDF e envio de cópia por e-mail.
6. Upload do PDF na pasta do voluntário no Google Drive e atualização do status para "Ativo" no Google Sheets.
7. Execução de uma rotina mensal via Cron para deletar permanentemente os dados de candidatos reprovados há mais de 6 meses da planilha principal.

Regras:
- Os dados na planilha de triagem não podem ser alterados diretamente pelos usuários da ONG (apenas visualizados pelo Looker Studio).
- Todos os formulários externos devem incluir checkboxes obrigatórios de consentimento da LGPD.
- Validação estrita de dados (CPF, E-mail e Telefone) nas etapas de formulário.

Explique quais nós do N8N devem ser utilizados e a lógica de funcionamento do workflow.
```
