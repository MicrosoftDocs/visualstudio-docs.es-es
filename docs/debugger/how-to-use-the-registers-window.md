---
title: Ver los valores de registro en el depurador de Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f236bf43d3667cd4263d205c4588593a973824d
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257178"
---
# <a name="view-register-values-and-use-the-registers-window-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Ver los valores de registrar y usar la ventana registros en el depurador de Visual Studio (C#, C++, Visual Basic, F#)
La ventana registros sólo está disponible si la depuración de nivel de dirección está habilitada en el **opciones** cuadro de diálogo, **depuración** nodo, **General** categoría.  
  
 El **registra** ventana muestra el contenido del registro. Si mantiene el **registra** ventana abierta al ir avanzando por el programa, puede ver cómo cambian los valores de registro mientras se ejecuta el código. Los valores que han cambiado recientemente se muestran en rojo. Se pueden modificar los valores de los registros. Para obtener más información, consulte [Cómo: editar el valor de un registro](../debugger/how-to-edit-a-register-value.md).  
  
 Para reducir el desorden, el **registra** ventana registros organiza en grupos, que pueden variar según la plataforma y el procesador de tipo. Puede mostrar u ocultar grupos como desee. Para obtener más información, consulte [Cómo: mostrar y ocultar grupos de registros](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Para obtener una introducción de alto nivel conceptos relacionados con los registros y la ventana registros, vea [Fundamentos de depuración: ventana registros](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-display-the-registers-window"></a>Para mostrar la ventana Registros  
  
-   En el **depurar** menú, elija **Windows**y, a continuación, elija **registra** (o elija **Ctrl** + **Alt**   +  **G**).  
  
     El depurador debe encontrarse en modo de interrupción.  
  
    > [!NOTE]
    >  La información de los registros no está disponible para las aplicaciones de script o SQL.  
  
## <a name="see-also"></a>Vea también  
 [Fundamentos de la depuración: ventana Registros](../debugger/debugging-basics-registers-window.md)   
 [Visualización de datos en el depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Fundamentos de la depuración: ventana Registros](../debugger/debugging-basics-registers-window.md)