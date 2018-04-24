---
title: 'Cómo: restaurar los comandos ocultos del depurador | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f47f8cbb342f480e6124f765b3b427a615ec6a38
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-restore-hidden-debugger-commands"></a>Cómo: Restaurar los comandos ocultos del depurador
Cuando se configura Visual Studio, se solicita la elección de un conjunto de configuraciones IDE predeterminadas para el lenguaje de programación principal. Las configuraciones IDE predeterminadas para algunos lenguajes pueden ocultar ciertos comandos del depurador.  
  
 Si desea utilizar una característica del depurador oculta por la configuración de IDE predeterminada, puede agregar de nuevo el comando al menú utilizando el procedimiento siguiente.  
  
### <a name="to-restore-hidden-debugger-commands"></a>Restablecer comandos ocultos del depurador  
  
1.  Con un proyecto abierto, en la **herramientas** menú, haga clic en **personalizar**.  
  
2.  En el **personalizar** cuadro de diálogo, haga clic en el **comandos** ficha.  
  
3.  En el **barra de menús:** lista desplegable, seleccione la **depurar** menú que desea que contenga el comando restaurado.  
  
4.  Haga clic en el **Agregar comando...**  botón.  
  
5.  En el **Agregar comando** , seleccione el comando que desea agregar y haga clic en **Aceptar**.  
  
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
  
4.  En el **elegir una colección de configuraciones para importar** página, en la **la configuración predeterminada de** carpeta, elija una colección de configuraciones de desarrollo que incluya los comandos que desea utilizar. Si no sabe qué colección utilizar, pruebe **configuración General de desarrollo** o **configuración de desarrollo de Visual C++**, que ofrecen más comandos de depuración.  
  
5.  Haga clic en **Siguiente**.  
  
6.  En el **elegir configuraciones para importar** página, en **opciones**, asegúrese de que **depuración** está seleccionada. Desactive las otras casillas, a menos que también desee importar dicha configuración.  
  
7.  Haga clic en **Finalizar**.  
  
8.  En el **importación completada** página, revise cualquier error asociado con el restablecimiento de la configuración bajo **detalles**.  
  
9. Haga clic en **Cerrar**.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)