---
title: 'CA3004: Revisión de código en busca de vulnerabilidades de divulgación de información'
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
ms.openlocfilehash: 8e8c8c58a01b9527df472907c8b55a9d175dd91d
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841610"
---
# <a name="ca3004-review-code-for-information-disclosure-vulnerabilities"></a>CA3004: Revisión de código en busca de vulnerabilidades de divulgación de información

|||
|-|-|
|TypeName|ReviewCodeForInformationDisclosureVulnerabilities|
|Identificador de comprobación|CA3004|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Mensaje de una excepción, seguimiento de la pila o representación de cadena llega a la salida de web.

## <a name="rule-description"></a>Descripción de la regla

Divulgación de información de excepción proporciona visión general de los aspectos internos de la aplicación, lo que puede ayudar a los atacantes encontrar otras vulnerabilidades aprovechar de los atacantes.

Esta regla intenta buscar un mensaje de excepción, seguimiento de la pila o representación de cadena que se va a utilizar en una respuesta HTTP.

> [!NOTE]
> Esta regla no puede realizar un seguimiento de datos a través de ensamblados. Por ejemplo, si un ensamblado detecta una excepción y, a continuación, pasa a otro ensamblado que genera la excepción, esta regla no genera una advertencia.

> [!NOTE]
> Hay un límite configurable para profundidad esta regla analizará el flujo de datos a través de llamadas de método. Consulte [Configuration Analyzer](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) acerca de cómo configurar el límite en un archivo EditorConfig.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

No información de excepción a las respuestas HTTP de salida. En su lugar, proporcione un mensaje de error genérico. Consulte [página de control de errores de OWASP](https://www.owasp.org/index.php/Error_Handling) para obtener más instrucciones.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Si sabe que es la salida web dentro del límite de confianza de la aplicación y nunca se expone fuera, no pasa nada suprimir esta advertencia. Esto es poco frecuente. Tenga en cuenta que pueden cambiar el límite de confianza de la aplicación y los flujos de datos con el tiempo.

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

### <a name="violation"></a>Infracción

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs eventArgs)
    {
        try
        {
            object o = null;
            o.ToString();
        }
        catch (Exception e)
        {
            this.Response.Write(e.ToString());
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Try
            Dim o As Object = Nothing
            o.ToString()
        Catch e As Exception
            Me.Response.Write(e.ToString())
        End Try
    End Sub
End Class
```

### <a name="solution"></a>Soluciones

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs eventArgs)
    {
        try
        {
            object o = null;
            o.ToString();
        }
        catch (Exception e)
        {
            this.Response.Write("An error occurred. Please try again later.");
        }
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, eventArgs As EventArgs)
        Try
            Dim o As Object = Nothing
            o.ToString()
        Catch e As Exception
            Me.Response.Write("An error occurred. Please try again later.")
        End Try
    End Sub
End Class
```