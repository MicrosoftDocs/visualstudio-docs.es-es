---
title: "Cómo: editar un valor de registro | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.register.edit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b9cc839b7829070f5d4c2e9db9da12b6522c21eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-edit-a-register-value"></a>Cómo: Editar un valor de registro
La ventana registros solo está disponible si está habilitada la depuración de nivel de dirección en la **opciones** cuadro de diálogo, **depuración** nodo.  
  
### <a name="to-change-the-value-of-a-register"></a>Para cambiar el valor de un registro  
  
1.  En el **registra** ventana, utilice la tecla TAB o el mouse para mover la inserción del punto en el valor que desea cambiar. Cuando empiece a escribir, el cursor deberá estar situado delante del valor que desea sobrescribir.  
  
2.  Escriba el nuevo valor.  
  
    > [!CAUTION]
    >  La modificación de los valores de registro (especialmente en los registros EIP y EBP) puede afectar a la ejecución del programa.  
  
    > [!CAUTION]
    >  La modificación de valores de punto flotante puede dar lugar a ligeras imprecisiones debido a la conversión de decimal a binario de los componentes fraccionarios. Incluso una operación de edición aparentemente inocua puede causar cambios en alguno de los bits menos significativos de un registro de punto flotante.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Usar la ventana Registros](../debugger/how-to-use-the-registers-window.md)