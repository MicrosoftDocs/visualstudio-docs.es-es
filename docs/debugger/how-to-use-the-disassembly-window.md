---
title: "Ver código de desensamblado en el depurador de Visual Studio | Documentos de Microsoft"
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c53f5404eb127f2f5eb9ec844024beafaad22e86
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger"></a>Ver el código de desensamblado en el depurador de Visual Studio
Esta característica solo está disponible si está habilitada la depuración de nivel de dirección la **opciones** cuadro de diálogo, **depuración** nodo. No está disponible para la depuración de script ni de SQL.  
  
 El **desensamblado** ventana muestra el código de ensamblado correspondiente a las instrucciones creadas por el compilador. Si depura código administrado, estas instrucciones de ensamblado corresponden al código nativo creado por el compilador JIT, y no al lenguaje intermedio de Microsoft (MSIL) que genera el compilador de Visual Studio.  
  
 Además de las instrucciones de ensamblado, el **desensamblado** ventana puede mostrar la siguiente información opcional:  
  
-   Dirección de memoria donde se encuentra cada instrucción máquina. Para aplicaciones nativas, ésta es la dirección de memoria real. Para Visual Basic, C# o código administrado, es un desplazamiento desde el inicio de la función.  
  
-   Código fuente del que se deriva el código ensamblado.  
  
-   Bytes de código: representaciones en bytes de las instrucciones máquina o MSIL reales.  
  
-   Nombres de símbolos para las direcciones de memoria.  
  
-   Número de líneas correspondiente al código fuente.  
  
 Las instrucciones en lenguaje de ensamblado consta de mnemónicos, que son abreviaturas de nombres de instrucciones, y de símbolos que representan variables, registros y constantes. Cada instrucción de código máquina se representa con un mnemónico de lenguaje de ensamblado, normalmente seguido de una o más variables, registros o constantes.  
  
 Si no conoce el lenguaje de ensamblado pero desea aprovechar al máximo la ventana Desensamblado, hágase con un buen libro sobre programación en lenguaje de ensamblado. La programación en este lenguaje queda fuera del alcance de esta breve introducción sobre la ventana Desensamblado.  
  
 Debido a que el código de ensamblado se refiere continuamente a los registros del procesador (o, en el caso del código administrado, a los registros de Common Language Runtime), a menudo le resultará útil usar la ventana Desensamblado junto con la ventana Registros, que permite observar el contenido de los registros.  
  
 Probablemente, nunca sentirá el deseo de ver las instrucciones de código máquina con su formato puro, numérico, en lugar del lenguaje de ensamblado. Sin embargo, si así lo desea, puede usar la ventana Memoria con este fin, o elegir Bytes de código en el menú contextual de la ventana Desensamblado.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-display-the-disassembly-window"></a>Para mostrar la ventana Desensamblado  
  
-   Durante la depuración, seleccione **Depurar > Windows** y, a continuación, haga clic en **desensamblado**.
  
### <a name="to-turn-optional-information-on-or-off"></a>Para activar o desactivar la información opcional  
  
-   Haga clic en el **desensamblado** ventana y Active o desactive las opciones que desee en el menú contextual.  
  
     Una flecha amarilla en el margen izquierdo indica la ubicación del punto de ejecución actual. Para el código nativo, este punto se corresponde con el contador de programas de la CPU. Esta ubicación indica la instrucción que debe ejecutarse a continuación en el programa.  
  
     Para obtener más información, consulte [retroceder o avanzar en la memoria](../debugger/how-to-page-up-or-down-in-memory.md).  
  
## <a name="see-also"></a>Vea también  
 [Ver los datos en el depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Cómo: Usar la ventana Registros](../debugger/how-to-use-the-registers-window.md)