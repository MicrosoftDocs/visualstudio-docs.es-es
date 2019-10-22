---
title: Procedimiento Iniciar Spy ++ | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 36555d9b00c9aff3f594ae2217afe8434bb41542
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442750"
---
# <a name="how-to-start-spy"></a>Procedimiento Iniciar Spy++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede iniciar Spy ++ desde Visual Studio o en un símbolo del sistema.  
  
 Al iniciar Spy ++, si se muestra un mensaje para solicitar permiso para realizar cambios en el equipo, haga clic en **Sí**.  
  
> [!NOTE]
> Puede ejecutar una única instancia de Spy ++. Si intenta ejecutar otra instancia, simplemente hace que la instancia en ejecución obtener el foco.  
  
### <a name="to-start-spy-from-visual-studio"></a>Para iniciar Spy ++ desde Visual Studio  
  
- En el **herramientas** menú, haga clic en **Spy ++**.  
  
     Dado que Spy ++ se ejecuta de forma independiente, después de iniciarla, puede cerrar Visual Studio.  
  
    > [!NOTE]
    > Al registrar los mensajes con Spy ++, provocaría el sistema operativo realice más lentamente.  
  
### <a name="to-start-spy-at-a-command-prompt"></a>Para iniciar Spy ++ en un símbolo del sistema  
  
1. En una ventana del símbolo del sistema, cambie los directorios a la carpeta que contiene spyxx.exe. Normalmente, es la ruta de acceso de esta carpeta... \\ *Carpeta de instalación de visual Studio*\Common7\Tools\\.  
  
2. Tipo **spyxx.exe** y, a continuación, presione ENTRAR.  
  
## <a name="see-also"></a>Vea también  
 [Usar Spy++](../debugger/using-spy-increment.md)   
 [Vistas de Spy++](../debugger/spy-increment-views.md)   
 [Referencia de Spy++](../debugger/spy-increment-reference.md)
