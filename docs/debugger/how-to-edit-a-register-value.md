---
title: 'Cómo: editar un valor del registro | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d0337f7c77d1ed601c7a6c13c702f4758cbfdbd
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257089"
---
# <a name="how-to-edit-a-register-value-c-c-visual-basic-f"></a>Cómo: editar un valor del registro (C#, C++, Visual Basic, F#)

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