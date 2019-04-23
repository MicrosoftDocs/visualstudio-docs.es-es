---
title: Aplicar tareas de edición en modo de interrupción con Editar y continuar | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ecc36ae8ce0ccbe75cddb94ea69d953cc6307b0b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050964"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Procedimiento Aplicar tareas de edición en modo de interrupción con Editar y continuar (Visual Basic)
Puede utilizar la opción Editar y continuar para modificar el código en modo de interrupción y, posteriormente, continuar sin detener ni reiniciar la ejecución.

Para conocer las limitaciones sobre el uso de editar y continuar durante la depuración, vea [Supported Code Changes (C# y Visual Basic)](../debugger/supported-code-changes-csharp.md).

### <a name="to-edit-code-in-break-mode"></a>Para editar código en modo de interrupción

1. Entre en el modo de interrupción siguiendo uno de estos pasos:

    - Establezca un punto de interrupción en el código y, a continuación, elija **Iniciar depuración** en el menú **Depurar**. Luego, espere a que la aplicación llegue al punto de interrupción.

         -o bien-

    - Inicie la depuración y, a continuación, seleccione **Interrumpir todo** en el menú **Depurar**.

         -o bien-

    - Si se produce una excepción, elija **Habilitar edición** en el **Asistente de excepciones**.

2. Realice los cambios de código deseadas y compatibles.

     Para obtener más información, consulte [Supported Code Changes (C# y Visual Basic)](../debugger/supported-code-changes-csharp.md).

    > [!NOTE]
    >  Si intenta realizar un cambio en el código no permitido por Editar y continuar, el cambio quedará subrayado con una línea ondulada de color púrpura y aparecerá una tarea en la Lista de tareas. No podrá reanudar la ejecución del código hasta que deshaga este cambio no válido en el código.

3. En el menú **Depurar**, haga clic en **Continuar** para reanudar la ejecución.

     El código se ejecutará con los cambios aplicados incorporados al proyecto.

## <a name="see-also"></a>Vea también
- [Cambios admitidos en el código (C# y Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Editar y continuar (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
