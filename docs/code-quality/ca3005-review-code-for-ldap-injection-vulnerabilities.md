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
ms.openlocfilehash: 38c28153fa513c4f4db5b3a7833d279674f66734
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541303"
---
# <a name="ca3005-review-code-for-ldap-injection-vulnerabilities"></a>CA3005: Revisión de código en busca de vulnerabilidades de inyección de LDAP

|||
|-|-|
|TypeName|ReviewCodeForLdapInjectionVulnerabilities|
|Identificador de comprobación|CA3005|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Entrada de solicitud HTTP potencialmente no confiable alcanza una instrucción de LDAP.

## <a name="rule-description"></a>Descripción de la regla

Al trabajar con entradas no seguras, esté atento a ataques de inyección de protocolo ligero de acceso a directorios (LDAP). Un atacante puede ejecutar instrucciones LDAP malintencionadas frente a los directorios de información. Las aplicaciones que usan la entrada del usuario para construir instrucciones dinámicas de LDAP para acceder a los servicios de directorio son especialmente vulnerables.

Esta regla intenta encontrar la entrada de las solicitudes HTTP para alcanzar una instrucción de LDAP.

> [!NOTE]
> Esta regla no puede realizar un seguimiento de datos a través de ensamblados. Por ejemplo, si un ensamblado lee la entrada de solicitud HTTP y, a continuación, pasa a otro ensamblado que se ejecuta una instrucción de LDAP, esta regla no genera una advertencia.

> [!NOTE]
> Hay un límite configurable para profundidad esta regla analizará el flujo de datos a través de llamadas de método. Consulte [Configuration Analyzer](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) para configurar el límite de `.editorconfig` archivos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

La parte controlado por el usuario de las instrucciones de LDAP, considere uno de:
- Permitir solo una lista segura de los caracteres que no son especiales.
- No permitir caracteres especiales
- Caracteres especiales de escape.

Consulte [hoja de referencia rápida de OWASP LDAP inyección prevención](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/LDAP_Injection_Prevention_Cheat_Sheet.md) para obtener más instrucciones.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Si conoce la entrada se ha validado o caracteres de escape para que sean seguras, es correcto suprimir esta advertencia.

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
