---
title: 'CA3005: Revisión de código en busca de vulnerabilidades de inyección de LDAP'
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
ms.openlocfilehash: c0c99d5d0adb145a061693f8a83b1f674e05eed4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237343"
---
# <a name="ca3005-review-code-for-ldap-injection-vulnerabilities"></a>CA3005: Revisión de código en busca de vulnerabilidades de inyección de LDAP

|||
|-|-|
|TypeName|ReviewCodeForLdapInjectionVulnerabilities|
|Identificador de comprobación|CA3005|
|Categoría|Microsoft.Security|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Una entrada de solicitud HTTP que podría no ser de confianza llega a una instrucción LDAP.

## <a name="rule-description"></a>Descripción de la regla

Cuando trabaje con una entrada que no sea de confianza, tenga en cuentan los ataques por inyección de Protocolo ligero de acceso a directorios (LDAP). Un atacante podría ejecutar instrucciones LDAP malintencionadas en directorios de información. Las aplicaciones que usan datos proporcionados por el usuario para construir instrucciones LDAP dinámicas para tener acceso a los servicios de directorio son especialmente vulnerables.

Esta regla intenta buscar la entrada de las solicitudes HTTP que llegan a una instrucción LDAP.

> [!NOTE]
> Esta regla no puede realizar el seguimiento de los datos entre ensamblados. Por ejemplo, si un ensamblado lee la entrada de la solicitud HTTP y, a continuación, la pasa a otro ensamblado que ejecuta una instrucción LDAP, esta regla no generará ninguna advertencia.

> [!NOTE]
> Existe un límite configurable en cuanto a la profundidad con que esta regla analizará el flujo de datos a través de las llamadas a métodos. Vea [configuración del analizador](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) para saber cómo configurar el límite en un archivo EditorConfig.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para la parte controlada por el usuario de las instrucciones LDAP, considere uno de los siguientes:
- Permitir solo una lista segura de caracteres no especiales.
- No permitir carácter especial
- Caracteres especiales de escape.

Consulte [la hoja](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/LDAP_Injection_Prevention_Cheat_Sheet.md) de referencia de prevención de inyección LDAP de OWASP para obtener más información.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Si sabe que la entrada se ha validado o no es segura, puede suprimir esta advertencia.

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

### <a name="violation"></a>Infracción

```csharp
using System;
using System.DirectoryServices;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string userName = Request.Params["user"];
        string filter = "(uid=" + userName + ")";  // searching for the user entry

        // In this example, if we send the * character in the user parameter which will
        // result in the filter variable in the code to be initialized with (uid=*).
        // The resulting LDAP statement will make the server return any object that
        // contains a uid attribute.
        DirectorySearcher searcher = new DirectorySearcher(filter);
        SearchResultCollection results = searcher.FindAll();

        // Iterate through each SearchResult in the SearchResultCollection.
        foreach (SearchResult searchResult in results)
        {
            // ...
        }
    }
}
```

```vb
Imports System
Imports System.DirectoryServices

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(send As Object, e As EventArgs)
        Dim userName As String = Me.Request.Params(""user"")
        Dim filter As String = ""(uid="" + userName + "")""    ' searching for the user entry

        ' In this example, if we send the * character in the user parameter which will
        ' result in the filter variable in the code to be initialized with (uid=*).
        ' The resulting LDAP statement will make the server return any object that
        ' contains a uid attribute.
        Dim searcher As DirectorySearcher = new DirectorySearcher(filter)
        Dim results As SearchResultCollection = searcher.FindAll()

        ' Iterate through each SearchResult in the SearchResultCollection.
        For Each searchResult As SearchResult in results
            ' ...
        Next searchResult
    End Sub
End Class
```
