---
title: Procedimiento Depurar un Control ActiveX | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.controls.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f8dea98b05f5350f581128f18f38ec5f095505a5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105676"
---
# <a name="how-to-debug-an-activex-control"></a>Procedimiento Depuración de un control ActiveX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Para depurar el control ActiveX, debe especificar un contenedor (ejecutable) en el que ejecutar el control.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>Para especificar un contenedor para la sesión de depuración  
  
1. En el Explorador de soluciones, seleccione el proyecto.  
  
2. Desde el **vista** menú, elija **páginas de propiedades**.  
  
3. En el cuadro de diálogo **Páginas de propiedades del proyecto**, abra la carpeta **Propiedades de configuración** y seleccione **Depuración**.  
  
4. Debajo de la categoría **Depuración**, busque la propiedad **Comando**.  
  
5. Especifique el nombre de ruta de acceso para el contenedor. Por ejemplo, C:\Archivos de programa\Internet Explorer\IEXPLORE.EXE.  
  
6. Si especifica Internet Explorer como el contenedor y está utilizando Active Desktop, escriba `/new` en el cuadro **Argumentos del comando**.  
  
7. Haga clic en **Aceptar**.  
  
     Si no especifica ningún contenedor en el cuadro de diálogo **Páginas de propiedades del proyecto**, puede especificarlo al iniciar la depuración. Cuando se selecciona un comando de ejecución para iniciar la depuración, aparece el [cuadro de diálogo Archivo ejecutable para sesión de depuración](../debugger/executable-for-debugging-session-dialog-box.md). Especifique el nombre de la ruta de acceso del contenedor en el cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX](http://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)   
 [Probar propiedades y eventos con un contenedor de prueba](http://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917)   
 [Depuración de COM y ActiveX](../debugger/com-and-activex-debugging.md)   
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)
