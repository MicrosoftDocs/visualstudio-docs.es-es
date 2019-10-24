---
title: Depuración de aplicaciones ASP.NET implementadas | Microsoft Docs
ms.date: 06/30/2018
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: c2b1838375ee878640d77a9c93808efafc9f519c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738298"
---
# <a name="debugging-deployed-aspnet-applications"></a>Depuración de aplicaciones ASP.NET implementadas
Para usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a fin de depurar una aplicación implementada, debe establecer una asociación al proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] y asegurarse de que el depurador tiene acceso a los símbolos de la aplicación. También debe buscar y abrir los archivos de código fuente de la aplicación. Para obtener más información, vea [especificar los archivos de código fuente y símbolos (. pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [Cómo: buscar el nombre del proceso ASP.net](../debugger/how-to-find-the-name-of-the-aspnet-process.md)y [los requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md).

> [!WARNING]
> Si se asocia al proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] para la depuración y se alcanza un punto de interrupción, se detiene todo el código administrado del proceso de trabajo. Detener todo el código administrado del proceso de trabajo puede interrumpir el trabajo de todos los usuarios del servidor. Antes de depurar en un servidor de producción, considere los posibles efectos que tendrá en el trabajo de producción.

El procedimiento para asociarse al proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] es el mismo que para asociarse a cualquier otro proceso remoto. Cuando está asociado, si no tiene abierto el proyecto correcto, aparecerá un cuadro de diálogo cuando se interrumpa la aplicación. Este cuadro de diálogo pide la ubicación de los archivos de código fuente de la aplicación. El nombre de archivo que especifique en el cuadro de diálogo debe coincidir con el nombre especificado en los símbolos de depuración, ubicados en el servidor web. Para obtener más información, vea [asociar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). Para configurar la depuración remota en IIS, consulte [depuración remota ASP.net en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

> [!NOTE]
> Muchas aplicaciones web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] hacen referencia a archivos DLL que contienen lógica empresarial u otro código de utilidad. Dicha referencia copia el archivo DLL del equipo local a la carpeta \Bin del directorio virtual de la aplicación web al implementar la aplicación. Durante el proceso de depuración, recuerde que la aplicación web hace referencia a esa copia del archivo DLL y no a la copia del equipo local.

## <a name="see-also"></a>Vea también
- [Depurar aplicaciones ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Cómo: Habilitar la depuración de aplicaciones de ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Cómo: Buscar el nombre de un proceso de ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)
- [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)