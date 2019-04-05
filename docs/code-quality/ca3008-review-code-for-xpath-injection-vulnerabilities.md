---
title: 'CA3008: Revisión de código para vulnerabilidades por inyección de XPath'
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
ms.openlocfilehash: e66b75160df0e8ecf9d33601ee383ec71cd62c4d
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018578"
---
# <a name="ca3008-review-code-for-xpath-injection-vulnerabilities"></a>CA3008: Revisión de código para vulnerabilidades por inyección de XPath

|||
|-|-|
|TypeName|ReviewCodeForXPathInjectionVulnerabilities|
|Identificador de comprobación|CA3008|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Entrada de solicitud HTTP potencialmente no confiable alcanza una consulta XPath.

## <a name="rule-description"></a>Descripción de la regla

Al trabajar con entradas no seguras, esté atento a ataques de inyección de XPath. Construir consultas de XPath utilizando la entrada no confiable puede permitir que un atacante manipular de forma malintencionada la consulta para devolver un resultado no deseado y posiblemente revelar el contenido del XML consultado. 

Esta regla intenta encontrar la entrada de las solicitudes HTTP para llegar a una expresión XPath.

> [!NOTE]
> Esta regla no puede realizar un seguimiento de datos a través de ensamblados. Por ejemplo, si un ensamblado lee la entrada de solicitud HTTP y, a continuación, pasa a otro ensamblado que realiza una consulta XPath, esta regla no genera una advertencia.

> [!NOTE]
> Hay un límite configurable para profundidad esta regla analizará el flujo de datos a través de llamadas de método. Consulte [Configuration Analyzer](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) para configurar el límite de `.editorconfig` archivos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Se incluyen algunos enfoques para corregir las vulnerabilidades por inyección de código de XPath:

- No crear consultas de XPath de entrada del usuario.
- Validar que la entrada contiene sólo un juego de caracteres segura.
- Escape las comillas.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Si sabe que ha validado la entrada para que sean seguras, es correcto suprimir esta advertencia.

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
