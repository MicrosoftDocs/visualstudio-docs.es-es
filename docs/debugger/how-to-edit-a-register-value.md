---
title: Procedimiento para editar un valor del registro | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f7a341fa3f8d41bf4788db5bb4b4957fd8cca81
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349827"
---
# <a name="how-to-edit-a-register-value-c-c-visual-basic-f"></a>Procedimiento Edición de un valor del registro (C#, C++, Visual Basic, F#)

La ventana Registros solo está disponible si está habilitada la depuración de nivel de dirección en el cuadro de diálogo **Opciones**, nodo **Depuración**.

### <a name="to-change-the-value-of-a-register"></a>Para cambiar el valor de un registro

1. En la ventana **Registros**, utilice la tecla TAB o el mouse para mover el punto de inserción hasta el valor que desee cambiar. Cuando empiece a escribir, el cursor deberá estar situado delante del valor que desea sobrescribir.

2. Escriba el nuevo valor.

    > [!CAUTION]
    > La modificación de los valores de registro (especialmente en los registros EIP y EBP) puede afectar a la ejecución del programa.

    > [!CAUTION]
    > La modificación de valores de punto flotante puede dar lugar a ligeras imprecisiones debido a la conversión de decimal a binario de los componentes fraccionarios. Incluso una operación de edición aparentemente inocua puede causar cambios en alguno de los bits menos significativos de un registro de punto flotante.

## <a name="see-also"></a>Vea también
- [Cómo: Uso de la ventana Registros](../debugger/how-to-use-the-registers-window.md)