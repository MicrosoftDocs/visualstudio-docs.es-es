---
title: "Cómo: depurar un Control ActiveX | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.controls.debug
dev_langs:
- CSharp
- VB
- FSharp
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
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 11d29d2d8a5ebf4774f3b71ea72a1dd9bc58cbd0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-an-activex-control"></a>Cómo: Depurar un control ActiveX
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Para depurar el control ActiveX, debe especificar un contenedor (ejecutable) en el que ejecutar el control.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>Para especificar un contenedor para la sesión de depuración  
  
1.  En el Explorador de soluciones, seleccione el proyecto.  
  
2.  Desde el **vista** menú, elija **páginas de propiedades**.  
  
3.  En el **páginas de propiedades de proyecto** cuadro de diálogo, abra el **propiedades de configuración** carpeta y seleccione **depuración**.  
  
4.  En el **depuración** categoría, busque el **comando** propiedad.  
  
5.  Especifique el nombre de ruta de acceso para el contenedor. Por ejemplo, C:\Archivos de programa\Internet Explorer\IEXPLORE.EXE.  
  
6.  Si especifica Internet Explorer como el contenedor y está utilizando Active Desktop, escriba `/new` en el **argumentos del comando** cuadro.  
  
7.  Haga clic en **Aceptar**.  
  
     Si no especifica un contenedor en el **páginas de propiedades de proyecto** cuadro de diálogo, puede especificar el contenedor al iniciar la depuración. Cuando se selecciona un comando de ejecución para iniciar la depuración, el [archivo ejecutable para el cuadro de diálogo de sesión de depuración](../debugger/executable-for-debugging-session-dialog-box.md) aparece. Especifique el nombre de la ruta de acceso del contenedor en el cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX](/cpp/mfc/activex-controls)   
 [Probar propiedades y eventos con un contenedor de prueba](/cpp/mfc/testing-properties-and-events-with-test-container)   
 [Depurar COM y ActiveX](../debugger/com-and-activex-debugging.md)   
 [Depurar en Visual Studio](../debugger/index.md)  
 [Guía de características del depurador](../debugger/debugger-feature-tour.md)