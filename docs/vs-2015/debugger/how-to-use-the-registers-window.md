---
title: Procedimiento Utilice la ventana registros | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.registers
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
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f622440c5bd0f0d09967eff56479459a4a3bfbb0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60042880"
---
# <a name="how-to-use-the-registers-window"></a>Procedimiento Utilice la ventana registros
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La ventana registros sólo está disponible si la depuración de nivel de dirección está habilitada en el **opciones** cuadro de diálogo, **depuración** nodo, **General** categoría.  
  
 El **registra** ventana muestra el contenido del registro. Si mantiene el **registra** ventana abierta al ir avanzando por el programa, puede ver cómo cambian los valores de registro mientras se ejecuta el código. Los valores que han cambiado recientemente se muestran en rojo. Se pueden modificar los valores de los registros. Para obtener más información, vea [Cómo: Editar un valor del registro](../debugger/how-to-edit-a-register-value.md).  
  
 Por motivos de claridad, la ventana **Registros** organiza los registros en grupos que varían según la plataforma y el tipo de procesador. Puede mostrar u ocultar grupos como desee. Para obtener más información, vea [Cómo: Mostrar y ocultar grupos de registros](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Para obtener una introducción de alto nivel conceptos relacionados con los registros y la ventana registros, vea [Fundamentos de depuración: Ventana registros](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-registers-window"></a>Para mostrar la ventana Registros  
  
- En el **depurar** menú, elija **Windows**y, a continuación, elija **registra**.  
  
     El depurador debe encontrarse en modo de interrupción.  
  
    > [!NOTE]
    >  La información de los registros no está disponible para las aplicaciones de script o SQL.  
  
## <a name="see-also"></a>Vea también  
 [Fundamentos de la depuración: Ventana registros](../debugger/debugging-basics-registers-window.md)   
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Fundamentos de la depuración: Ventana Registros](../debugger/debugging-basics-registers-window.md)
