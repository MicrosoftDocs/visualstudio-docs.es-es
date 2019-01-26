---
title: 'CA3147: Marcar los controladores de verbo con ValidateAntiForgeryToken'
ms.date: 08/08/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 630d16b17f687842574348d86c1591a5433d9bfa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037154"
---
# <a name="ca3147-mark-verb-handlers-with-validateantiforgerytoken"></a>CA3147: Marcar los controladores de verbo con ValidateAntiForgeryToken

|||
|-|-|
|TypeName|MarkVerbHandlersWithValidateAntiForgeryToken|
|Identificador de comprobación|CA3147|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Un método de acción de controlador de MVC de ASP.NET no está marcado con [ValidateAntiForgeryTokenAttribute](/previous-versions/aspnet/web-frameworks/dd492108(v=vs.118)), o un atributo que especifica el verbo HTTP, como [HttpGetAttribute](/previous-versions/aspnet/web-frameworks/ee470993(v%3dvs.118)) o [ AcceptVerbsAttribute](/previous-versions/aspnet/web-frameworks/dd470553%28v%3dvs.118%29).

## <a name="rule-description"></a>Descripción de la regla

Al diseñar un controlador ASP.NET MVC, esté atento ataques de falsificación de solicitud entre sitios. Un ataque de falsificación de solicitud entre sitios puede enviar solicitudes malintencionadas de un usuario autenticado al controlador de MVC de ASP.NET. Para obtener más información, consulte [prevención de XSRF/CSRF en ASP.NET MVC y web pages](/aspnet/mvc/overview/security/xsrfcsrf-prevention-in-aspnet-mvc-and-web-pages).

Esta regla comprueba si ese controlador de MVC de ASP.NET los métodos de acción ya sea:

- Tiene la [ValidateAntiforgeryTokenAttribute](/previous-versions/aspnet/web-frameworks/dd492108%28v%3dvs.118%29) y especifique los verbos HTTP permitidos, sin incluir el HTTP GET.

- Especificar HTTP GET como un verbo permitido.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

- Para acciones de controlador de MVC de ASP.NET que controlan las solicitudes HTTP GET y no tienen efectos secundarios potencialmente dañinos, agregue un [HttpGetAttribute](/previous-versions/aspnet/web-frameworks/ee470993%28v%3dvs.118%29) al método.

   Si tiene un ASP.NET MVC, las solicitudes de acción del controlador que controla HTTP GET y tiene potencialmente perjudiciales efectos como la modificación de datos confidenciales, la aplicación es vulnerable a ataques de falsificación de solicitud entre sitios.  Necesitará volver a diseñar la aplicación para que solamente las solicitudes HTTP POST, PUT o DELETE realizan operaciones confidenciales.

- Para acciones de controlador de MVC de ASP.NET que controlan la solicitud HTTP POST, PUT o las solicitudes de eliminación, agregue [ValidateAntiForgeryTokenAttribute](/previous-versions/aspnet/web-frameworks/dd492108(v=vs.118)) y los atributos que especifican los verbos HTTP permitidos ([AcceptVerbsAttribute](/previous-versions/aspnet/web-frameworks/dd470553%28v%3dvs.118%29) [HttpPostAttribute](/previous-versions/aspnet/web-frameworks/ee264023%28v%3dvs.118%29), [HttpPutAttribute](/previous-versions/aspnet/web-frameworks/ee470909%28v%3dvs.118%29), o [HttpDeleteAttribute](/previous-versions/aspnet/web-frameworks/ee470917%28v%3dvs.118%29)). Además, debe llamar a la [HtmlHelper.AntiForgeryToken()](/previous-versions/aspnet/web-frameworks/dd504812%28v%3dvs.118%29) método desde la vista de MVC o página web de Razor. Para obtener un ejemplo, vea [examinando los métodos de edición y editar vista](/aspnet/mvc/overview/getting-started/introduction/examining-the-edit-methods-and-edit-view).

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla si:

- La acción de controlador de MVC de ASP.NET no tiene efectos perjudiciales.

- La aplicación valida el token antifalsificación de forma diferente.

## <a name="validateantiforgerytoken-attribute-example"></a>Ejemplo de atributo ValidateAntiForgeryToken

### <a name="violation"></a>Infracción

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            // You don't want an attacker to specify to who and how much money to transfer.

            return null;
        }
    }
}
```

### <a name="solution"></a>Soluciones

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpPost]
        [ValidateAntiForgeryToken]
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            return null;
        }
    }
}
```

## <a name="httpget-attribute-example"></a>Ejemplo de atributo HttpGet

### <a name="violation"></a>Infracción

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult Help(int topicId)
        {
            // This Help method is an example of a read-only operation with no harmful side effects.
            return null;
        }
    }
}
```

### <a name="solution"></a>Soluciones

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpGet]
        public ActionResult Help(int topicId)
        {
            return null;
        }
    }
}
```
