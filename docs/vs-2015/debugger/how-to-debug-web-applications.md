---
title: 'Cómo: depurar aplicaciones Web | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205401"
---
# <a name="how-to-debug-web-applications"></a>Cómo: Depurar aplicaciones web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] es la tecnología principal para desarrollar aplicaciones web en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . El depurador de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proporciona herramientas muy eficaces para depurar aplicaciones web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] localmente o en un servidor remoto. En este tema se describe cómo depurar un [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] proyecto durante el desarrollo. Para obtener información sobre cómo depurar una [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplicación web ya implementada en un servidor de producción, vea [depurar aplicaciones web implementadas](../debugger/debugging-deployed-web-applications.md).  
  
 Para depurar una aplicación [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]:  
  
- Debe tener los permisos necesarios. Para obtener más información, vea [Requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
- [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] la depuración debe estar habilitada en **las propiedades del proyecto**.  
  
- El archivo de configuración de la aplicación (Web.config) se debe establecer en modo de depuración. El modo de depuración hace que [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] genere símbolos para los archivos generados dinámicamente y permite al depurador asociarse a la aplicación [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] establece esto automáticamente al empezar a depurar si se creó el proyecto a partir de la plantilla de proyectos web.  
  
- Para obtener más información, vea [Cómo: habilitar la depuración para aplicaciones de ASP.net](../debugger/how-to-enable-debugging-for-aspnet-applications.md).  
  
### <a name="to-debug-a-web-application-during-development"></a>Para depurar una aplicación Web durante la fase de desarrollo  
  
1. En el menú **depurar** , haga clic en **iniciar** para empezar a depurar la aplicación Web.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] compila el proyecto de aplicación Web, implementa la aplicación si es necesario, inicia el Servidor de desarrollo de ASP.NET si está depurando localmente y se asocia al [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] proceso de trabajo.  
  
2. Utilice el depurador para establecer y borrar puntos de interrupción, ver paso a paso el código y realizar otras operaciones de depuración, igual que haría para cualquier otra aplicación.  
  
     Para obtener más información, vea [conceptos básicos del depurador](../debugger/debugger-basics.md).  
  
3. En el menú **depurar** , haga clic en **detener depuración** para finalizar la sesión de depuración o, en el menú **archivo** de Internet Explorer, haga clic en **cerrar**.  
  
## <a name="see-also"></a>Consulte también  
 [Depurar scripts y aplicaciones Web](../debugger/debugging-web-applications-and-script.md)   
 [Depuración de aplicaciones ASP.NET y AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Cómo: Habilitación de la depuración de aplicaciones de ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
