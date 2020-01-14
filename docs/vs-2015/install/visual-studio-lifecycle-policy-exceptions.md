---
title: Excepciones de la Directiva de ciclo de vida de Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
ms.assetid: c238489d-6181-42c6-aa60-f75d0889dc68
caps.latest.revision: 3
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: cc3a18fe1ce76b6214766ba45fc5441e80c56cef
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918489"
---
# <a name="visual-studio-lifecycle-policy-exceptions"></a>Excepciones de la directiva de ciclo de vida de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio incluye una colección de compiladores, lenguajes, tiempos de ejecución, entornos y otros recursos que permiten el desarrollo en muchas plataformas de Microsoft. Por comodidad para nuestros clientes de Visual Studio, Visual Studio puede instalar determinados SDK de Microsoft y otros componentes de Microsoft que dirigen y proporcionan compatibilidad con dichas plataformas de Microsoft. Las licencias y el soporte de estos componentes se rigen por términos y directivas propios.  
  
## <a name="external-components-that-follow-a-lifecycle-policy-other-than-the-visual-studio-policy"></a>Componentes externos que siguen una directiva de ciclo de vida distinta de la directiva de Visual Studio  
 La tabla siguiente muestra los componentes de la plataforma de Microsoft que puedan estar incluidos con Visual Studio (según la edición específica del software de Visual Studio) y que están sujetos a sus propias directivas de soporte técnico y plazos de tiempo.  
  
|FAMILIA DE PRODUCTOS|EXTERNAL NAME|  
|--------------------|-------------------|  
|[.NET 3.5](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=net%20framework%203.5&Filter=FilterNO)|SDK DE .NET 3.5<br /><br /> Windows Identity Foundation|  
|[.NET 4.5](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=net%20framework%204.5&Filter=FilterNO)|SDK DE .NET 4.5|  
|[.NET 4.5.1](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=.NET%20Framework%204.5.1&Filter=FilterNO)|Paquete de .NET 4.5.1 (clásico)<br /><br /> Paquete de compatibilidad con múltiples versiones de .NET 4.5.1 (almacén)<br /><br /> MSU OOB de .NET 4.5.1<br /><br /> Paquete redistribuible de .NET 4.5.1<br /><br /> Paquetes de idiomas redistribuibles de .NET 4.5.1<br /><br /> SDK DE .NET 4.5.1|  
|[Pila web de ASP.NET](https://support.microsoft.com/kb/2902020)|ASP.NET MVC 4<br /><br /> ASP.NET MVC 5<br /><br /> ASP.NET Web API<br /><br /> ASP.NET Web API 2<br /><br /> ASP.NET Web Pages 2<br /><br /> ASP.NET Web Pages 3|  
|[Entity Framework 6](https://support.microsoft.com/kb/2902020)|Entity Framework 6|  
|[Exchange 2013](https://support.microsoft.com/kb/2902020)|Servicios Web Exchange|  
|[Microsoft OWIN](https://support.microsoft.com/kb/2902020)|Microsoft OWIN|  
|[Microsoft Web Developer Tools 2013](https://support.microsoft.com/kb/2902020)|Microsoft Web Developer Tools 2013|  
|Las actualizaciones de estos componentes se distribuyen a través de NuGet y no siguen las directivas de ciclo de vida estándar de Microsoft.  Para más información, vea [http://docs.nuget.org/](/nuget/).|Controlador de token web JSON para Microsoft .NET Framework 4.5<br /><br /> NuGet 2.7<br /><br /> SignalR<br /><br /> Web Optimization Framework<br /><br /> WebGrease|  
|[ODataLib](https://support.microsoft.com/kb/2902020)|ODataLib|  
|[Office 2013](https://support.microsoft.com/lifecycle/search/?p1=16674)|SDK de Open XML|  
|[Directiva de servicios en línea](https://support.microsoft.com/hub/4095338/microsoft-lifecycle-policy)|SDK de Microsoft Ads|  
|[SharePoint 2013](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=sharepoint%20server%202013&Filter=FilterNO)|Componente de cliente de SharePoint<br /><br /> SharePoint Foundation 2013<br /><br /> Extensiones de Windows Identity Foundation|  
|[Silverlight 5](https://support.microsoft.com/lifecycle/search/?p1=16278)<br /><br /> <br />> Vea también: [http://support.microsoft.com/gp/lifean45](https://support.microsoft.com/gp/lifean45)|Tiempo de ejecución de Silverlight 5<br /><br /> SDK de Silverlight 5|  
|[SQL Server 2008 R2](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202008%20R2&Filter=FilterNO)|Tipos CLR del sistema de SQL (SQL Server 2008 R2)|  
|[SQL Server 2012](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202012&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> Utilidades de línea de comandos SQL<br /><br /> Servicio de lenguaje SQL: IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client (Sqlncli)<br /><br /> SQL Server Express 2012 SP1<br /><br /> Tipos CLR del sistema de SQL (SQL Server 2012)<br /><br /> SQLDOM|  
|[SQL Server 2014](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202014&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> Utilidades de línea de comandos SQL<br /><br /> Servicio de lenguaje SQL: IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client (Sqlncli)<br /><br /> SQL Server Express 2014<br /><br /> Tipos CLR del sistema de SQL (SQL Server 2014)<br /><br /> SQLDOM|  
|[SQL Server Compact Edition 4.0](https://support.microsoft.com/lifecycle/search/?p1=16106)|SQL Server Compact Edition 4.0|  
|[Servicios WCF RIA v1.0 SP2](https://support.microsoft.com/kb/2902020)|Servicios WCF RIA v1.0 SP2|  
|[Windows Server 2008](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=Windows%20Server%202008&Filter=FilterNO)|Servicios web de Windows (WWS) para Windows Server 2008|  
|[Windows 7](https://support.microsoft.com/lifecycle/search/?c2=14019)|SDK de Windows 7|  
|[Windows 8](https://support.microsoft.com/lifecycle/search/?c2=16796)|SDK de Windows 8|  
|[Windows 8.1](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=windows%208.1&Filter=FilterNO)|SDK de Windows 8.1<br /><br /> Biblioteca de Windows para JavaScript (WinJS)|  
|[Microsoft Azure](https://support.microsoft.com/help/18486/lifecycle-faq-azure)<br /><br /> <br />> Vea también: [Directiva de ciclo de vida en línea](https://support.microsoft.com/hub/4095338/microsoft-lifecycle-policy)|SDK de servicios móviles de Microsoft Azure<br /><br /> Herramientas de servicios móviles de Microsoft Azure|
