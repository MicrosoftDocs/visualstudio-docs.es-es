---
title: Depuración de aplicaciones ASP.NET implementadas | Microsoft Docs
description: Use Visual Studio para depurar una aplicación de ASP.NET implementada; para ello, establezca una asociación al proceso de trabajo y asegúrese de que el depurador tiene acceso a los símbolos de la aplicación.
ms.custom: SEO-VS-2020
ms.date: 06/30/2018
ms.topic: how-to
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
ms.openlocfilehash: 1e8c99f1988ef1aa2e14c7b0a4d6ed46e10f6f1e
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727053"
---
# <a name="debugging-deployed-aspnet-applications"></a>Depuración de aplicaciones ASP.NET implementadas
Para usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a fin de depurar una aplicación implementada, debe establecer una asociación al proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] y asegurarse de que el depurador tiene acceso a los símbolos de la aplicación. También debe buscar y abrir los archivos de código fuente de la aplicación. Para obtener más información, vea [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [Cómo: Buscar el nombre de un proceso de ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md) y [Requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md).

> [!WARNING]
> Si establece una asociación al proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] para depurar y alcanzar un punto de interrupción, se detiene todo el código administrado del proceso de trabajo. Detener todo el código administrado del proceso de trabajo puede interrumpir el trabajo de todos los usuarios del servidor. Antes de depurar en un servidor de producción, considere los posibles efectos que tendrá en el trabajo de producción.

El procedimiento para asociarse al proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] es el mismo que para asociarse a cualquier otro proceso remoto. Cuando está asociado, si no tiene abierto el proyecto correcto, aparecerá un cuadro de diálogo cuando se interrumpa la aplicación. Este cuadro de diálogo pide la ubicación de los archivos de código fuente de la aplicación. El nombre de archivo que especifique en el cuadro de diálogo debe coincidir con el nombre especificado en los símbolos de depuración, ubicados en el servidor web. Para más información, vea [Asociar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). Para configurar la depuración remota en IIS, vea [Depuración remota de ASP.NET Core en un equipo de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

> [!NOTE]
> Muchas aplicaciones web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] hacen referencia a archivos DLL que contienen lógica empresarial u otro código de utilidad. Dicha referencia copia el archivo DLL del equipo local en la carpeta \bin del directorio virtual de la aplicación web cuando se implementa la aplicación. Durante el proceso de depuración, recuerde que la aplicación web hace referencia a esa copia del archivo DLL y no a la copia del equipo local.

## <a name="see-also"></a>Vea también
- [Depurar aplicaciones ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Cómo: Habilitación de la depuración de aplicaciones de ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Cómo: Búsqueda del nombre de un proceso de ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)
- [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)