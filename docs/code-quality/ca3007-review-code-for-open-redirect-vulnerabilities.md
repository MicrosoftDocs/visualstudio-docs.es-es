---
title: 'CA3007: Revisión de código en busca de vulnerabilidades de redireccionamiento abierto'
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
ms.openlocfilehash: e60d0fad1262138b57f079485bc7455e55c7ec25
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841342"
---
# <a name="ca3007-review-code-for-open-redirect-vulnerabilities"></a>CA3007: Revisión de código en busca de vulnerabilidades de redireccionamiento abierto

|||
|-|-|
|TypeName|ReviewCodeForOpenRedirectVulnerabilities|
|Identificador de comprobación|CA3007|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Entrada de solicitud HTTP potencialmente no confiable alcanza una redirección de respuesta HTTP.

## <a name="rule-description"></a>Descripción de la regla

Al trabajar con entradas no seguras, esté atento vulnerabilidades de redireccionamiento abierto. Un atacante puede aprovechar una vulnerabilidad de redireccionamiento abierto para usar su sitio Web para darle el aspecto de una dirección URL válida, pero redirigir un visitante confiado a una suplantación de identidad o a otra página Web malintencionado.

Esta regla intenta encontrar la entrada de las solicitudes HTTP para llegar a una dirección URL de redireccionamiento HTTP.

> [!NOTE]
> Esta regla no puede realizar un seguimiento de datos a través de ensamblados. Por ejemplo, si un ensamblado lee la entrada de solicitud HTTP y, a continuación, pasa a otro ensamblado al que responde con una redirección de HTTP, esta regla no genera una advertencia.

> [!NOTE]
> Hay un límite configurable para profundidad esta regla analizará el flujo de datos a través de llamadas de método. Consulte [Configuration Analyzer](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) acerca de cómo configurar el límite en un archivo EditorConfig.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Algunos enfoques para corregir las vulnerabilidades de redireccionamiento abierto incluyen:

- No permita que los usuarios iniciar redirecciones.
- No permitir a los usuarios especificar cualquier parte de la dirección URL en un escenario de redirección.
- Restringir las redirecciones a una predefinido "lista de permitidos" de las direcciones URL.
- Validar las direcciones URL de redireccionamiento.
- Si procede, considere la posibilidad de usar una página de declinación de responsabilidades cuando se le redirige a los usuarios fuera de su sitio.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Si sabe que ha validado la entrada para limitarse a direcciones URL previstas, es correcto suprimir esta advertencia.

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

### <a name="violation"></a>Infracción

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["url"];
        this.Response.Redirect(input);
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Dim input As String = Me.Request.Form("url")
        Me.Response.Redirect(input)
    End Sub
End Class
```

### <a name="solution"></a>Soluciones

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        if (String.IsNullOrWhiteSpace(input))
        {
            this.Response.Redirect("https://example.org/login.html");
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Dim input As String = Me.Request.Form("in")
        If String.IsNullOrWhiteSpace(input) Then
            Me.Response.Redirect("https://example.org/login.html")
        End If
    End Sub
End Class
```
