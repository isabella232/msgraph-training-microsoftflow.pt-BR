<!-- markdownlint-disable MD002 MD041 -->

O fluxo que você criou no exercício anterior usa a `$batch` API para fazer duas solicitações individuais para o Microsoft Graph. Chamar o `$batch` ponto de extremidade dessa forma oferece alguns benefícios e flexibilidade, mas a potência real `$batch` do ponto de extremidade é exibida ao executar várias solicitações ao Microsoft `$batch` Graph em uma única chamada. Neste exercício, você estenderá o exemplo de criação de um grupo unificado e associando uma equipe para incluir a criação de vários canais padrão para a `$batch` equipe em uma única solicitação.

Abra o [Microsoft Flow](https://flow.microsoft.com) no seu navegador e entre com sua conta de administrador de locatário do Office 365. Selecione o fluxo que você criou na etapa anterior e escolha **Editar**.

Escolha **nova etapa** e digite `Batch` na caixa de pesquisa. Adicione a ação do **conector de lotes do MS Graph** . Escolha as reticências e renomeie `Batch POST-channels`esta ação como.

Adicione o seguinte código à caixa de texto **corpo** da ação.

```json
{
  "requests": [
    {
      "id": 1,
      "url": "/teams/REPLACE/channels",
      "headers": {
        "Content-Type": "application/json"
      },
      "method": "POST",
      "body": {
        "displayName": "Marketing Collateral",
        "description": "Marketing collateral and documentation."
      }
    },
    {
      "id": 2,
      "dependsOn": [
        "1"
      ],
      "url": "/teams/REPLACE/channels",
      "headers": {
        "Content-Type": "application/json"
      },
      "method": "POST",
      "body": {
        "displayName": "Vendor Contracts",
        "description": "Vendor documents, contracts, agreements and schedules."
      }
    },
    {
      "id": 3,
      "dependsOn": [
        "2"
      ],
      "url": "/teams/REPLACE/channels",
      "headers": {
        "Content-Type": "application/json"
      },
      "method": "POST",
      "body": {
        "displayName": "General Client Agreements",
        "description": "General Client documents and agreements."
      }
    }
  ]
}
```

Observe que as três solicitações acima estão usando [](https://docs.microsoft.com/graph/json-batching#sequencing-requests-with-the-dependson-property) a propriedade dependn para especificar uma ordem de sequência, e cada uma executará uma solicitação post para criar um novo canal na nova equipe.

Selecione cada instância do `REPLACE` espaço reservado e, em seguida, selecione **expressão** no painel conteúdo dinâmico. Adicione a seguinte fórmula à **expressão**.

```js
body('Batch_PUT-team').responses[0].body.id
```

![Uma captura de tela da expressão no painel de conteúdo dinâmico](./images/flow-channel1.png)

Escolha **salvar**e, em seguida, escolha **testar** para executar o fluxo. Selecione o botão de opção **eu executarei a ação do gatilho** e, em seguida, escolha **salvar & Test**. Insira um nome de grupo exclusivo no campo **nome** sem espaços e escolha **executar fluxo** para executar o fluxo.

![Uma captura de tela da caixa de diálogo Executar fluxo](./images/flow-channel3.png)

Depois que o fluxo for iniciado, escolha o link **Exibir atividade de execução do fluxo** e, em seguida, escolha o fluxo de execução para ver o log de atividades.

Quando o fluxo é concluído, a saída final da `Batch POST-channels` ação tem uma resposta de Status http 201 para cada canal criado.

![Uma captura de tela do log de atividades de fluxo bem-sucedido](./images/flow-channel2.png)

Navegue até [Microsoft Teams](https://teams.microsoft.com) e entre com sua conta de administrador de locatário do Office 365. Verifique se a equipe que você acabou de criar aparece e inclui os três canais criados `$batch` pela solicitação.

![Uma captura de tela do aplicativo Teams com a nova equipe e os canais mostrando](./images/team-channels.png)

Embora a ação `Batch POST-channels` acima tenha sido implementada neste tutorial como uma ação separada, as chamadas para criar os canais podem ter sido adicionadas como chamadas adicionais `Batch PUT-team` na ação. Isso criaria a equipe e todos os canais em uma única chamada em lote. Tente fazer isso por conta própria.

Por fim, lembre-se de que as chamadas [em lote JSON](https://docs.microsoft.com/graph/json-batching) retornarão um código de status HTTP para cada solicitação. Em um processo de produção, talvez você queira combinar o pós-processamento dos resultados com uma [`Apply to each`](https://docs.microsoft.com/flow/apply-to-each) ação e validar cada resposta individual tem um código de status 201 ou compensar outros códigos de status recebidos.