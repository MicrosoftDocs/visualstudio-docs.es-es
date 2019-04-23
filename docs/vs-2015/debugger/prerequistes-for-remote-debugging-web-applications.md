---
title: Requisitos previos para la depuración remota de aplicaciones Web | Documentos de Microsoft
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
- debugging ASP.NET Web applications, remote servers
- remote debugging, prerequisites
- remote servers, debugging Web applications
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 46bf49567558cab556180c470bfd4b80d93f5dbb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105518"
---
# <a name="prerequistes-for-remote-debugging-web-applications"></a>Requisitos previos para la depuración remota de aplicaciones web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con el depurador de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], puede depurar una aplicación web de modo transparente en el equipo local o en un servidor remoto. Esto significa que el depurador funciona del mismo modo y permite usar las mismas características en cualquiera de los dos equipos. No obstante, para que la depuración remota funcione correctamente, se deben cumplir algunos requisitos previos.  
  
- Los componentes de depuración remota de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se deben instalar en el servidor que desee depurar. Para obtener más información, consulte [configurar la depuración remota](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
- De forma predeterminada, el proceso de trabajo de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] se ejecuta como un proceso de usuario de ASPNET. Por lo tanto, debe tener privilegios de administrador en el equipo en el que se ejecute [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] para depurarlo. El nombre del proceso de trabajo de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] varía en función del escenario de depuración y de la versión de IIS. Para obtener más información, vea [Cómo: Búsqueda del nombre de un proceso de ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones de ASP.NET y AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md)
