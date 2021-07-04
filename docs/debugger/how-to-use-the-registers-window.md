---
title: Visualización de valores de registro en el depurador | Microsoft Docs
description: Vea los valores de registro en la ventana Registros de Visual Studio. Durante la depuración, los valores de registro cambian a medida que el código se ejecuta en la aplicación.
ms.custom: SEO-VS-2020
ms.date: 11/19/2018
ms.topic: how-to
f1_keywords:
- vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e2648f74453f51cd8d655ccb0c2344eb1030c1ed
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385401"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Visualización de valores de registro en la ventana Registros (C#, C++, Visual Basic, F#)

En la ventana **Registros** se muestra el contenido de los registros durante la depuración en Visual Studio. Para obtener una introducción general de los conceptos subyacentes a los registros y la ventana **Registros**, vea [Fundamentos de depuración: ventana Registros](../debugger/debugging-basics-registers-window.md).

> [!NOTE]
> La información de los registros no está disponible para las aplicaciones de script o SQL.

Durante la depuración, los valores de registro cambian a medida que el código se ejecuta en la aplicación. Los valores que han cambiado recientemente aparecen en color rojo en la ventana **Registros**.

Por motivos de claridad, la ventana **Registros** organiza los registros en grupos que varían según la plataforma y el tipo de procesador. Puede mostrar u ocultar grupos de registros. Para obtener más información, vea [Cómo: mostrar y ocultar grupos de registros](../debugger/how-to-display-and-hide-register-groups.md).

Para obtener información sobre las marcas que se ven en la ventana **Registros**, vea [Acerca de la ventana Registros](../debugger/debugging-basics-registers-window.md)

Se pueden modificar los valores de los registros. Para obtener más información, vea [Cómo: editar un valor de registro](../debugger/how-to-edit-a-register-value.md).

**Para abrir la ventana Registros**

1. Para habilitar la depuración de nivel de dirección, seleccione **Habilitar la depuración de nivel de dirección** en **Herramientas** (o **Depurar**) > **Opciones** > **Depuración**.

1. Mientras se ejecuta la depuración o en un punto de interrupción, seleccione **Depurar** > **Ventanas** > **Registros**, o bien presione **Alt**+**5**.

>[!NOTE]
>Es posible que los cuadros de diálogo y los comandos de menú varíen en función de la configuración o la edición de Visual Studio. Para cambiar la configuración, seleccione **Importar y exportar configuraciones** en el menú **Herramientas** de Visual Studio. Para obtener más información, vea [Restablecer la configuración](../ide/environment-settings.md#reset-settings).

### <a name="see-also"></a>Vea también

- [Fundamentos de la depuración: Ventana Registros](../debugger/debugging-basics-registers-window.md)
- [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)
