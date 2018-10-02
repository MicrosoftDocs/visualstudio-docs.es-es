---
title: 'Cómo: restaurar los comandos ocultos del depurador | Microsoft Docs'
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
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61021e902befc29d90505e3e9c28f1b9dde3ded3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578142"
---
# <a name="how-to-restore-hidden-debugger-commands"></a>Cómo: Restaurar los comandos ocultos del depurador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: restaurar comandos ocultos del depurador](https://docs.microsoft.com/visualstudio/debugger/how-to-restore-hidden-debugger-commands).  
  
Cuando se configura Visual Studio, se solicita la elección de un conjunto de configuraciones IDE predeterminadas para el lenguaje de programación principal. Las configuraciones IDE predeterminadas para algunos lenguajes pueden ocultar ciertos comandos del depurador.  
  
 Si desea utilizar una característica del depurador oculta por la configuración de IDE predeterminada, puede agregar de nuevo el comando al menú utilizando el procedimiento siguiente.  
  
### <a name="to-restore-hidden-debugger-commands"></a>Restablecer comandos ocultos del depurador  
  
1.  Con un proyecto abierto, en el **herramientas** menú, haga clic en **personalizar**.  
  
2.  En el **personalizar** cuadro de diálogo, haga clic en el **comandos** ficha.  
  
3.  En el **barra de menús:** lista desplegable, seleccione el **depurar** menú que desea que contenga el comando restaurado.  
  
4.  Haga clic en el **Agregar comando...** .  
  
5.  En el **Agregar comando** , seleccione el comando que desee agregar y haga clic en **Aceptar**.  
  
6.  Repita el paso anterior para agregar otro comando.  
  
7.  Haga clic en **cerrar** cuando haya terminado de agregar comandos al menú.  
  
    > [!WARNING]
    >  Algunos elementos de menú sólo aparecen cuando el depurador se encuentra en modos concretos, como el modo de ejecución o el modo de interrupción. Por consiguiente, es posible que un elemento agregado no sea visible inmediatamente después de realizar estos pasos.  
  
## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>Restablecer los comandos no disponibles en el cuadro de diálogo Personalizar  
 Algunos comandos, especialmente las que se encuentran en los menús jerárquicos, no se puede restaurar desde el **personalizar** cuadro de diálogo. Para restaurarlos, debe importar una nueva colección de configuraciones IDE.  
  
#### <a name="to-import-new-ide-settings"></a>Para importar nuevas configuraciones IDE  
  
1.  En el **herramientas** menú, haga clic en **importar y exportar configuraciones**.  
  
2.  En el **Asistente para importar y exportar configuración** página, haga clic en **importar la configuración de entorno seleccionada**y, a continuación, haga clic en **siguiente**.  
  
3.  En el **Guardar configuración actual** página, decida si desea guardar la configuración existente y, a continuación, haga clic en o no **siguiente**.  
  
4.  En el **elija una colección de configuraciones para importar** página, en el **la configuración predeterminada de** carpeta, elija una colección de configuraciones de desarrollo que incluya los comandos que desea usar. Si no sabe qué colección utilizar, pruebe **configuración General de desarrollo** o **configuración de desarrollo de Visual C++**, que proporcionan el máximo partido a los comandos de depurador.  
  
5.  Haga clic en **Siguiente**.  
  
6.  En el **elegir configuraciones para importar** página, en **opciones**, asegúrese de que **depuración** está seleccionada. Desactive las otras casillas, a menos que también desee importar dicha configuración.  
  
7.  Haga clic en **Finalizar**.  
  
8.  En el **importación completada** página, revise cualquier error asociado con el restablecimiento de la configuración bajo **detalles**.  
  
9. Haga clic en **Cerrar**.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)



