---
title: 'Cómo: editar un valor del registro | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.register.edit
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
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 465ecd4e8003b82a0a7dfbab33004ef2b80d7f32
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577905"
---
# <a name="how-to-edit-a-register-value"></a>Cómo: Editar un valor de registro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: editar el valor de un registro](https://docs.microsoft.com/visualstudio/debugger/how-to-edit-a-register-value).  
  
La ventana registros sólo está disponible si la depuración de nivel de dirección está habilitada en el **opciones** cuadro de diálogo, **depuración** nodo.  
  
### <a name="to-change-the-value-of-a-register"></a>Para cambiar el valor de un registro  
  
1.  En el **registra** ventana, utilice la tecla TAB o el mouse para mover la inserción del punto en el valor que desee cambiar. Cuando empiece a escribir, el cursor deberá estar situado delante del valor que desea sobrescribir.  
  
2.  Escriba el nuevo valor.  
  
    > [!CAUTION]
    >  La modificación de los valores de registro (especialmente en los registros EIP y EBP) puede afectar a la ejecución del programa.  
  
    > [!CAUTION]
    >  La modificación de valores de punto flotante puede dar lugar a ligeras imprecisiones debido a la conversión de decimal a binario de los componentes fraccionarios. Incluso una operación de edición aparentemente inocua puede causar cambios en alguno de los bits menos significativos de un registro de punto flotante.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Usar la ventana Registros](../debugger/how-to-use-the-registers-window.md)





