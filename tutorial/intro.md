<!-- markdownlint-disable MD002 MD041 -->

Há mais de 230 conectores de caixa de entrada para o Microsoft Flow. Muitos desses conectores usam o Microsoft Graph para se comunicar com pontos de extremidade específicos de produtos da Microsoft, mas não há conectores que se comunicam diretamente com o Microsoft Graph para cobrir toda a API. No entanto, há situações em que pode ser necessário chamar o Microsoft Graph diretamente do fluxo usando blocos de construção básicos do serviço.

Além de abordar cenários para chamar o Microsoft Graph diretamente, vários pontos de extremidade da API do Microsoft Graph só dão suporte a [permissões delegadas](https://docs.microsoft.com/graph/permissions-reference). O conector HTTP no Microsoft Flow permite integrações muito flexíveis, incluindo chamar o Microsoft Graph. No entanto, o conector HTTP não tem a capacidade de armazenar em cache as credenciais de um usuário para habilitar cenários de permissão delegada específicos. Nesses casos, um conector personalizado pode ser criado para fornecer um invólucro em torno da API do Microsoft Graph e habilitar o consumo da API com permissões delegadas.

Este laboratório aborda os dois desafios acima. Primeiro, você criará um conector personalizado para habilitar as integrações com o Microsoft Graph, que exigem [permissões delegadas](https://docs.microsoft.com/graph/permissions-reference). Em segundo lugar, você usará o [ponto de extremidade de solicitação $batch](https://docs.microsoft.com/graph/json-batching), para fornecer acesso a todo o poder do Microsoft Graph enquanto usa as permissões delegadas que exigem que um aplicativo tenha um usuário "conectado".

> [!NOTE]
> Este é um tutorial sobre como criar um conector personalizado para uso no Microsoft Flow e no Azure LogicApps. Este tutorial pressupõe que você tenha lido a [visão geral do conector personalizado](https://docs.microsoft.com/connectors/custom-connectors/) para entender o processo.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este exercício nesta postagem, você precisará do seguinte:

- Acesso de administrador a uma locação do Office 365. Se você não tiver um, visite o [programa para desenvolvedores do Office 365](https://developer.microsoft.com/office/dev-program) para se inscrever de um locatário de desenvolvedor gratuito.
- Acesso ao [Microsoft Flow](https://flow.microsoft.com/).

## <a name="feedback"></a>Comentários

Forneça comentários sobre este tutorial no [repositório do GitHub](https://github.com/microsoftgraph/msgraph-training-microsoftflow).
