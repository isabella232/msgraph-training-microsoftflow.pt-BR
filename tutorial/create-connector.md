<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="ff231-101">Neste exercício, você criará um novo conector personalizado que pode ser usado no fluxo ou em aplicativos de lógica do Azure.</span><span class="sxs-lookup"><span data-stu-id="ff231-101">In this exercise, you will create a new custom connector which can be used in Flow or in Azure Logic Apps.</span></span> <span data-ttu-id="ff231-102">O arquivo de definição de API aberto é pré-criado com o caminho correto para o ponto `$batch` de extremidade do Microsoft Graph e configurações adicionais para habilitar a importação simples.</span><span class="sxs-lookup"><span data-stu-id="ff231-102">The Open API definition file is prebuilt with the correct path for the Microsoft Graph `$batch` endpoint and additional settings to enable simple import.</span></span>

<span data-ttu-id="ff231-103">Usando um editor de texto, crie um novo arquivo vazio `MSGraph-Delegate-Batch.swagger.json` chamado e adicione o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ff231-103">Using a text editor, create a new empty file named `MSGraph-Delegate-Batch.swagger.json` and add the following code.</span></span>

[!code-json[](../LabFiles/MSGraph-Delegate-Batch.swagger.json)]

<span data-ttu-id="ff231-104">Abra um navegador e navegue até [Microsoft Flow](https://flow.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="ff231-104">Open a browser and navigate to [Microsoft Flow](https://flow.microsoft.com).</span></span> <span data-ttu-id="ff231-105">Entre com sua conta de administrador de locatário do Office 365.</span><span class="sxs-lookup"><span data-stu-id="ff231-105">Sign in with your Office 365 tenant administrator account.</span></span> <span data-ttu-id="ff231-106">Escolha o ícone de engrenagem no canto superior direito e selecione o item **conectorEs personalizados** no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="ff231-106">Choose the gear icon in the upper right, and select the **Custom Connectors** item in the drop-down menu.</span></span>

![Uma captura de tela do menu suspenso no Microsoft Flow](./images/flow-conn1.png)

<span data-ttu-id="ff231-108">Na página **conectorEs personalizados** , escolha o link **criar conector personalizado** no canto superior direito e, em seguida, selecione o item **importar um arquivo de API aberto** no menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="ff231-108">On the **Custom Connectors** page choose the **Create custom connector** link in the top right, then select the **Import an Open API file** item in the drop-down menu.</span></span>

 ![Uma captura de tela do menu suspenso criar conector personalizado no Microsoft Flow](./images/flow-conn2.png)

<span data-ttu-id="ff231-110">Insira `MS Graph Batch Connector` na caixa de texto **nome do conector personalizado** .</span><span class="sxs-lookup"><span data-stu-id="ff231-110">Enter `MS Graph Batch Connector` in the **Custom connector name** text box.</span></span> <span data-ttu-id="ff231-111">Escolha o ícone de pasta para carregar o arquivo de API aberto.</span><span class="sxs-lookup"><span data-stu-id="ff231-111">Choose the folder icon to upload the Open API file.</span></span> <span data-ttu-id="ff231-112">Navegue até o `MSGraph-Delegate-Batch.swagger.json` arquivo que você criou.</span><span class="sxs-lookup"><span data-stu-id="ff231-112">Browse to the `MSGraph-Delegate-Batch.swagger.json` file you created.</span></span> <span data-ttu-id="ff231-113">Escolha **continuar** para carregar o arquivo de API aberto.</span><span class="sxs-lookup"><span data-stu-id="ff231-113">Choose **Continue** to upload the Open API file.</span></span>

 ![Uma captura de tela da caixa de diálogo Criar conector personalizado](./images/flow-conn3.png)

<span data-ttu-id="ff231-115">Na página configuração do conector, escolha o link **segurança** no menu de navegação.</span><span class="sxs-lookup"><span data-stu-id="ff231-115">On the connector configuration page, choose the **Security** link in the navigation menu.</span></span> <span data-ttu-id="ff231-116">Preencha os campos da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="ff231-116">Fill in the fields as follows.</span></span>

- <span data-ttu-id="ff231-117">**Escolha qual autenticação é implementada por sua API**:`OAuth 2.0`</span><span class="sxs-lookup"><span data-stu-id="ff231-117">**Choose what authentication is implemented by your API**: `OAuth 2.0`</span></span>
- <span data-ttu-id="ff231-118">**Provedor de identidade**:`Azure Active Directory`</span><span class="sxs-lookup"><span data-stu-id="ff231-118">**Identity Provider**: `Azure Active Directory`</span></span>
- <span data-ttu-id="ff231-119">**ID do cliente**: a ID do aplicativo que você criou no exercício anterior</span><span class="sxs-lookup"><span data-stu-id="ff231-119">**Client id**: the application ID you created in the previous exercise</span></span>
- <span data-ttu-id="ff231-120">**Segredo do cliente**: a chave que você criou no exercício anterior</span><span class="sxs-lookup"><span data-stu-id="ff231-120">**Client secret**: the key you created in the previous exercise</span></span>
- <span data-ttu-id="ff231-121">**URL de logon**:`https://login.windows.net`</span><span class="sxs-lookup"><span data-stu-id="ff231-121">**Login url**: `https://login.windows.net`</span></span>
- <span data-ttu-id="ff231-122">**ID do locatário**:`common`</span><span class="sxs-lookup"><span data-stu-id="ff231-122">**Tenant ID**: `common`</span></span>
- <span data-ttu-id="ff231-123">**URL**do recurso `https://graph.microsoft.com` : (sem à direita/)</span><span class="sxs-lookup"><span data-stu-id="ff231-123">**Resource URL**: `https://graph.microsoft.com` (no trailing /)</span></span>
- <span data-ttu-id="ff231-124">**Escopo**: deixar em branco</span><span class="sxs-lookup"><span data-stu-id="ff231-124">**Scope**: Leave blank</span></span>

<span data-ttu-id="ff231-125">Escolha **criar conector** no canto superior direito</span><span class="sxs-lookup"><span data-stu-id="ff231-125">Choose **Create Connector** on the top-right</span></span>

![Uma captura de tela da guia Segurança na configuração do conector](./images/flow-conn4.png)

<span data-ttu-id="ff231-127">Após a criação do conector, copie a **URL**de redirecionamento gerada.</span><span class="sxs-lookup"><span data-stu-id="ff231-127">After the connector has been created, copy the generated **Redirect URL**.</span></span>

![Uma captura de tela da URL de reDirecionamento gerada](./images/flow-conn5.png)

<span data-ttu-id="ff231-129">Volte para o aplicativo registrado no [portal do Azure](https://aad.portal.azure.com) que você criou no exercício anterior.</span><span class="sxs-lookup"><span data-stu-id="ff231-129">Go back to the registered application in the [Azure Portal](https://aad.portal.azure.com) you created in the previous exercise.</span></span> <span data-ttu-id="ff231-130">Selecione **responder URLs** na folha **configurações** .</span><span class="sxs-lookup"><span data-stu-id="ff231-130">Select **Reply URLs** in the **Settings** blade.</span></span> <span data-ttu-id="ff231-131">Adicione a **URL** de redirecionamento que você copiou como uma **URL de resposta**adicional.</span><span class="sxs-lookup"><span data-stu-id="ff231-131">Add the **Redirect URL** you copied as an additional **Reply URL**.</span></span> <span data-ttu-id="ff231-132">Salve o aplicativo no portal do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="ff231-132">Save the application in Azure Active Directory portal.</span></span>

![Uma captura de tela da lâmina URLs de resposta no portal do Azure](./images/flow-conn6.png)