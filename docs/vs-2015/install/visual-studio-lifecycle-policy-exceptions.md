---
title: Excepciones de la directiva de ciclo de vida de Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
ms.assetid: c238489d-6181-42c6-aa60-f75d0889dc68
caps.latest.revision: 3
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: b17693523c75dc434fdda258c07a9b17ecfda1b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180237"
---
# <a name="visual-studio-lifecycle-policy-exceptions"></a>Excepciones de la directiva de ciclo de vida de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio incluye una colección de compiladores, lenguajes, tiempos de ejecución, entornos y otros recursos que permiten el desarrollo en muchas plataformas de Microsoft. Por comodidad para nuestros clientes de Visual Studio, Visual Studio puede instalar determinados SDK de Microsoft y otros componentes de Microsoft que dirigen y proporcionan compatibilidad con dichas plataformas de Microsoft. Las licencias y el soporte de estos componentes se rigen por términos y directivas propios.  
  
## <a name="external-components-that-follow-a-lifecycle-policy-other-than-the-visual-studio-policy"></a>Componentes externos que siguen una directiva de ciclo de vida distinta de la directiva de Visual Studio  
 La tabla siguiente muestra los componentes de la plataforma de Microsoft que puedan estar incluidos con Visual Studio (según la edición específica del software de Visual Studio) y que están sujetos a sus propias directivas de soporte técnico y plazos de tiempo.  
  
|FAMILIA DE PRODUCTOS|NOMBRE EXTERNO|  
|--------------------|-------------------|  
|[.NET 3.5](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=net%20framework%203.5&Filter=FilterNO)|SDK DE .NET 3.5<br /><br /> Windows Identity Foundation|  
|[.NET 4.5](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=net%20framework%204.5&Filter=FilterNO)|SDK DE .NET 4.5|  
|[.NET 4.5.1](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=.NET%20Framework%204.5.1&Filter=FilterNO)|Paquete de .NET 4.5.1 (clásico)<br /><br /> Paquete de compatibilidad con múltiples versiones de .NET 4.5.1 (almacén)<br /><br /> MSU OOB de .NET 4.5.1<br /><br /> Paquete redistribuible de .NET 4.5.1<br /><br /> Paquetes de idiomas redistribuibles de .NET 4.5.1<br /><br /> SDK DE .NET 4.5.1|  
|[Pila web de ASP.NET](http://go.microsoft.com/fwlink/?LinkId=328918)|ASP.NET MVC 4<br /><br /> ASP.NET MVC 5<br /><br /> ASP.NET Web API<br /><br /> ASP.NET Web API 2<br /><br /> ASP.NET Web Pages 2<br /><br /> ASP.NET Web Pages 3|  
|[Entity Framework 6](http://go.microsoft.com/fwlink/?LinkId=328950)|Entity Framework 6|  
|[Exchange 2013](http://go.microsoft.com/fwlink/?LinkId=328950)|Servicios Web Exchange|  
|[Microsoft OWIN](http://go.microsoft.com/fwlink/?LinkId=328951)|Microsoft OWIN|  
|[Microsoft Web Developer Tools 2013](http://go.microsoft.com/fwlink/?LinkId=328952)|Microsoft Web Developer Tools 2013|  
|Las actualizaciones de estos componentes se distribuyen a través de NuGet y no siguen las directivas de ciclo de vida estándar de Microsoft.  Para más información, vea [http://docs.nuget.org/](http://docs.nuget.org/).|Controlador de token web JSON para Microsoft .NET Framework 4.5<br /><br /> NuGet 2.7<br /><br /> SignalR<br /><br /> Web Optimization Framework<br /><br /> WebGrease|  
|[ODataLib](http://go.microsoft.com/fwlink/?LinkId=328954)|ODataLib|  
|[Office 2013](http://support.microsoft.com/lifecycle/?p1=16674)|SDK de Open XML|  
|[Directiva de servicios en línea](http://support.microsoft.com/gp/OSSLpolicy)|SDK de Microsoft Ads|  
|[SharePoint 2013](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=sharepoint%20server%202013&Filter=FilterNO)|Componente de cliente de SharePoint<br /><br /> SharePoint Foundation 2013<br /><br /> Extensiones de Windows Identity Foundation|  
|[Silverlight 5](http://support.microsoft.com/lifecycle/?p1=16278)<br /><br /> <br />> Vea también: [http://support.microsoft.com/gp/lifean45](http://support.microsoft.com/gp/lifean45)|Tiempo de ejecución de Silverlight 5<br /><br /> SDK de Silverlight 5|  
|[SQL Server 2008 R2](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=SQL%20Server%202008%20R2&Filter=FilterNO)|Tipos CLR del sistema de SQL (SQL Server 2008 R2)|  
|[SQL Server 2012](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=SQL%20Server%202012&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> Utilidades de línea de comandos SQL<br /><br /> Servicio de lenguaje SQL: IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client (Sqlncli)<br /><br /> SQL Server Express 2012 SP1<br /><br /> Tipos CLR del sistema de SQL (SQL Server 2012)<br /><br /> SQLDOM|  
|[SQL Server 2014](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202014&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> Utilidades de línea de comandos SQL<br /><br /> Servicio de lenguaje SQL: IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client (Sqlncli)<br /><br /> SQL Server Express 2014<br /><br /> Tipos CLR del sistema de SQL (SQL Server 2014)<br /><br /> SQLDOM|  
|[SQL Server Compact Edition 4.0](http://support.microsoft.com/lifecycle/?p1=16106)|SQL Server Compact Edition 4.0|  
|[Servicios WCF RIA v1.0 SP2](http://go.microsoft.com/fwlink/?LinkId=328955)|Servicios WCF RIA v1.0 SP2|  
|[Windows Server 2008](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=Windows%20Server%202008&Filter=FilterNO)|Servicios web de Windows (WWS) para Windows Server 2008|  
|[Windows 7](http://support.microsoft.com/lifecycle/?c2=14019)|SDK de Windows 7|  
|[Windows 8](http://support.microsoft.com/lifecycle/?c2=16796)|SDK de Windows 8|  
|[Windows 8.1](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=windows%208.1&Filter=FilterNO)|SDK de Windows 8.1<br /><br /> Biblioteca de Windows para JavaScript (WinJS)|  
|[Microsoft Azure](http://support.microsoft.com/gp/azure-cloud-lifecycle-faq)<br /><br /> <br />> Vea también: [Directiva de ciclo de vida en línea](http://support.microsoft.com/gp/OSSLpolicy)|SDK de servicios móviles de Microsoft Azure<br /><br /> Herramientas de servicios móviles de Microsoft Azure|