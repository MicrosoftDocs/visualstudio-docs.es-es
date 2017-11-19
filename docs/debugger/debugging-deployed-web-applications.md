---
title: Depurar aplicaciones ASP.NET implementadas | Documentos de Microsoft
ms.custom: 
ms.date: 06/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
caps.latest.revision: "31"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 421c1f5f8736b9bd2cd95ac61570cc831c468c78
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-deployed-aspnet-applications"></a>Depurar aplicaciones ASP.NET implementadas
Para usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a fin de depurar una aplicación implementada, debe establecer una asociación al proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] y asegurarse de que el depurador tiene acceso a los símbolos de la aplicación. También debe buscar y abrir los archivos de código fuente de la aplicación. Para obtener más información, consulte [especificar símbolos (.pdb) y archivos de código fuente](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [Cómo: buscar el nombre del proceso de ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md), y [requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md).  

> [!WARNING]
> Si se adjunta a la [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proceso de trabajo para la depuración y posicionamiento de un punto de interrupción, todo el código en el proceso de trabajo se detiene administrado. Detener todo el código administrado del proceso de trabajo puede interrumpir el trabajo de todos los usuarios del servidor. Antes de depurar en un servidor de producción, considere los posibles efectos que tendrá en el trabajo de producción. 
  
El procedimiento para asociarse al proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] es el mismo que para asociarse a cualquier otro proceso remoto. Cuando se adjunta, si no tiene abierto el proyecto correcto, un cuadro de diálogo aparece cuando la aplicación se interrumpe. Este cuadro de diálogo pide la ubicación de los archivos de código fuente de la aplicación. El nombre de archivo que especifique en el cuadro de diálogo debe coincidir con el nombre especificado en los símbolos de depuración, ubicados en el servidor web. Para obtener más información, consulte [adjuntar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). Para configurar la depuración remota en IIS, vea [ASP.NET de depuración remota en un equipo de IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).
 
> [!NOTE]
>  Muchas aplicaciones web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] hacen referencia a archivos DLL que contienen lógica empresarial u otro código de utilidad. Dicha referencia copia el archivo DLL desde el equipo local a la carpeta \bin del directorio virtual de la aplicación Web cuando se implementa la aplicación. Durante el proceso de depuración, recuerde que la aplicación web hace referencia a esa copia del archivo DLL y no a la copia del equipo local. 
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones ASP.](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Cómo: habilitar la depuración de aplicaciones de ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Cómo: buscar el nombre del proceso de ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [Especificar los símbolos (.pdb) y archivos de código fuente](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)