---
title: 'Cómo: depurar un Control ActiveX | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: f1e43d94807fa28f86193fc7818b77887d797772
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745155"
---
# <a name="how-to-debug-an-activex-control"></a>Cómo: Depurar un control ActiveX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Para depurar el control ActiveX, debe especificar un contenedor (ejecutable) en el que ejecutar el control.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>Para especificar un contenedor para la sesión de depuración  
  
1.  En el Explorador de soluciones, seleccione el proyecto.  
  
2.  Desde el **vista** menú, elija **páginas de propiedades**.  
  
3.  En el **páginas de propiedades de proyecto** cuadro de diálogo, abra el **propiedades de configuración** carpeta y seleccione **depuración**.  
  
4.  En el **depuración** categoría, busque el **comando** propiedad.  
  
5.  Especifique el nombre de ruta de acceso para el contenedor. Por ejemplo, C:\Archivos de programa\Internet Explorer\IEXPLORE.EXE.  
  
6.  Si especifica Internet Explorer como el contenedor y está utilizando Active Desktop, escriba `/new` en el **argumentos de comando** cuadro.  
  
7.  Haga clic en **Aceptar**.  
  
     Si no especifica un contenedor en el **Project Property Pages** cuadro de diálogo, puede especificar el contenedor al iniciar la depuración. Cuando se selecciona un comando de ejecución para iniciar la depuración, la [archivo ejecutable para el cuadro de diálogo de sesión de depuración](../debugger/executable-for-debugging-session-dialog-box.md) aparece. Especifique el nombre de la ruta de acceso del contenedor en el cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX](http://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)   
 [Probar propiedades y eventos con un contenedor de prueba](http://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917)   
 [Depurar COM y ActiveX](../debugger/com-and-activex-debugging.md)   
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)



