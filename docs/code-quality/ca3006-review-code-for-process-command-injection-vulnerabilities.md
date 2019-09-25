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
ms.openlocfilehash: 986607d7f42f49c99396bbb021c48bad549930c9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237291"
---
# <a name="ca3006-review-code-for-process-command-injection-vulnerabilities"></a>CA3006: Revisión de código en busca de vulnerabilidades de inyección de comandos de procesos

|||
|-|-|
|TypeName|ReviewCodeForProcessCommandInjectionVulnerabilities|
|Identificador de comprobación|CA3006|
|Categoría|Microsoft.Security|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Una entrada de solicitud HTTP que podría no ser de confianza llega a un comando de proceso.

## <a name="rule-description"></a>Descripción de la regla

Al trabajar con una entrada que no es de confianza, tenga en cuentan los ataques por inyección de comandos. Un ataque por inyección de comandos puede ejecutar comandos malintencionados en el sistema operativo subyacente, poniendo en peligro la seguridad y la integridad del servidor.

Esta regla intenta buscar la entrada de las solicitudes HTTP que llegan a un comando de proceso.

> [!NOTE]
> Esta regla no puede realizar el seguimiento de los datos entre ensamblados. Por ejemplo, si un ensamblado lee la entrada de la solicitud HTTP y, a continuación, la pasa a otro ensamblado que inicia un proceso, esta regla no generará ninguna advertencia.

> [!NOTE]
> Existe un límite configurable en cuanto a la profundidad con que esta regla analizará el flujo de datos a través de las llamadas a métodos. Vea [configuración del analizador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) para saber cómo configurar el límite en un archivo EditorConfig.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

- Si es posible, evite iniciar procesos en función de los datos proporcionados por el usuario.
- Valide la entrada con un conjunto seguro de caracteres y longitud conocidos.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Si sabe que la entrada se ha validado o se ha convertido en un carácter de escape para que sea segura, es seguro suprimir esta advertencia.

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
