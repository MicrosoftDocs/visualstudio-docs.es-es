---
title: Ver el código de desensamblado en el depurador de Visual Studio | Documentos de Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 10/30/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9733569c3fa53d2c5a5905b5b893d16b4eeaf10b
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257048"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Ver el código de desensamblado en el depurador de Visual Studio (C#, C++, Visual Basic, F#)

El **desensamblado** ventana muestra el código de ensamblado correspondiente a las instrucciones creadas por el compilador. Si depura código administrado, estas instrucciones de ensamblado corresponden al código nativo creado por el compilador Just-in-Time (JIT), no el lenguaje intermedio de Microsoft (MSIL) que creado por el compilador de Visual Studio.  
  
> [!NOTE]
> Para aprovechar al máximo la **desensamblado** ventana, comprender o aprender los conceptos básicos de [programación de lenguaje de ensamblado](https://wikipedia.org/wiki/Assembly_language).
  
Esta característica solo está disponible si está habilitada la depuración de nivel de dirección. No está disponible para la depuración de SQL o la secuencia de comandos. 

Además de las instrucciones de ensamblado, el **desensamblado** ventana puede mostrar la siguiente información opcional:  
  
- Dirección de memoria donde se encuentra cada instrucción máquina. Para aplicaciones nativas, es la dirección de memoria real. Para Visual Basic o C#, es un desplazamiento desde el principio de la función.  
  
- Código fuente del que se deriva el código ensamblado.  
  
- Código de bytes, es decir, las representaciones de bytes de las instrucciones de MSIL o real del equipo.  
  
- Nombres de símbolos para las direcciones de memoria.  
  
- Número de líneas correspondiente al código fuente.  
  
Las instrucciones de lenguaje de ensamblado consta de *teclas de acceso*, que son abreviaturas de nombres de instrucciones, y *símbolos* para variables, registros y constantes. Cada instrucción de código máquina se representa con un mnemónico de lenguaje de ensamblado seguido opcionalmente por uno o más símbolos.  
  
Código de ensamblado se basa principalmente en los registros del procesador, o bien, para código administrado, common language runtime registra. Puede usar el **desensamblado** ventana junto con el **registra** ventana, que le permite examinar el contenido de los registros.  
  
Para ver las instrucciones de código máquina en su formato numérico sin procesar, en lugar de como lenguaje de ensamblado, utilice el **memoria** ventana o seleccione **Bytes de código** en el menú contextual en el **desensamblado**  ventana.  
  
## <a name="use-the-disassembly-window"></a>Utilice la ventana Desensamblado

Para habilitar el **desensamblado** ventana, en **herramientas** > **opciones** (o **herramientas**  >  **Opciones**) > **depuración**, seleccione **habilitar la depuración de nivel de dirección**.

Para abrir el **desensamblado** ventana durante la depuración, seleccione **Windows** > **desensamblado** o presione **Alt** + **8**.

> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
Para activar o desactivar la información opcional, haga clic en el **desensamblado** ventana y Active o desactive las opciones que desee en el menú contextual.  

Una flecha amarilla en el margen izquierdo marca el punto de ejecución actual. Para código nativo, el punto de ejecución corresponde al contador de programas de la CPU. Esta ubicación indica la instrucción que debe ejecutarse a continuación en el programa.  

## <a name="see-also"></a>Vea también  

* [Retroceder o avanzar en la memoria](../debugger/how-to-page-up-or-down-in-memory.md)
* [Visualización de datos en el depurador](../debugger/viewing-data-in-the-debugger.md)
* [Cómo: utilizar la ventana registros](../debugger/how-to-use-the-registers-window.md)
