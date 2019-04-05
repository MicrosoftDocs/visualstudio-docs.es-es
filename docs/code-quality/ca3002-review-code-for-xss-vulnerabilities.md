---
title: 'CA3002: Revisión de código para las vulnerabilidades XSS'
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
ms.openlocfilehash: a10f72297746a1e7bda3c69f8f7daf0efacd20bc
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018672"
---
# <a name="ca3002-review-code-for-xss-vulnerabilities"></a>CA3002: Revisión de código para las vulnerabilidades XSS

|||
|-|-|
|TypeName|ReviewCodeForXssVulnerabilities|
|Identificador de comprobación|CA3002|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Entrada de solicitud HTTP potencialmente no confiable alcanza la salida HTML sin procesar.

## <a name="rule-description"></a>Descripción de la regla

Al trabajar con entradas no seguras de las solicitudes web, esté atento cross-site scripting (XSS) ataques. Un ataque XSS inserta la entrada que no se confía en HTML sin formato de salida, lo que permite al atacante ejecutar los scripts malintencionados o modificar contenido en la página web de forma malintencionada. Una técnica habitual es colocar `<script>` elementos con código malintencionado en la entrada. Para obtener más información, consulte [XSS de OWASP](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)).

Esta regla intenta encontrar la entrada de las solicitudes HTTP que llegue a la salida HTML sin procesar.

> [!NOTE]
> Esta regla no puede realizar un seguimiento de datos a través de ensamblados. Por ejemplo, si un ensamblado lee la entrada de solicitud HTTP y, a continuación, pasa a otro ensamblado que genera el código HTML sin procesar, esta regla no genera una advertencia.

> [!NOTE]
> Hay un límite configurable para profundidad esta regla analizará el flujo de datos a través de llamadas de método. Consulte [Configuration Analyzer](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) para configurar el límite de `.editorconfig` archivos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

- En lugar de generar HTML sin formato, use un método o propiedad esa primera codifica en HTML su entrada.
- Datos no de confianza para codificar en HTML antes de generar HTML sin formato.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla si:
- Sabrá que se valida la entrada con un conjunto conocido de prueba de errores de caracteres que no contiene código HTML.
- Sabrá que los datos están codificados en HTML de una manera no detectada por esta regla.

> [!NOTE]
> Esta regla puede notificar falsos positivos para algunos métodos o propiedades que codificar en HTML su entrada.

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