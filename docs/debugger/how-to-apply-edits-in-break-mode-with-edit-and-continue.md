---
title: Aplicación de ediciones en el modo de interrupción con Editar y continuar | Microsoft Docs
description: Vea cómo usar Editar y continuar para editar el código de Visual Basic en modo de interrupción. Hay varias formas de entrar en el modo de interrupción.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a9074d992c06c1b7d49f59481bee35345c5199f8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155047"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Procedimiento Aplicación de ediciones en el modo de interrupción con Editar y continuar (Visual Basic)
Puede utilizar la opción Editar y continuar para modificar el código en modo de interrupción y, posteriormente, continuar sin detener ni reiniciar la ejecución.

Para conocer las limitaciones sobre el uso de Editar y continuar durante la depuración, vea [Cambios de código admitidos (C# y Visual Basic)](../debugger/supported-code-changes-csharp.md).

### <a name="to-edit-code-in-break-mode"></a>Para editar código en modo de interrupción

1. Entre en el modo de interrupción siguiendo uno de estos pasos:

    - Establezca un punto de interrupción en el código y, a continuación, elija **Iniciar depuración** en el menú **Depurar**. Luego, espere a que la aplicación llegue al punto de interrupción.

         o bien

    - Inicie la depuración y, a continuación, seleccione **Interrumpir todo** en el menú **Depurar**.

         o bien

    - Si se produce una excepción, elija **Habilitar edición** en el **Asistente de excepciones**.

2. Realice los cambios de código admitidos que desee.

     Para obtener más información, vea [Cambios de código admitidos (C# y Visual Basic)](../debugger/supported-code-changes-csharp.md).

    > [!NOTE]
    > Si intenta realizar un cambio en el código no permitido por Editar y continuar, el cambio quedará subrayado con una línea ondulada de color púrpura y aparecerá una tarea en la Lista de tareas. No podrá reanudar la ejecución del código hasta que deshaga este cambio no válido en el código.

3. En el menú **Depurar**, haga clic en **Continuar** para reanudar la ejecución.

     El código se ejecutará con los cambios aplicados incorporados al proyecto.

## <a name="see-also"></a>Vea también
- [Cambios de código admitidos (C# y Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Editar y continuar (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
