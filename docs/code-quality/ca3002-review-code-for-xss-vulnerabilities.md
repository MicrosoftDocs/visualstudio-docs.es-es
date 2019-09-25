---
title: 'CA3002: Revisión de código en busca de vulnerabilidades de XSS'
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
ms.openlocfilehash: 6bcf32401abdeae499097bc5187d11154e7dfc6e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237417"
---
# <a name="ca3002-review-code-for-xss-vulnerabilities"></a>CA3002: Revisión de código en busca de vulnerabilidades de XSS

|||
|-|-|
|TypeName|ReviewCodeForXssVulnerabilities|
|Identificador de comprobación|CA3002|
|Categoría|Microsoft.Security|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

La entrada de la solicitud HTTP que podría no ser de confianza llega a la salida HTML sin formato.

## <a name="rule-description"></a>Descripción de la regla

Al trabajar con una entrada que no es de confianza de las solicitudes Web, tenga en cuentan los ataques de scripting entre sitios (XSS). Un ataque XSS inyecta entradas que no son de confianza en salidas HTML sin procesar, lo que permite al atacante ejecutar scripts malintencionados o modificar contenido de forma malintencionada en la Página Web. Una técnica típica consiste en `<script>` colocar elementos con código malintencionado en la entrada. Para obtener más información, consulte [XSS de OWASP](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)).

Esta regla intenta buscar la entrada de las solicitudes HTTP que llegan a la salida HTML sin formato.

> [!NOTE]
> Esta regla no puede realizar el seguimiento de los datos entre ensamblados. Por ejemplo, si un ensamblado lee la entrada de la solicitud HTTP y, a continuación, la pasa a otro ensamblado que genera HTML sin formato, esta regla no generará una advertencia.

> [!NOTE]
> Existe un límite configurable en cuanto a la profundidad con que esta regla analizará el flujo de datos a través de las llamadas a métodos. Vea [configuración del analizador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) para saber cómo configurar el límite en un archivo EditorConfig.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

- En lugar de generar código HTML sin formato, use un método o propiedad que primero codifique en HTML su entrada.
- Codifique los datos que no son de confianza en HTML antes de generar HTML sin formato.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla si:
- Sabe que la entrada se valida con un conjunto de caracteres seguro conocido que no contiene HTML.
- Sabe que los datos están codificados en HTML de forma que esta regla no los detecte.

> [!NOTE]
> Esta regla puede notificar falsos positivos para algunos métodos o propiedades que codifican en HTML su entrada.

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

### <a name="violation"></a>Infracción

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        Response.Write("<HTML>" + input + "</HTML>");
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Me.Request.Form("in")
        Me.Response.Write("<HTML>" + input + "</HTML>")
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

        // Example usage of System.Web.HttpServerUtility.HtmlEncode().
        Response.Write("<HTML>" + Server.HtmlEncode(input) + "</HTML>");
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Me.Request.Form("in")

        ' Example usage of System.Web.HttpServerUtility.HtmlEncode().
        Me.Response.Write("<HTML>" + Me.Server.HtmlEncode(input) + "</HTML>")
    End Sub
End Class
```