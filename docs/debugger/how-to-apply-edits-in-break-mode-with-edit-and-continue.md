---
title: "C&#243;mo: Aplicar tareas de edici&#243;n en modo de interrupci&#243;n con Editar y continuar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.variables.failededit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
helpviewer_keywords: 
  - "modo de interrupción, aplicar cambios del código"
  - "código, editar en modo de interrupción"
  - "incluir en código, editar en modo de interrupción"
  - "Editar y continuar [Visual Basic], aplicar tareas de edición en modo de interrupción"
  - "Editar y continuar, aplicar tareas de edición en modo de interrupción"
  - "editar, modo de interrupción"
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 30
---
# C&#243;mo: Aplicar tareas de edici&#243;n en modo de interrupci&#243;n con Editar y continuar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede utilizar la opción Editar y continuar para modificar el código en modo de interrupción y, posteriormente, continuar sin detener ni reiniciar la ejecución.  
  
 La opción Editar y continuar no se encuentra disponible en los siguientes escenarios de depuración:  
  
-   Depuración en modo mixto \(nativa o administrada\).  
  
-   Depuración de SQL.  
  
-   Depuración de un volcado de Dr.  Volcado de memoria de Watson.  
  
-   Edición de código tras una excepción no controlada, cuando no se ha seleccionado la opción **Desenredar la pila de llamadas de las excepciones no controladas**.  
  
-   Depuración de una aplicación incrustada en tiempo de ejecución.  
  
-   Depuración de una aplicación con **Asociar a**, en lugar de ejecutar la aplicación con **Iniciar** desde el menú **Depurar**.  
  
-   Depuración de código optimizado.  
  
-   Depuración de código administrado cuando el destino es una aplicación de 64 bits.  Si desea utilizar la opción Editar y continuar, deberá establecer el destino en x86.  \(*Proyecto***Propiedades**, pestaña **Compilar**, **Configuración de compilador avanzada**\).  
  
-   Depuración de una versión anterior del código cuando no se haya podido generar una nueva versión debido a errores de compilación.  
  
### Para editar código en modo de interrupción  
  
1.  Entre en el modo de interrupción siguiendo uno de estos pasos:  
  
    -   Establezca un punto de interrupción en el código y, a continuación, elija **Iniciar depuración** en el menú **Depurar**; espere a que la aplicación llegue al punto de interrupción.  
  
         \-O bien\-  
  
    -   Inicie la depuración y, a continuación, seleccione **Interrumpir todos** en el menú **Depurar**.  
  
         \-O bien\-  
  
    -   Si se produce una excepción, elija **Habilitar edición** en el **Asistente de excepciones**.  
  
2.  Realice todos los cambios que desee en el código, siempre y cuando sean válidos.  
  
     Para obtener más información, vea [Ediciones no compatibles en Editar y continuar de Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md).  
  
    > [!NOTE]
    >  Si intenta realizar un cambio en el código no permitido por Editar y continuar, el cambio quedará subrayado con una línea ondulada de color púrpura y aparecerá una tarea en la Lista de tareas.  No podrá reanudar la ejecución del código hasta que deshaga este cambio no válido en el código.  
  
3.  En el menú **Depurar**, haga clic en **Continuar** para reanudar la ejecución.  
  
     El código se ejecutará con los cambios aplicados incorporados al proyecto.  
  
## Vea también  
 [Ediciones no compatibles en Editar y continuar de Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [Editar y continuar \(Visual Basic\)](../debugger/edit-and-continue-visual-basic.md)