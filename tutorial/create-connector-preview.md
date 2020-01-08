<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="b4d86-101">Neste exercício, você criará um novo conector personalizado que pode ser usado no fluxo ou em aplicativos de lógica do Azure.</span><span class="sxs-lookup"><span data-stu-id="b4d86-101">In this exercise, you will create a new custom connector which can be used in Flow or in Azure Logic Apps.</span></span> <span data-ttu-id="b4d86-102">O arquivo de definição de API aberto é pré-criado com o caminho correto para o ponto `$batch` de extremidade do Microsoft Graph e configurações adicionais para habilitar a importação simples.</span><span class="sxs-lookup"><span data-stu-id="b4d86-102">The Open API definition file is prebuilt with the correct path for the Microsoft Graph `$batch` endpoint and additional settings to enable simple import.</span></span>

<span data-ttu-id="b4d86-103">Usando um editor de texto, crie um novo arquivo vazio `MSGraph-Delegate-Batch.swagger.json` chamado e adicione o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b4d86-103">Using a text editor, create a new empty file named `MSGraph-Delegate-Batch.swagger.json` and add the following code.</span></span>

[!code-json[](../LabFiles/MSGraph-Delegate-Batch.swagger.json)]

<span data-ttu-id="b4d86-104">Abra um navegador e navegue até [Microsoft Flow](https://flow.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="b4d86-104">Open a browser and navigate to [Microsoft Flow](https://flow.microsoft.com).</span></span> <span data-ttu-id="b4d86-105">Entre com sua conta de administrador de locatário do Office 365.</span><span class="sxs-lookup"><span data-stu-id="b4d86-105">Sign in with your Office 365 tenant administrator account.</span></span> <span data-ttu-id="b4d86-106">No menu à esquerda, expanda **dados** e escolha **conectores personalizados**.</span><span class="sxs-lookup"><span data-stu-id="b4d86-106">In the left-hand menu, expand **Data** and choose **Custom connectors**.</span></span>

![Uma captura de tela do item de menu de conectores personalizados no Microsoft Flow](./images/flow-conn1.png)

<span data-ttu-id="b4d86-108">Na página **conectores personalizados** , escolha o link **novo conector personalizado** no canto superior direito e, em seguida, selecione o item **importar um arquivo do openapi** no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="b4d86-108">On the **Custom connectors** page choose the **New custom connector** link in the top right, then select the **Import an OpenAPI file** item in the drop-down menu.</span></span> <span data-ttu-id="b4d86-109">Insira `MS Graph Batch Connector` na caixa de texto **nome do conector** .</span><span class="sxs-lookup"><span data-stu-id="b4d86-109">Enter `MS Graph Batch Connector` in the **Connector name** text box.</span></span> <span data-ttu-id="b4d86-110">Escolha o botão **importar** para carregar o arquivo de API aberto.</span><span class="sxs-lookup"><span data-stu-id="b4d86-110">Choose **Import** button to upload the Open API file.</span></span> <span data-ttu-id="b4d86-111">Navegue até o `MSGraph-Delegate-Batch.swagger.json` arquivo que você criou.</span><span class="sxs-lookup"><span data-stu-id="b4d86-111">Browse to the `MSGraph-Delegate-Batch.swagger.json` file you created.</span></span> <span data-ttu-id="b4d86-112">Escolha **continuar** para carregar o arquivo openapi.</span><span class="sxs-lookup"><span data-stu-id="b4d86-112">Choose **Continue** to upload the OpenAPI file.</span></span>

 ![Uma captura de tela da caixa de diálogo Criar conector personalizado](./images/flow-conn3.png)

<span data-ttu-id="b4d86-114">Na página configuração do conector, escolha o link **segurança** no menu de navegação.</span><span class="sxs-lookup"><span data-stu-id="b4d86-114">On the connector configuration page, choose the **Security** link in the navigation menu.</span></span> <span data-ttu-id="b4d86-115">Preencha os campos da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="b4d86-115">Fill in the fields as follows.</span></span>

- <span data-ttu-id="b4d86-116">**Escolha qual autenticação é implementada por sua API**:`OAuth 2.0`</span><span class="sxs-lookup"><span data-stu-id="b4d86-116">**Choose what authentication is implemented by your API**: `OAuth 2.0`</span></span>
- <span data-ttu-id="b4d86-117">**Provedor de identidade**:`Azure Active Directory`</span><span class="sxs-lookup"><span data-stu-id="b4d86-117">**Identity Provider**: `Azure Active Directory`</span></span>
- <span data-ttu-id="b4d86-118">**ID do cliente**: a ID do aplicativo que você criou no exercício anterior</span><span class="sxs-lookup"><span data-stu-id="b4d86-118">**Client id**: the application ID you created in the previous exercise</span></span>
- <span data-ttu-id="b4d86-119">**Segredo do cliente**: a chave que você criou no exercício anterior</span><span class="sxs-lookup"><span data-stu-id="b4d86-119">**Client secret**: the key you created in the previous exercise</span></span>
- <span data-ttu-id="b4d86-120">**URL de logon**:`https://login.windows.net`</span><span class="sxs-lookup"><span data-stu-id="b4d86-120">**Login url**: `https://login.windows.net`</span></span>
- <span data-ttu-id="b4d86-121">**ID do locatário**:`common`</span><span class="sxs-lookup"><span data-stu-id="b4d86-121">**Tenant ID**: `common`</span></span>
- <span data-ttu-id="b4d86-122">**URL**do recurso `https://graph.microsoft.com` : (sem à direita/)</span><span class="sxs-lookup"><span data-stu-id="b4d86-122">**Resource URL**: `https://graph.microsoft.com` (no trailing /)</span></span>
- <span data-ttu-id="b4d86-123">**Escopo**: deixar em branco</span><span class="sxs-lookup"><span data-stu-id="b4d86-123">**Scope**: Leave blank</span></span>

<span data-ttu-id="b4d86-124">Escolha **criar conector** no canto superior direito</span><span class="sxs-lookup"><span data-stu-id="b4d86-124">Choose **Create Connector** on the top-right</span></span>

![Uma captura de tela da guia Segurança na configuração do conector](./images/flow-conn4.png)

<span data-ttu-id="b4d86-126">Após a criação do conector, copie a URL de **redirecionamento**gerada.</span><span class="sxs-lookup"><span data-stu-id="b4d86-126">After the connector has been created, copy the generated **Redirect URL**.</span></span>

![Uma captura de tela da URL de redirecionamento gerada](./images/flow-conn5.png)

<span data-ttu-id="b4d86-128">Volte para o aplicativo registrado no [portal do Azure](https://aad.portal.azure.com) que você criou no exercício anterior.</span><span class="sxs-lookup"><span data-stu-id="b4d86-128">Go back to the registered application in the [Azure Portal](https://aad.portal.azure.com) you created in the previous exercise.</span></span> <span data-ttu-id="b4d86-129">Selecione **visão geral** na folha do **aplicativo de lote do MS Graph** e, em seguida, selecione **Adicionar um URI de redirecionamento**.</span><span class="sxs-lookup"><span data-stu-id="b4d86-129">Select **Overview** on the **MS Graph Batch App** blade, then select **Add a Redirect URI**.</span></span> <span data-ttu-id="b4d86-130">Adicione a **URL de redirecionamento** que você copiou no campo **URI de redirecionamento** e escolha **salvar**.</span><span class="sxs-lookup"><span data-stu-id="b4d86-130">Add the **Redirect URL** you copied in the **Redirect URI** field and choose **Save**.</span></span>

![Uma captura de tela da lâmina URLs de resposta no portal do Azure](./images/flow-conn-preview6.png)
