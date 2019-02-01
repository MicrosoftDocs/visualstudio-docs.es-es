---
title: 'Cómo: utilizar la ventana registros | Microsoft Docs'
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
manager: ghogen
ms.openlocfilehash: 6856b2e10c43f33e22711353d33f732779e8f4af
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748120"
---
# <a name="how-to-use-the-registers-window"></a>Cómo: Utilizar la ventana Registros
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La ventana registros sólo está disponible si la depuración de nivel de dirección está habilitada en el **opciones** cuadro de diálogo, **depuración** nodo, **General** categoría.  
  
 El **registra** ventana muestra el contenido del registro. Si mantiene el **registra** ventana abierta al ir avanzando por el programa, puede ver cómo cambian los valores de registro mientras se ejecuta el código. Los valores que han cambiado recientemente se muestran en rojo. Se pueden modificar los valores de los registros. Para obtener más información, consulte [Cómo: editar el valor de un registro](../debugger/how-to-edit-a-register-value.md).  
  
 Para reducir el desorden, el **registra** ventana registros organiza en grupos, que pueden variar según la plataforma y el procesador de tipo. Puede mostrar u ocultar grupos como desee. Para obtener más información, consulte [Cómo: mostrar y ocultar grupos de registros](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Para obtener una introducción de alto nivel conceptos relacionados con los registros y la ventana registros, vea [Fundamentos de depuración: ventana registros](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-registers-window"></a>Para mostrar la ventana Registros  
  
-   En el **depurar** menú, elija **Windows**y, a continuación, elija **registra**.  
  
     El depurador debe encontrarse en modo de interrupción.  
  
    > [!NOTE]
    >  La información de los registros no está disponible para las aplicaciones de script o SQL.  
  
## <a name="see-also"></a>Vea también  
 [Fundamentos de la depuración: ventana Registros](../debugger/debugging-basics-registers-window.md)   
 [Visualización de datos en el depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Fundamentos de la depuración: ventana Registros](../debugger/debugging-basics-registers-window.md)





