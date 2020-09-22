---
title: 'Cómo: aplicar ediciones en modo de interrupción con editar y continuar | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5c04dc0ae6e5272d2544ad7436fa7ca516c9a022
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842595"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>Cómo: Aplicar tareas de edición en modo de interrupción con Editar y continuar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede utilizar la opción Editar y continuar para modificar el código en modo de interrupción y, posteriormente, continuar sin detener ni reiniciar la ejecución.  
  
 La opción Editar y continuar no se encuentra disponible en los siguientes escenarios de depuración:  
  
- Depuración en modo mixto (nativa o administrada).  
  
- Depuración de SQL.  
  
- Depuración de un volcado de Dr. Watson.  
  
- Edición de código tras una excepción no controlada, cuando no se ha seleccionado la opción **Desenredar la pila de llamadas de las excepciones no controladas** .  
  
- Depuración de una aplicación incrustada en tiempo de ejecución.  
  
- Depurar una aplicación con **adjuntar a** en lugar de ejecutar la aplicación con **Start** en el menú **depurar** .  
  
- Depuración de código optimizado.  
  
- Depuración de código administrado cuando el destino es una aplicación de 64 bits. Si desea utilizar la opción Editar y continuar, deberá establecer el destino en x86. (_Project_**Propiedades**del proyecto, pestaña **compilar** , configuración de **compilador avanzada** ).  
  
- Depuración de una versión anterior del código cuando no se haya podido generar una nueva versión debido a errores de compilación.  
  
### <a name="to-edit-code-in-break-mode"></a>Para editar código en modo de interrupción  
  
1. Entre en el modo de interrupción siguiendo uno de estos pasos:  
  
    - Establezca un punto de interrupción en el código y, a continuación, elija **Iniciar depuración** en el menú **Depurar**. Luego, espere a que la aplicación llegue al punto de interrupción.  
  
         -o bien-  
  
    - Inicie la depuración y, a continuación, seleccione **Interrumpir todo** en el menú **Depurar**.  
  
         -o bien-  
  
    - Cuando se produzca una excepción, elija **Habilitar edición** en el**Asistente de excepciones**.  
  
2. Realice todos los cambios que desee en el código, siempre y cuando sean válidos.  
  
     Para obtener más información, consulte [ediciones no compatibles en Visual Basic editar y continuar](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md).  
  
    > [!NOTE]
    > Si intenta realizar un cambio en el código no permitido por Editar y continuar, el cambio quedará subrayado con una línea ondulada de color púrpura y aparecerá una tarea en la Lista de tareas. No podrá reanudar la ejecución del código hasta que deshaga este cambio no válido en el código.  
  
3. En el menú **Depurar**, haga clic en **Continuar** para reanudar la ejecución.  
  
     El código se ejecutará con los cambios aplicados incorporados al proyecto.  
  
## <a name="see-also"></a>Consulte también  
 [Ediciones no compatibles en Visual Basic editar y continuar](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [Editar y continuar (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
