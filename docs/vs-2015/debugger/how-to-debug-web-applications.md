---
title: Procedimiento Depurar aplicaciones Web | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web services, debugging
- ASP.NET Web Forms, debugging
- ASP.NET, debugging Web applications
- debugging ASP.NET Web applications, during development
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd3cbbcd740c0f124b8ab4379204a9d425cd541c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039549"
---
# <a name="how-to-debug-web-applications"></a>Procedimiento Depurar aplicaciones Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] es la tecnología principal para desarrollar aplicaciones Web en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. El depurador de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proporciona herramientas muy eficaces para depurar aplicaciones web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] localmente o en un servidor remoto. Este tema describe cómo depurar un [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] proyecto durante el desarrollo. Para obtener información sobre cómo depurar un [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ya implementada en un servidor de producción de aplicaciones Web, consulte [depurar aplicaciones Web implementadas](../debugger/debugging-deployed-web-applications.md).  
  
 Para depurar una aplicación [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]:  
  
- Debe tener los permisos necesarios. Para obtener más información, consulte [requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
- [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] depuración debe estar habilitada en **las propiedades del proyecto**.  
  
- El archivo de configuración de la aplicación (Web.config) se debe establecer en modo de depuración. El modo de depuración hace que [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] genere símbolos para los archivos generados dinámicamente y permite al depurador asociarse a la aplicación [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] establece esto automáticamente al empezar a depurar si se creó el proyecto a partir de la plantilla de proyectos web.  
  
- Para obtener más información, vea [Cómo: Habilitar la depuración de aplicaciones ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md).  
  
### <a name="to-debug-a-web-application-during-development"></a>Para depurar una aplicación Web durante la fase de desarrollo  
  
1. En el **depurar** menú, haga clic en **iniciar** para empezar a depurar la aplicación Web.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] compila el proyecto de aplicación web, implementa la aplicación si es necesario, inicia el Servidor de desarrollo de ASP.NET si se está depurando localmente y lo asocia al proceso de trabajo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
2. Utilice el depurador para establecer y borrar puntos de interrupción, ver paso a paso el código y realizar otras operaciones de depuración, igual que haría para cualquier otra aplicación.  
  
     Para obtener más información, consulte [Fundamentos del depurador](../debugger/debugger-basics.md).  
  
3. En el **depurar** menú, haga clic en **Detener depuración** para finalizar la sesión de depuración, o bien, en el **archivo** menús en Internet Explorer, haga clic en **cerrar**.  
  
## <a name="see-also"></a>Vea también  
 [Depurar script y aplicaciones web](../debugger/debugging-web-applications-and-script.md)   
 [Depurar aplicaciones de ASP.NET y AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Cómo: Habilitación de la depuración de aplicaciones de ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
