<!-- markdownlint-disable MD002 MD041 -->

Neste exercício, você criará um novo aplicativo do Azure Active Directory que será usado para fornecer as permissões delegadas para o conector personalizado.

Abra um navegador e navegue até o [centro de administração do Azure Active Directory](https://aad.portal.azure.com). Escolha o link do **Azure Active Directory** no menu de navegação à esquerda e, em seguida, escolha a entrada de **registros de aplicativos** na seção **gerenciar** da folha do **Azure Active Directory** .

![Uma captura de tela da lâmina do Azure Active Directory no centro de administração do Azure Active Directory](./images/app-reg-preview1.png)

Escolha o item de menu **novo registro** na parte superior da folha **registros de aplicativo** .

![Uma captura de tela da lâmina de registros de aplicativos no centro de administração do Azure Active Directory](./images/app-reg-preview2.png)

Insira `MS Graph Batch App` no campo **nome** . Na seção **tipos de conta com suporte** , selecione **contas em qualquer diretório organizacional**. Deixe a seção redirecionar **URI** em branco e escolha **registrar**.

![Uma captura de tela da folha registrar um aplicativo no centro de administração do Azure Active Directory](./images/app-reg-preview3.png)

Na folha do **aplicativo de lote do MS Graph** , copie a **ID do aplicativo (cliente)**. Você precisará disso no próximo exercício.

![Uma captura de tela da página de aplicativo registrado](./images/app-reg-preview4.png)

Escolha a entrada de **permissões de API** na seção **gerenciar** da folha do aplicativo de **lote do MS Graph** . Escolha **Adicionar uma permissão** em **permissões de API**.

![Uma captura de tela da lâmina de permissões de API](./images/app-perms-preview1.png)

Na folha **solicitar permissões de API** , escolha o **Microsoft Graph**e, em seguida, escolha **permissões delegadas**. `group`Procure e selecione a permissão delegada **ler e gravar todos os grupos** . Escolha **adicionar permissões** na parte inferior da folha.

 ![Uma captura de tela da lâmina solicitar permissões de API](./images/app-perms-preview2.png)

Escolha a entrada **certificados e segredos** na seção **gerenciar** da folha do **aplicativo de lote do MS Graph** e, em seguida, escolha **novo segredo do cliente**. Insira `forever` na **Descrição** e selecione **nunca** em **expirar**. Escolha **Adicionar**.

![Uma captura de tela da folha de certificados e segredos](./images/app-key-preview1.png)

Copie o valor da chave para a nova chave. Você precisará disso no próximo exercício.

![Uma captura de tela do novo segredo do cliente](./images/app-key-preview2.png)

> [!IMPORTANT]
> Esta etapa é crítica, pois a chave não estará acessível quando você fechar esta folha. Salve essa chave em um editor de texto para usá-lo nos próximos exercícios.

Para habilitar o gerenciamento de serviços adicionais que podem ser acessados por meio do Microsoft Graph, incluindo as propriedades do Teams, você precisaria selecionar escopos adicionais e apropriados para habilitar o gerenciamento de serviços específicos. Por exemplo, para estender nossa solução para habilitar a criação de blocos de anotações do OneNote ou planos do Planner, Buckets e tarefas, você precisaria adicionar os escopos de permissão necessários para as APIs relevantes.