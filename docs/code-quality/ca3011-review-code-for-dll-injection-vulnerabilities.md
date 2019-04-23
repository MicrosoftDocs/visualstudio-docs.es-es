---
title: 'CA3011: Revisión de código en busca de vulnerabilidades de inyección de DLL'
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
ms.openlocfilehash: a6f3a2db89e35408a19cec47c971821fedf5f85a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60089549"
---
# <a name="ca3011-review-code-for-dll-injection-vulnerabilities"></a>CA3011: Revisión de código en busca de vulnerabilidades de inyección de DLL

|||
|-|-|
|TypeName|ReviewCodeForDllInjectionVulnerabilities|
|Identificador de comprobación|CA3011|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Solicitud HTTP potencialmente no confiable entrada llega a un método que carga un ensamblado.

## <a name="rule-description"></a>Descripción de la regla

Al trabajar con entradas no seguras, esté atento al cargar el código no seguro. Si la aplicación web carga código no seguro, un atacante puede insertar archivos DLL malintencionado en su proceso y ejecutar código malintencionado.

Esta regla intenta encontrar la entrada de una solicitud HTTP que llegue a un método que carga un ensamblado.

> [!NOTE]
> Esta regla no puede realizar un seguimiento de datos a través de ensamblados. Por ejemplo, si un ensamblado lee la entrada de solicitud HTTP y, a continuación, pasa a otro ensamblado que carga un ensamblado, esta regla no genera una advertencia.

> [!NOTE]
> Hay un límite configurable para profundidad esta regla analizará el flujo de datos a través de llamadas de método. Consulte [Configuration Analyzer](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) para configurar el límite de `.editorconfig` archivos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

No se cargan archivos DLL que no se confía por el usuario.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

### <a name="violation"></a>Infracción

```csharp
using System;
using System.Reflection;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        byte[] rawAssembly = Convert.FromBase64String(input);
        Assembly.Load(rawAssembly);
    }
}
```

```vb
Imports System
Imports System.Reflection

Public Partial Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Request.Form("in")
        Dim rawAssembly As Byte() = Convert.FromBase64String(input)
        Assembly.Load(rawAssembly)
    End Sub
End Class
```
