---
title: Filtrar Editar un valor del registro | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7566d3a89ff27cc473b9352c7e0f02492dc736d1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999046"
---
# <a name="how-to-edit-a-register-value"></a>Filtrar Editar un valor del registro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La ventana Registros solo está disponible si está habilitada la depuración de nivel de dirección en el cuadro de diálogo **Opciones**, nodo **Depuración**.  
  
### <a name="to-change-the-value-of-a-register"></a>Para cambiar el valor de un registro  
  
1.  En la ventana **Registros**, utilice la tecla TAB o el mouse para mover el punto de inserción hasta el valor que desee cambiar. Cuando empiece a escribir, el cursor deberá estar situado delante del valor que desea sobrescribir.  
  
2.  Escriba el nuevo valor.  
  
    > [!CAUTION]
    >  La modificación de los valores de registro (especialmente en los registros EIP y EBP) puede afectar a la ejecución del programa.  
  
    > [!CAUTION]
    >  La modificación de valores de punto flotante puede dar lugar a ligeras imprecisiones debido a la conversión de decimal a binario de los componentes fraccionarios. Incluso una operación de edición aparentemente inocua puede causar cambios en alguno de los bits menos significativos de un registro de punto flotante.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Uso de la ventana Registros](../debugger/how-to-use-the-registers-window.md)
