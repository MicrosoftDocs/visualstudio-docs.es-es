---
title: 'CA3003: Revisión de código en busca de vulnerabilidades de inyección de rutas de acceso a archivos'
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
ms.openlocfilehash: c20d3efb9ea84a7e8bb22288303313ef44b2b795
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806568"
---
# <a name="ca3003-review-code-for-file-path-injection-vulnerabilities"></a>CA3003: Revisión de código en busca de vulnerabilidades de inyección de rutas de acceso a archivos

|||
|-|-|
|TypeName|ReviewCodeForFilePathInjectionVulnerabilities|
|Identificador de comprobación|CA3003|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Entrada de solicitud HTTP potencialmente no confiable alcanza la ruta de acceso de una operación de archivo.

## <a name="rule-description"></a>Descripción de la regla

Al trabajar con entradas no seguras de las solicitudes web, esté atento con entrada controlado por el usuario al especificar las rutas de acceso a archivos. Un atacante puede ser capaz de leer un archivo no deseado, lo que produce la divulgación de información confidencial. O bien, un atacante puede ser capaz de escribir en un archivo no deseado, lo que resulta en una modificación no autorizada de información confidencial o poner en peligro la seguridad del servidor. Es una técnica común del atacante [recorrido de la ruta de acceso](https://www.owasp.org/index.php/Path_Traversal) acceso a los archivos fuera del directorio deseado.

Esta regla intenta encontrar la entrada de las solicitudes HTTP para llegar a una ruta de acceso en una operación de archivo.

> [!NOTE]
> Esta regla no puede realizar un seguimiento de datos a través de ensamblados. Por ejemplo, si un ensamblado lee la entrada de solicitud HTTP y, a continuación, pasa a otro ensamblado que se escribe en un archivo, esta regla no genera una advertencia.

> [!NOTE]
> Hay un límite configurable para profundidad esta regla analizará el flujo de datos a través de llamadas de método. Consulte [Configuration Analyzer](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) para configurar el límite de `.editorconfig` archivos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

- Si es posible, limite las rutas de acceso basadas en la entrada del usuario a una lista segura explícitamente conocida.  Por ejemplo, si la aplicación solo necesita tener acceso a "red.txt", "green.txt" o "blue.txt", permitir solo esos valores.
- Compruebe los nombres de archivo que no se confía y validar que el nombre es correcto.
- Utilice los nombres de ruta de acceso completa al especificar las rutas de acceso.
- Evite construcciones potencialmente peligrosos como variables de entorno path.
- Solo acepta nombres de archivo largos y validar el nombre largo si el usuario envía los nombres cortos.
- Restringir la entrada de usuario final a los caracteres válidos.
- Rechazar nombres donde se supera la longitud MAX_PATH.
- Administrar nombres de archivo literalmente, sin interpretación.
- Determinar si el nombre de archivo representa un archivo o un dispositivo.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Si ha validado la entrada como se describe en la sección anterior, es correcto suprimir esta advertencia.

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

### <a name="violation"></a>Infracción

```csharp
using System;
using System.IO;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string userInput = Request.Params["UserInput"];
        // Assume the following directory structure:
        //   wwwroot\currentWebDirectory\user1.txt
        //   wwwroot\currentWebDirectory\user2.txt
        //   wwwroot\secret\allsecrets.txt
        // There is nothing wrong if the user inputs:
        //   user1.txt
        // However, if the user input is: 
        //   ..\secret\allsecrets.txt
        // Then an attacker can now see all the secrets.

        // Avoid this:
        using (File.Open(userInput, FileMode.Open))
        {
            // Read a file with the name supplied by user
            // Input through request's query string and display 
            // The content to the webpage. 
        }
    }
}
```

```vb
Imports System
Imports System.IO

Partial Public Class WebForm 
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim userInput As String = Me.Request.Params("UserInput")
        ' Assume the following directory structure:
        '   wwwroot\currentWebDirectory\user1.txt
        '   wwwroot\currentWebDirectory\user2.txt
        '   wwwroot\secret\allsecrets.txt
        ' There is nothing wrong if the user inputs:
        '   user1.txt
        ' However, if the user input is: 
        '   ..\secret\allsecrets.txt
        ' Then an attacker can now see all the secrets.

        ' Avoid this:
        Using File.Open(userInput, FileMode.Open)
            ' Read a file with the name supplied by user
            ' Input through request's query string and display 
            ' The content to the webpage. 
        End Using
    End Sub
End Class
```
