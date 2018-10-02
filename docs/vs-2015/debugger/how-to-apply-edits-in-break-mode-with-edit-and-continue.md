---
title: 'Cómo: aplicar tareas de edición en modo de interrupción con Editar y continuar | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c9b380c4a28beb50a2048eb00aa68f81bf27449
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "47593032"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>Cómo: Aplicar tareas de edición en modo de interrupción con Editar y continuar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: aplicar ediciones en modo de interrupción con Editar y continuar](https://docs.microsoft.com/visualstudio/debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue).  
  
Puede utilizar la opción Editar y continuar para modificar el código en modo de interrupción y, posteriormente, continuar sin detener ni reiniciar la ejecución.  
  
 La opción Editar y continuar no se encuentra disponible en los siguientes escenarios de depuración:  
  
-   Depuración en modo mixto (nativa o administrada).  
  
-   Depuración de SQL.  
  
-   Depuración de un volcado de Dr. Volcado de memoria de Watson.  
  
-   Edición de código tras una excepción no controlada, cuando no se ha seleccionado la opción **Desenredar la pila de llamadas de las excepciones no controladas** .  
  
-   Depuración de una aplicación incrustada en tiempo de ejecución.  
  
-   Depurar una aplicación con **adjuntar a** en lugar de ejecutar la aplicación con **iniciar** desde el **depurar** menú.  
  
-   Depuración de código optimizado.  
  
-   Depuración de código administrado cuando el destino es una aplicación de 64 bits. Si desea utilizar la opción Editar y continuar, deberá establecer el destino en x86. (_Proyecto_**propiedades**, **compilar** ficha, **compilador avanzada** configuración.).  
  
-   Depuración de una versión anterior del código cuando no se haya podido generar una nueva versión debido a errores de compilación.  
  
### <a name="to-edit-code-in-break-mode"></a>Para editar código en modo de interrupción  
  
1.  Entre en el modo de interrupción siguiendo uno de estos pasos:  
  
    -   Establezca un punto de interrupción en el código y luego elija **Iniciar depuración** desde el **depurar** menú y espere a que la aplicación en el punto de interrupción.  
  
         -O bien-  
  
    -   Inicie la depuración y, a continuación, seleccione **interrumpir todos** desde el **depurar** menú.  
  
         -O bien-  
  
    -   Si se produce una excepción, elija **Habilitar edición** en el**Asistente de excepciones**.  
  
2.  Realice todos los cambios que desee en el código, siempre y cuando sean válidos.  
  
     Para obtener más información, consulte [ediciones no compatibles en Visual Basic editar y continuar](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md).  
  
    > [!NOTE]
    >  Si intenta realizar un cambio en el código no permitido por Editar y continuar, el cambio quedará subrayado con una línea ondulada de color púrpura y aparecerá una tarea en la Lista de tareas. No podrá reanudar la ejecución del código hasta que deshaga este cambio no válido en el código.  
  
3.  En el **depurar** menú, haga clic en **continuar** para reanudar la ejecución.  
  
     El código se ejecutará con los cambios aplicados incorporados al proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Ediciones no compatibles en Visual Basic, edición y continuar](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [Editar y continuar (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)



