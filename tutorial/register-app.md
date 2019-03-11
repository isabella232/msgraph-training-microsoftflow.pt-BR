<!-- markdownlint-disable MD002 MD041 -->

Neste exercício, você criará um novo aplicativo do Azure Active Directory que será usado para fornecer as permissões delegadas para o conector personalizado.

Abra um navegador e navegue até o [centro de administração do Azure Active Directory](https://aad.portal.azure.com). Escolha o link do **Azure Active Directory** no menu de navegação à esquerda e, em seguida, escolha a entrada de **registros de aplicativos** na seção **gerenciar** da folha do **Azure Active Directory** .

![Uma captura de tela da lâmina do Azure Active Directory no centro de administração do Azure Active Directory](./images/app-reg1.png)

Escolha o item de menu **novo aplicativo de registro** na parte superior da folha **registros de aplicativos** .

![Uma captura de tela da lâmina de registros de aplicativos no centro de administração do Azure Active Directory](./images/app-reg2.png)

Insira `MS Graph Batch App` no campo **nome** e `https://localhost.com/$batch` , no campo **URL de logon** e escolha **criar**.

![Uma captura de tela do formulário criar para um novo registro de aplicativo no centro de administração do Azure Active Directory](./images/app-reg3.png)

Na página do **aplicativo de lote do MS Graph** , copie a **ID do aplicativo** do aplicativo. Você precisará disso no próximo exercício.

![Uma captura de tela da página de aplicativo registrado](./images/app-reg4.png)

Escolha as **configurações** engrenagem sob o nome do aplicativo e, em seguida, escolha o item de menu **permissões necessárias** na folha configurações. Escolha **Adicionar** na parte superior da folha **permissões necessárias** .

![Uma captura de tela da lâmina de permissões necessárias](./images/app-perms1.png)

Escolha a opção **selecionar uma API** na folha de **acesso Adicionar API** e selecione o item **Microsoft Graph** e escolha **selecionar** na parte inferior da folha.

![Uma captura de tela da folha selecionar uma API](./images/app-perms2.png)

Na folha **habilitar acesso** , role para baixo até a seção **permissões delegadas** . Selecione a permissão delegada **ler e gravar todos os grupos** e, em seguida, escolha **selecionar** na parte inferior da folha. Escolha **concluído** na parte inferior da folha **Adicionar acesso à API** .

 ![Uma captura de tela do habilitar lâmina de acesso](./images/app-perms3.png)

Escolha o item de menu **Keys** na folha **configurações** . Insira `forever` a **Descrição da chave** e selecione **nunca expira** no menu suspenso **duração** . Escolha **salvar** na parte superior da folha de **chaves** . Copie o valor da chave para a nova chave. Você precisará disso no próximo exercício.

![Uma captura de tela da folha de chaves](./images/app-key1.png)

> [!IMPORTANT]
> Esta etapa é crítica, pois a chave não estará acessível quando você fechar esta folha. Salve essa chave em um editor de texto para usá-lo nos próximos exercícios.

Para habilitar o gerenciamento de serviços adicionais que podem ser acessados por meio do Microsoft Graph, incluindo as propriedades do Teams, você precisaria selecionar escopos adicionais e apropriados para habilitar o gerenciamento de serviços específicos. Por exemplo, para estender nossa solução para habilitar a criação de blocos de anotações do OneNote ou planos do Planner, Buckets e tarefas, você precisaria adicionar os escopos de permissão necessários para as APIs relevantes.