---
title: Requisitos previos para la depuración remota de aplicaciones Web | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 197a6e9b433173f1de13e3506db79e7edf53bade
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576351"
---
# <a name="prerequistes-for-remote-debugging-web-applications"></a>Requisitos previos para la depuración remota de aplicaciones web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [requisitos previos para las aplicaciones Web de depuración remota](https://docs.microsoft.com/visualstudio/debugger/prerequistes-for-remote-debugging-web-applications).  
  
Con el depurador de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], puede depurar una aplicación web de modo transparente en el equipo local o en un servidor remoto. Esto significa que el depurador funciona del mismo modo y permite usar las mismas características en cualquiera de los dos equipos. No obstante, para que la depuración remota funcione correctamente, se deben cumplir algunos requisitos previos.  
  
-   Los componentes de depuración remota de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se deben instalar en el servidor que desee depurar. Para obtener más información, consulte [configurar la depuración remota](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
-   De forma predeterminada, el proceso de trabajo de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] se ejecuta como un proceso de usuario de ASPNET. Por lo tanto, debe tener privilegios de administrador en el equipo en el que se ejecute [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] para depurarlo. El nombre del proceso de trabajo de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] varía en función del escenario de depuración y de la versión de IIS. Para obtener más información, consulta [How to: Find the Name of the ASP.NET Process](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## <a name="see-also"></a>Vea también  
 [Depuración de aplicaciones de ASP.NET y AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md)



