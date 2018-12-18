---
title: 'Cómo: usar la ventana Desensamblado | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.disassembly
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67f9307f2f5fece64ee2ee11dd48863b9a951180
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760917"
---
# <a name="how-to-use-the-disassembly-window"></a>Cómo: Utilizar la ventana Desensamblado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta característica solo está disponible si está habilitada la depuración de nivel de dirección la **opciones** cuadro de diálogo, **depuración** nodo. No está disponible para la depuración de script ni de SQL.  
  
 El **desensamblado** ventana muestra el código de ensamblado correspondiente a las instrucciones creadas por el compilador. Si depura código administrado, estas instrucciones de ensamblado corresponden al código nativo creado por el compilador JIT, y no al lenguaje intermedio de Microsoft (MSIL) que genera el compilador de Visual Studio.  
  
 Además de las instrucciones de ensamblado, el **desensamblado** ventana puede mostrar la siguiente información opcional:  
  
- Dirección de memoria donde se encuentra cada instrucción máquina. Para aplicaciones nativas, ésta es la dirección de memoria real. Para Visual Basic, C# o código administrado, es un desplazamiento desde el inicio de la función.  
  
- Código fuente del que se deriva el código ensamblado.  
  
- Bytes de código: representaciones en bytes de las instrucciones máquina o MSIL reales.  
  
- Nombres de símbolos para las direcciones de memoria.  
  
- Número de líneas correspondiente al código fuente.  
  
  Las instrucciones en lenguaje de ensamblado consta de mnemónicos, que son abreviaturas de nombres de instrucciones, y de símbolos que representan variables, registros y constantes. Cada instrucción de código máquina se representa con un mnemónico de lenguaje de ensamblado, normalmente seguido de una o más variables, registros o constantes.  
  
  Si no conoce el lenguaje de ensamblado pero desea aprovechar al máximo la ventana Desensamblado, hágase con un buen libro sobre programación en lenguaje de ensamblado. La programación en este lenguaje queda fuera del alcance de esta breve introducción sobre la ventana Desensamblado.  
  
  Debido a que el código de ensamblado se refiere continuamente a los registros del procesador (o, en el caso del código administrado, a los registros de Common Language Runtime), a menudo le resultará útil usar la ventana Desensamblado junto con la ventana Registros, que permite observar el contenido de los registros.  
  
  Probablemente, nunca sentirá el deseo de ver las instrucciones de código máquina con su formato puro, numérico, en lugar del lenguaje de ensamblado. Sin embargo, si así lo desea, puede usar la ventana Memoria con este fin, o elegir Bytes de código en el menú contextual de la ventana Desensamblado.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-disassembly-window"></a>Para mostrar la ventana Desensamblado  
  
-   En el **depurar** menú, elija **Windows**y haga clic en **desensamblado**.  
  
     El depurador debe encontrarse en modo de interrupción.  
  
### <a name="to-turn-optional-information-on-or-off"></a>Para activar o desactivar la información opcional  
  
-   Haga clic en el **desensamblado** ventana y Active o desactive las opciones que desee en el menú contextual.  
  
     Una flecha amarilla en el margen izquierdo indica la ubicación del punto de ejecución actual. Para el código nativo, este punto se corresponde con el contador de programas de la CPU. Esta ubicación indica la instrucción que debe ejecutarse a continuación en el programa.  
  
     Para obtener más información, consulte [retroceder o avanzar en la memoria](../debugger/how-to-page-up-or-down-in-memory.md).  
  
## <a name="see-also"></a>Vea también  
 [Visualización de datos en el depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Cómo: Usar la ventana Registros](../debugger/how-to-use-the-registers-window.md)





