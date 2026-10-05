# Protocolo de delegação

O orquestrador reduz o trabalho de cada subagente a uma tarefa com contexto suficiente e saída verificável. Use um subagente diferente por papel ou etapa quando a capacidade estiver disponível; não envie simultaneamente tarefas dependentes. Revisor e testador devem avaliar os artefatos aceitos de forma independente, sem receber a conclusão que se espera que confirmem.

## Pacote de tarefa

Adapte este modelo e mantenha-o curto:

```text
Papel e etapa:
Objetivo desta tarefa:
Contexto aceito: resumo, caminhos dos arquivos e decisões relevantes
Escopo e limites:
Critérios de conclusão:
Verificação/evidência solicitada:
Saída esperada: artefatos, achados, decisões pendentes e próximo risco
```

Envie apenas contexto relevante ao papel. Inclua fatos do repositório com caminhos e evidências, não hipóteses como se fossem fatos. Para decisões, forneça opções consideradas, critérios e responsável por decidir. Não peça a um agente para adivinhar autorização, critérios ausentes ou decisões do usuário.

## Etapas e entregáveis típicos

| Etapa | Entregável mínimo |
| --- | --- |
| Pesquisa e grilling | Estado atual relevante, requisitos, incógnitas, evidências e perguntas materiais |
| Planejamento | Escopo, aceite, fatias, dependências, riscos e verificação por fatia |
| Arquitetura/modelagem | Decisões e alternativas, contratos/dados/interfaces afetados e riscos de migração |
| Construção | Alterações limitadas ao plano, resumo de arquivos e decisões de implementação |
| Testes/revisão | Verificações executadas, resultados, lacunas, bugs ou evidências formais conforme o modelo |
| Entrega | Resumo do que foi concluído, como verificar, itens não concluídos e riscos residuais |

Adapte ou omita etapas que o modelo não exige. No modelo formal, acrescente especificação, obrigações de prova, prova reproduzível e revisão independente. Na prototipação, reporte hipótese, evidência rápida e limitações.

## Controle do orquestrador

- Mantenha um registro enxuto: modelo, responsável por decisões, escopo/aceite, decisões aceitas, etapa atual, riscos abertos, evidências e próximo responsável.
- Ao fechar uma etapa, confira o resultado contra seu pacote e o estado compartilhado do repositório. Corrija ou reabra a etapa se faltar evidência; não propague uma conclusão não verificada.
- Gere o pacote seguinte a partir dos artefatos aceitos e de um resumo compacto. Atualize-o quando uma mudança invalidar requisito, decisão, risco ou resultado anterior.
- Evite atribuir dois agentes para editar os mesmos arquivos ao mesmo tempo. Se houver conflito, serialise as alterações e peça integração explícita.
- Respeite gates humanos e autorização para efeitos externos. Uma recomendação de subagente ou Jev orienta a decisão; não substitui consentimento obrigatório.
- Se a capacidade de subagentes estiver indisponível, execute cada papel sequencialmente e preserve o mesmo registro e contrato de saída, sem afirmar que houve delegação.
