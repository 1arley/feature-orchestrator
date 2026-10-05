# Modelos de entrega

Escolha o modelo pelo grau de clareza, mudança esperada, risco e ritmo de feedback. A preferência explícita do usuário prevalece, exceto que requisitos de segurança ou regulação não podem ser dispensados por uma preferência de velocidade. Modelos podem ser combinados: por exemplo, ciclos espirais para reduzir incerteza com especificação e provas formais como gate de produção.

## Cascata

Use quando escopo e aceite estão claros, as decisões são simples e reversíveis e há poucas incógnitas relevantes.

- Faça pesquisa e grilling no início. Resolva as perguntas materiais em uma conversa curta com o usuário ou pelo responsável de decisão já escolhido.
- Delegue planejamento e apresente plano, escopo, arquitetura de alto nível, critérios de aceite e riscos para aprovação quando o usuário for o decisor.
- Depois que o plano for aceito, execute as etapas dependentes em sequência até a entrega, sem pedir aprovação manual a cada etapa. Interrompa apenas por uma decisão não delegada, mudança material de escopo ou risco que invalide o plano.
- Se o escopo mudar, volte ao planejamento afetado e torne visível o impacto antes de continuar.

## Incremental

Use quando os requisitos são gerais ou devem evoluir, mas o sistema permite entregar fatias pequenas e úteis rapidamente.

- Defina uma primeira fatia vertical com valor e critérios de aceite observáveis.
- Para cada fatia, delegue planejamento, arquitetura necessária, implementação, verificação e entrega; mostre a entrega e recolha feedback antes da próxima fatia.
- Com decisão do usuário, espere confirmação manual em cada gate de entrega. Com decisão de Jev ou do orquestrador, use o julgamento configurado para recomendar continuar, ajustar ou parar e mostre a decisão e seu motivo. Essa escolha não autoriza operações externas ou irreversíveis sem autorização.
- Incorpore mudanças ao plano entre fatias, preservando decisões e evidências que ainda se aplicam.

## Prototipação

Use para responder rapidamente a uma pergunta de viabilidade ou experiência quando ainda não se sabe se a ideia funciona.

- Combine a hipótese a provar, limite de escopo e critério simples de sucesso. Trabalhe em sandbox, branch ou área descartável quando isso reduzir risco.
- Construa o menor protótipo capaz de testar a hipótese. Priorize velocidade e evidência de viabilidade, sem adicionar acabamento ou infraestrutura de produção que não ajude a responder à pergunta.
- Verifique o caminho essencial e rotule limitações; não apresente o protótipo como pronto para produção.
- Encerre apresentando três opções: descartar; continuar a partir do protótipo, com uma etapa explícita de endurecimento e revisão; ou descartar e reconstruir depois que a ideia for validada. O usuário, Jev disponível ou orquestrador decide conforme a política escolhida.

## Espiral orientado a risco

Use quando há incerteza ou risco alto e o usuário quer ajustar a direção conforme aprende. Combine antes o objetivo, as restrições e o limite de risco com o usuário; mantenha espaço para ele sentir e escolher o rumo ao longo do trabalho.

- Identifique riscos concretos de falha, impacto, incerteza e evidência disponível. Priorize primeiro o risco capaz de invalidar a solução ou causar o maior dano; não use uma pontuação numérica sem dados ou pedido que a justifique.
- Para o risco prioritário, delegue uma rodada curta de investigação, modelagem ou experimento, implementação mínima, verificação e entrega de evidência.
- Mostre o que a rodada reduziu, confirmou ou descobriu; atualize riscos e opções de direção e então selecione o risco seguinte.
- Ajuste o equilíbrio entre rapidez e qualidade ao impacto do risco e às escolhas do usuário. Reduza ou aumente escopo entre rodadas sem perder os critérios de segurança e aceite.

## Método formal

Use quando o usuário pedir prova matemática de propriedades de software ou quando uma parte do sistema exigir garantia elevada, como software embarcado de aviação ou equipamento médico de imagem. Ele custa mais tempo e requer especialistas e ferramentas adequadas. O método pode ser combinado com os demais, mas a pressa de um protótipo ou uma entrega incremental não remove os gates formais para produção.

- Antes de tratar a implementação como pronta para produção, delegue uma especificação formal precisa: estado e tipos, pré-condições, pós-condições, invariantes, contratos, propriedades temporais ou modelo de estados conforme o problema. Torne explícitos limites do sistema, hipóteses ambientais e o que não está sendo provado.
- Peça provas matemáticas verificáveis para as propriedades de segurança e correção acordadas. Use provador de teoremas, verificador de modelo ou ferramenta apropriada ao formalismo; registre ferramenta e versão, entradas, hipóteses, obrigações de prova e resultado reproduzível.
- Delegue revisão independente da especificação, das hipóteses e das provas. A implementação só pode ser chamada de formalmente verificada para as propriedades e o código refinado cobertos pelas evidências aceitas.
- Uma prova cobre suas propriedades sob suas hipóteses. Ela pode substituir testes que apenas duplicariam uma propriedade provada, se o processo de assurance aplicável aceitar essa evidência. Não conclua que todo teste é desnecessário: valide fronteiras não modeladas, integração, hardware, runtime, compilador, toolchain, sensores e comportamento ambiental conforme o risco e as normas aplicáveis.
- Exija validação por profissionais responsáveis pelo domínio e pelo processo de segurança/certificação antes de qualquer alegação de conformidade ou liberação crítica. Uma explicação de LLM ou prova em linguagem natural não é evidência matemática reproduzível.
