---
title: Ver los valores de registro en el depurador de Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7aa89b6e8d36c3eb47168c8672fb7eea1e3507db
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="view-register-values-and-use-the-registers-window-in-the-visual-studio-debugger"></a>Ver valores de registrar y utilizar la ventana se registra en el depurador de Visual Studio
La ventana registros solo está disponible si está habilitada la depuración de nivel de dirección en la **opciones** cuadro de diálogo, **depuración** nodo, **General** categoría.  
  
 El **registra** ventana muestra el contenido del registro. Si decide mantener la **registra** ventana abierta recorre el programa paso a paso, puede ver cómo cambian los valores mientras se ejecuta el código. Los valores que han cambiado recientemente se muestran en rojo. Se pueden modificar los valores de los registros. Para obtener más información, consulte [Cómo: editar un valor registrar](../debugger/how-to-edit-a-register-value.md).  
  
 Para reducir la acumulación de elementos, el **registra** ventana registros organiza en grupos, que varían según la plataforma y el procesador de tipo. Puede mostrar u ocultar grupos como desee. Para obtener más información, consulte [Cómo: mostrar y ocultar grupos de registros](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Para obtener una introducción general a los conceptos relativos a registros y la ventana registros, vea [Fundamentos de depuración: ventana registros](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-display-the-registers-window"></a>Para mostrar la ventana Registros  
  
-   En el **depurar** menú, elija **Windows**y, a continuación, elija **registra**.  
  
     El depurador debe encontrarse en modo de interrupción.  
  
    > [!NOTE]
    >  La información de los registros no está disponible para las aplicaciones de script o SQL.  
  
## <a name="see-also"></a>Vea también  
 [Fundamentos de la depuración: ventana Registros](../debugger/debugging-basics-registers-window.md)   
 [Ver los datos en el depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Fundamentos de la depuración: ventana Registros](../debugger/debugging-basics-registers-window.md)