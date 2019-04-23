---
title: 'CA3006: Revisión de código en busca de vulnerabilidades de inyección de comandos de procesos'
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
ms.openlocfilehash: da161e611ca1d802c8da16370907029233bfd785
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60037990"
---
# <a name="ca3006-review-code-for-process-command-injection-vulnerabilities"></a>CA3006: Revisión de código en busca de vulnerabilidades de inyección de comandos de procesos

|||
|-|-|
|TypeName|ReviewCodeForProcessCommandInjectionVulnerabilities|
|Identificador de comprobación|CA3006|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Entrada de solicitud HTTP potencialmente no confiable alcanza un comando de proceso.

## <a name="rule-description"></a>Descripción de la regla

Al trabajar con entradas no seguras, esté atento ataques de inyección de comandos. Un ataque de inyección de comandos puede ejecutar comandos malintencionados en el sistema operativo subyacente, poner en peligro la seguridad e integridad de su servidor.

Esta regla intenta encontrar la entrada de las solicitudes HTTP para llegar a un comando de proceso.

> [!NOTE]
> Esta regla no puede realizar un seguimiento de datos a través de ensamblados. Por ejemplo, si un ensamblado lee la entrada de solicitud HTTP y, a continuación, pasa a otro ensamblado que se inicia un proceso, esta regla no genera una advertencia.

> [!NOTE]
> Hay un límite configurable para profundidad esta regla analizará el flujo de datos a través de llamadas de método. Consulte [Configuration Analyzer](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) para configurar el límite de `.editorconfig` archivos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

- Si es posible, evite iniciar procesos en función de entrada del usuario.
- Validar la entrada con un conjunto de prueba de errores conocido de caracteres y la longitud.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Si conoce la entrada se ha validado o caracteres de escape para que sean seguras, es seguro suprimir esta advertencia.

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

### <a name="violation"></a>Infracción

```csharp
using System;
using System.Diagnostics;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        Process p = Process.Start(input);
    }
}
```

```vb
Imports System
Imports System.Diagnostics

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs as EventArgs)
        Dim input As String = Me.Request.Form("in")
        Dim p As Process = Process.Start(input)
    End Sub
End Class
```
