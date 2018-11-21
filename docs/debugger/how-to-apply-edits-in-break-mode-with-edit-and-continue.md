---
title: 'Cómo: aplicar tareas de edición en modo de interrupción con Editar y continuar | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f45b2a64e7602d038a12f436019a8f99e352aa26
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257083"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Cómo: aplicar tareas de edición en modo de interrupción con Editar y continuar (Visual Basic)
Puede utilizar la opción Editar y continuar para modificar el código en modo de interrupción y, posteriormente, continuar sin detener ni reiniciar la ejecución.  
  
Para conocer las limitaciones sobre el uso de editar y continuar durante la depuración, vea [Supported Code Changes (C# y Visual Basic](../debugger/supported-code-changes-csharp.md)]
  
### <a name="to-edit-code-in-break-mode"></a>Para editar código en modo de interrupción  
  
1.  Entre en el modo de interrupción siguiendo uno de estos pasos:  
  
    -   Establezca un punto de interrupción en el código y luego elija **Iniciar depuración** desde el **depurar** menú y espere a que la aplicación en el punto de interrupción.  
  
         O bien  
  
    -   Inicie la depuración y, a continuación, seleccione **interrumpir todos** desde el **depurar** menú.  
  
         O bien  
  
    -   Si se produce una excepción, elija **Habilitar edición** en el **Asistente de excepciones**.  
  
2.  Realice los cambios de código deseadas y compatibles.  
  
     Para obtener más información, consulte [Supported Code Changes (C# y Visual Basic](../debugger/supported-code-changes-csharp.md).  
  
    > [!NOTE]
    >  Si intenta realizar un cambio en el código no permitido por Editar y continuar, el cambio quedará subrayado con una línea ondulada de color púrpura y aparecerá una tarea en la Lista de tareas. No podrá reanudar la ejecución del código hasta que deshaga este cambio no válido en el código.  
  
3.  En el **depurar** menú, haga clic en **continuar** para reanudar la ejecución.  
  
     El código se ejecutará con los cambios aplicados incorporados al proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Cambios admitidos en el código (C# y Visual Basic](../debugger/supported-code-changes-csharp.md)   
 [Editar y continuar (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)