---
title: Visualización del código de desensamblado en el depurador | Microsoft Docs
description: Use la ventana Desensamblado en Visual Studio para ver el código de ensamblado correspondiente a las instrucciones que ha creado el compilador.
ms.custom: SEO-VS-2020, seodec18
ms.date: 10/30/2018
ms.topic: how-to
f1_keywords:
- vs.debug.disassembly
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b7d772ed757b231ce68fe27b74123f7f5878d0ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99845053"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Visualización del código de desensamblado en el depurador de Visual Studio (C#, C++, Visual Basic, F#)

En la ventana **Desensamblado** se muestra el código de ensamblado correspondiente a las instrucciones creadas por el compilador. Si depura código administrado, estas instrucciones de ensamblado se corresponden al código nativo creado por el compilador JIT y no al lenguaje intermedio de Microsoft (MSIL) que genera el compilador de Visual Studio.

> [!NOTE]
> Para sacar el máximo partido de la ventana **Desensamblado**, infórmese bien sobre los conceptos básicos de la [programación del lenguaje de ensamblado](https://wikipedia.org/wiki/Assembly_language).

Esta característica solo está disponible si está habilitada la depuración en el nivel de dirección. No está disponible para la depuración de scripts ni de SQL.

Además de las instrucciones de ensamblado, la ventana **Desensamblado** puede mostrar la siguiente información opcional:

- Dirección de memoria donde se encuentra cada instrucción máquina. Para aplicaciones nativas, esta es la dirección de memoria real. Para Visual Basic o C#, es un desplazamiento desde el inicio de la función.

- Código fuente del que se deriva el código ensamblado.

- Bytes de código, esto es, representaciones en bytes de las instrucciones máquina o MSIL reales.

- Nombres de símbolos para las direcciones de memoria.

- Número de líneas correspondiente al código fuente.

Las instrucciones en lenguaje de ensamblado constan de *mnemónicos*, que son abreviaturas de nombres de instrucciones, y de *símbolos* para variables, registros y constantes. Cada instrucción de código máquina se representa con un mnemónico de lenguaje de ensamblado, opcionalmente seguido de uno o más símbolos.

El código de ensamblado se basa en gran medida en registros de procesador o, en el caso de código administrado, en registros de Common Language Runtime. Puede usar la ventana **Desensamblado** junto con la ventana **Registros**, que le permite examinar el contenido de los registros.

Para ver las instrucciones de código máquina en forma numérica sin formato, en lugar de como lenguaje de ensamblado, use la ventana **Memoria** o seleccione **Bytes de código** en el menú contextual de la ventana **Desensamblado**.

## <a name="use-the-disassembly-window"></a>Uso de la ventana Desensamblado

Para habilitar la ventana **Desensamblado**, en **Herramientas** > **Opciones** > **Depuración**, seleccione **Habilitar la depuración de nivel de dirección**.

Para abrir la ventana **Desensamblado** durante la depuración, seleccione **Windows** > **Desensamblado** o presione **Alt**+**8**.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, vea [Restablecer la configuración](../ide/environment-settings.md#reset-settings).

Para activar o desactivar información opcional, haga clic con el botón secundario en la ventana **Desensamblado** y active o desactive las opciones que desee en el menú contextual.

Una flecha amarilla en el margen izquierdo indica el punto de ejecución actual. Para el código nativo, el punto de ejecución se corresponde con el contador de programas de la CPU. Esta ubicación indica la instrucción que debe ejecutarse a continuación en el programa.

## <a name="see-also"></a>Vea también

* [Retroceder o avanzar en la memoria](../debugger/how-to-page-up-or-down-in-memory.md)
* [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)
* [Cómo: Uso de la ventana Registros](../debugger/how-to-use-the-registers-window.md)