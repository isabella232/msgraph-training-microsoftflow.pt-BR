<!-- markdownlint-disable MD002 MD041 -->

Neste exercício, você criará um fluxo para usar o conector personalizado que você criou nos exercícios anteriores para criar e configurar uma equipe da Microsoft. O fluxo usará o conector personalizado para enviar uma solicitação POST para criar um grupo uniFicado do Office 365, pausará um atraso enquanto a criação do grupo for concluída e, em seguida, enviará uma solicitação PUT para associar o grupo a uma equipe da Microsoft.

No final, seu fluxo será semelhante à seguinte imagem:

![Uma captura de tela do fluxo concluído](./images/flow-team1.png)

Abra o [Microsoft Flow](https://flow.microsoft.com) no seu navegador e entre com sua conta de administrador de locatário do Office 365. Escolha **meus fluxos** na navegação à esquerda. Escolha **novo**e, em seguida, **criar de em branco**. Escolha **criar de em branco**. Insira `Manual` na caixa de pesquisa e adicione o disparador de **fluxo do gatilho manualmente** .

Escolha **Adicionar uma entrada**, selecione **texto** e Enter `Name` como o título.

![Uma captura de tela do gatilho manual de um gatilho de fluxo](./images/flow-team6.png)

Escolha **nova etapa** e digite `Batch` na caixa de pesquisa. Adicione a ação do **conector de lotes do MS Graph** . Escolha as reticências e renomeie `Batch POST-groups`esta ação como.

Adicione o seguinte código à caixa de texto **corpo** da ação.

```json
{
  "requests": [
    {
      "url": "/groups",
      "method": "POST",
      "id": 1,
      "headers": { "Content-Type": "application/json" },
      "body": {
        "description": "REPLACE",
        "displayName": "REPLACE",
        "groupTypes": ["Unified"],
        "mailEnabled": true,
        "mailNickname": "REPLACE",
        "securityEnabled": false
      }
    }
  ]
}
```

Substitua cada `REPLACE` espaço reservado selecionando `Name` o valor do disparador manual no menu **adicionar conteúdo dinâmico** .

![Uma captura de tela do menu de conteúdo dinâmico no Microsoft Flow](./images/flow-team2.png)

Escolha **nova etapa**, procure `delay` e adicione uma ação de **atraso** e configure por um minuto.

Escolha **nova etapa** e digite `Batch` na caixa de pesquisa. Adicione a ação do **conector de lotes do MS Graph** . Escolha as reticências e renomeie `Batch PUT-team`esta ação como.

Adicione o seguinte código à caixa de texto **corpo** da ação.

```json
{
  "requests": [
    {
      "id": 1,
      "url": "/groups/REPLACE/team",
      "method": "PUT",
      "headers": {
        "Content-Type": "application/json"
      },
      "body": {
        "memberSettings": {
          "allowCreateUpdateChannels": true
        },
        "messagingSettings": {
          "allowUserEditMessages": true,
          "allowUserDeleteMessages": true
        },
        "funSettings": {
          "allowGiphy": true,
          "giphyContentRating": "strict"
        }
      }
    }
  ]
}
```

Selecione o `REPLACE` espaço reservado e, em seguida, selecione **expressão** no painel conteúdo dinâmico. Adicione a seguinte fórmula à **expressão**.

```js
body('Batch_POST-groups').responses[0].body.id
```

![Uma captura de tela da expressão no painel de conteúdo dinâmico](./images/flow-formula.png)

Essa fórmula especifica que queremos usar a ID de grupo do resultado da primeira ação.

![Uma captura de tela do corpo da ação atualizado](./images/flow-team3.png)

Escolha **salvar**, fluxo e escolha **testar** para executar o fluxo.

> [!TIP]
> Se você receber uma mensagem de `The template validation failed: 'The action(s) 'Batch_POST-groups' referenced by 'inputs' in action 'Batch_2' are not defined in the template'`erro, a expressão está incorreta e provavelmente faz referência a uma ação de fluxo que não consegue localizar. Verifique se o nome da ação que você está fazendo referência corresponde exatamente.

Escolha o botão de opção **eu executarei a ação do gatilho** e escolha **salvar & Test**. Escolha **continuar** na caixa de diálogo. Forneça um nome sem espaços e escolha **executar fluxo** para criar uma equipe.

![Uma captura de tela da caixa de diálogo Executar fluxo](./images/flow-team4.png)

Por fim, escolha o link **Exibir atividade de execução de fluxo** e, em seguida, selecione o fluxo de execução para ver o log de atividades.

> [!NOTE]
> Talvez seja necessário clicar em sua instância de fluxo em execução na lista executar histórico para exibir a execução do fluxo.

Depois que o fluxo é concluído, seu grupo do Office 365 e sua equipe foram configurados. Selecione os itens de ação em lote para exibir os resultados das chamadas em lote JSON. O `outputs` da `Batch PUT-team` ação deve ter um código de status de 201 para uma associação de equipe bem-sucedida semelhante à imagem abaixo.

![Uma captura de tela do log de atividades de fluxo bem-sucedido](./images/flow-team5.png)