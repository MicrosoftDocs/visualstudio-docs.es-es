---
title: 'Cómo: usar la ventana registros | Microsoft Docs'
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
ms.openlocfilehash: 233092af638824c462a6d9a47865a1c6f5fd9397
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697466"
---
# <a name="how-to-use-the-registers-window"></a>Cómo: Utilizar la ventana Registros
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La ventana Registros está disponible únicamente si la depuración del nivel de dirección está habilitada en el cuadro de diálogo **Opciones**, nodo **Depuración**, categoría **General**.  
  
 La ventana **registros** muestra el contenido del registro. Si mantiene abierta la ventana **registros** mientras se recorre el programa, puede ver los cambios de los valores de registro a medida que se ejecuta el código. Los valores que han cambiado recientemente se muestran en rojo. Se pueden modificar los valores de los registros. Para obtener más información, consulte [Cómo: editar un valor de registro](../debugger/how-to-edit-a-register-value.md).  
  
 Por motivos de claridad, la ventana **Registros** organiza los registros en grupos que varían según la plataforma y el tipo de procesador. Puede mostrar u ocultar grupos como desee. Para obtener más información, consulte [Cómo: mostrar y ocultar grupos de registros](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Para obtener una introducción de alto nivel a los conceptos relacionados con los registros y la ventana registros, vea fundamentos de la [depuración: ventana registros](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo de Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-registers-window"></a>Para mostrar la ventana Registros  
  
- En el menú **depurar** , elija **ventanas**y, a continuación, elija **registros**.  
  
     El depurador debe encontrarse en modo de interrupción.  
  
    > [!NOTE]
    > La información de los registros no está disponible para las aplicaciones de script o SQL.  
  
## <a name="see-also"></a>Consulte también  
 [Fundamentos de la depuración: ventana registros](../debugger/debugging-basics-registers-window.md)   
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Fundamentos de la depuración: ventana registros](../debugger/debugging-basics-registers-window.md)
