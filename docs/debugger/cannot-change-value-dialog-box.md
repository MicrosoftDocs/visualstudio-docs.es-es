---
title: No se puede cambiar el cuadro de diálogo valor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f8f9dafe8ada8914591426dea9abc867de2236f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628278"
---
# <a name="cannot-change-value-dialog-box"></a>No se puede cambiar el valor (cuadro de diálogo)
## <a name="error"></a>Error
 `The value of this variable cannot be changed` &#124;`The name` *nombre* `does not exist in the current context` &#124; *otros mensajes*

 Este cuadro de mensaje aparece al intentar cambiar el contenido de una variable a un valor no válido en una ventana del depurador (ventanas Automático, Inspección o Variables locales) o en el cuadro de diálogo Inspección rápida. Por ejemplo, este cuadro de mensaje aparece si intenta establecer el valor de una variable entera a una cadena de caracteres.

## <a name="solution"></a>Soluciones
 Asegúrese de que el valor de entrada que escribe en la ventana del depurador o en el cuadro de diálogo Inspección rápida representa un valor válido para la variable que está intentando establecer.

## <a name="see-also"></a>Vea también

- [Expresiones en el depurador](../debugger/expressions-in-the-debugger.md)