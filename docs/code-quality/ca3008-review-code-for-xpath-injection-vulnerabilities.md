---
title: 'CA3008: Revisión de código en busca de vulnerabilidades de inyección de XPath'
ms.date: 04/03/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1d001dc306bbb225c4ecc1c0f17bf46619e2d0a7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237263"
---
# <a name="ca3008-review-code-for-xpath-injection-vulnerabilities"></a>CA3008: Revisión de código en busca de vulnerabilidades de inyección de XPath

|||
|-|-|
|TypeName|ReviewCodeForXPathInjectionVulnerabilities|
|Identificador de comprobación|CA3008|
|Categoría|Microsoft.Security|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Una entrada de solicitud HTTP que podría no ser de confianza llega a una consulta XPath.

## <a name="rule-description"></a>Descripción de la regla

Al trabajar con una entrada que no es de confianza, tenga en cuentan los ataques por inyección de XPath. La construcción de consultas XPath mediante la entrada que no es de confianza puede permitir a un atacante manipular de forma malintencionada la consulta para devolver un resultado no deseado y, posiblemente, divulgar el contenido del XML consultado.

Esta regla intenta buscar la entrada de las solicitudes HTTP que llegan a una expresión XPath.

> [!NOTE]
> Esta regla no puede realizar el seguimiento de los datos entre ensamblados. Por ejemplo, si un ensamblado lee la entrada de la solicitud HTTP y, a continuación, la pasa a otro ensamblado que realiza una consulta XPath, esta regla no generará ninguna advertencia.

> [!NOTE]
> Existe un límite configurable en cuanto a la profundidad con que esta regla analizará el flujo de datos a través de las llamadas a métodos. Vea [configuración del analizador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) para saber cómo configurar el límite en un archivo EditorConfig.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Algunos enfoques para corregir las vulnerabilidades de inyección de XPath incluyen:

- No construya consultas XPath a partir de datos proporcionados por el usuario.
- Compruebe que la entrada solo contiene un conjunto seguro de caracteres.
- Comillas de escape.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Si sabe que ha validado la entrada para que sea segura, puede suprimir esta advertencia.

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

### <a name="violation"></a>Infracción

```csharp
using System;
using System.Xml.XPath;

public partial class WebForm : System.Web.UI.Page
{
    public XPathNavigator AuthorizedOperations { get; set; }

    protected void Page_Load(object sender, EventArgs e)
    {
        string operation = Request.Form["operation"];

        // If an attacker uses this for input:
        //     ' or 'a' = 'a
        // Then the XPath query will be:
        //     authorizedOperation[@username = 'anonymous' and @operationName = '' or 'a' = 'a']
        // and it will return any authorizedOperation node.
        XPathNavigator node = AuthorizedOperations.SelectSingleNode(
            "//authorizedOperation[@username = 'anonymous' and @operationName = '" + operation + "']");
    }
}
```

```vb
Imports System
Imports System.Xml.XPath

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Public Property AuthorizedOperations As XPathNavigator

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim operation As String = Me.Request.Form("operation")

        ' If an attacker uses this for input:
        '     ' or 'a' = 'a
        ' Then the XPath query will be:
        '      authorizedOperation[@username = 'anonymous' and @operationName = '' or 'a' = 'a']
        ' and it will return any authorizedOperation node.
        Dim node As XPathNavigator = AuthorizedOperations.SelectSingleNode( _
            "//authorizedOperation[@username = 'anonymous' and @operationName = '" + operation + "']")
    End Sub
End Class
```
