---
title: "Editar y continuar (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
helpviewer_keywords: 
  - "Editar y continuar de 64 bits"
  - "depurar [Visual Basic], Editar y continuar"
  - "Editar y continuar [Visual Basic]"
  - "Editar y continuar, 64 bits"
  - "Visual Basic, Editar y continuar"
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
caps.latest.revision: 40
caps.handback.revision: 40
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Editar y continuar (Visual Basic)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Editar y continuar es una característica de depuración de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] que le permite realizar cambios en el código mientras se ejecuta en modo de interrupción.  Una vez que se aplican los cambios de código, se puede reanudar su ejecución con las nuevas modificaciones en contexto y observar el efecto.  
  
 Es posible utilizar la característica Editar y continuar cada vez que se entra en el modo de interrupción.  En modo de interrupción, el puntero de instrucciones \(una punta de flecha amarilla en la ventana de código fuente\) señala la línea que se ejecutará a continuación y se ubicará en una instrucción ejecutable dentro de un cuerpo de método o propiedad.  Se puede realizar casi cualquier tipo de cambio en las instrucciones ejecutables mientras se está en modo de interrupción; dicho cambio se incorporará al proyecto subyacente.  Sin embargo, mientras se está en modo de interrupción no se permite, por lo general, realizar cambios en instrucciones de declaración, como métodos, campos públicos o declaraciones de clase.  
  
 Cuando se realiza una modificación que no está autorizada, el cambio se marca con un subrayado ondulado de color púrpura y aparece una tarea en la Lista de tareas.  Si desea seguir utilizando Editar y continuar, debe deshacer el cambio no autorizado.  Es posible que algunas modificaciones no autorizadas puedan realizarse fuera de Editar y continuar.  Si desea retener los resultados de dicha modificación no autorizada, deberá detener la depuración y reiniciar la aplicación.  
  
 Editar y continuar se admite para proyectos 64 bits destinados a .NET Framework 4.5.1.  
  
 No se admite Editar y continuar si la depuración se inicia utilizando **Asociar al proceso**.  Editar y continuar no se admite para el código optimizado, el código mixto \(administrado y nativo\) o los proyectos de Compact Framework \(Smart Device\).  
  
 En los temas de esta sección se proporciona información adicional sobre cómo utilizar esta característica y los tipos de cambios no permitidos.  
  
## En esta sección  
 [Cómo: Aplicar tareas de edición en modo de interrupción con Editar y continuar](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Explica cómo aplicar cambios de código en modo de interrupción.  
  
 [Ediciones no compatibles en Editar y continuar de Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)  
 Describe los tipos de modificaciones que no pueden realizarse en Editar y continuar de [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].  
  
## Secciones relacionadas  
 [Editar y continuar](../debugger/edit-and-continue.md)  
 Ofrece una lista de temas sobre la característica Editar y continuar.