---
title: 'CA3012: Revisión de código para el tipo de vulnerabilidades por inyección de código'
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
ms.openlocfilehash: 114b44ec566554c81f5caf3b8ac474f9c5a75c07
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018586"
---
# <a name="ca3012-review-code-for-regex-injection-vulnerabilities"></a>CA3012: Revisión de código para el tipo de vulnerabilidades por inyección de código

|||
|-|-|
|TypeName|ReviewCodeForRegexInjectionVulnerabilities|
|Identificador de comprobación|CA3012|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Entrada de solicitud HTTP potencialmente no confiable alcanza una expresión regular.

## <a name="rule-description"></a>Descripción de la regla

Al trabajar con entradas no seguras, esté atento a ataques de inyección de regex. Un atacante puede usar la inserción de regex para modificar una expresión regular, para que la expresión regular coincida con los resultados no deseados o para hacer que la expresión regular consumir cantidad excesiva de CPU resultante en un ataque de denegación de servicio de forma malintencionada.

Esta regla intenta encontrar la entrada de las solicitudes HTTP para llegar a una expresión regular.

> [!NOTE]
> Esta regla no puede realizar un seguimiento de datos a través de ensamblados. Por ejemplo, si un ensamblado lee la entrada de solicitud HTTP y, a continuación, pasa a otro ensamblado que se crea una expresión regular, esta regla no genera una advertencia.

> [!NOTE]
> Hay un límite configurable para profundidad esta regla analizará el flujo de datos a través de llamadas de método. Consulte [Configuration Analyzer](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) para configurar el límite de `.editorconfig` archivos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Se incluyen algunas de las mitigaciones frente a inyecciones de regex:

- Use siempre un [coincide con el tiempo de espera](/dotnet/standard/base-types/best-practices#use-time-out-values) al utilizar expresiones regulares.
- Evite el uso de expresiones regulares según la entrada del usuario.
- Caracteres especiales de escape de entrada del usuario mediante una llamada a <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=fullName> u otro método.
- Permitir solo especial que no son caracteres de entrada del usuario.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Si sabe que está usando un [coincide con el tiempo de espera](/dotnet/standard/base-types/best-practices#use-time-out-values) y la entrada del usuario es libre de caracteres especiales, no pasa nada suprimir esta advertencia.

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

### <a name="violation"></a>Infracción

```csharp
using System;
using System.Text.RegularExpressions;

public partial class WebForm : System.Web.UI.Page
{
    public string SearchableText { get; set; }

    protected void Page_Load(object sender, EventArgs e)
    {
        string findTerm = Request.Form["findTerm"];
        Match m = Regex.Match(SearchableText, "^term=" + findTerm);
    }
}
```

```vb
Imports System
Imports System.Text.RegularExpressions

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Public Property SearchableText As String

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim findTerm As String = Request.Form("findTerm")
        Dim m As Match = Regex.Match(SearchableText, "^term=" + findTerm)
    End Sub
End Class
```
