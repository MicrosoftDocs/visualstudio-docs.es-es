---
title: No se puede cambiar el cuadro de diálogo valor | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40bcc1eb26ded43f092d89e62cd6f74b2f4dda73
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="cannot-change-value-dialog-box"></a>No se puede cambiar el valor (cuadro de diálogo)
## <a name="error"></a>Error  
 `The value of this variable cannot be changed` &#124;`The name` *nombre* `does not exist in the current context` &#124; *otros mensajes*  
  
 Este cuadro de mensaje aparece al intentar cambiar el contenido de una variable a un valor no válido en una ventana del depurador (ventanas Automático, Inspección o Variables locales) o en el cuadro de diálogo Inspección rápida. Por ejemplo, este cuadro de mensaje aparece si intenta establecer el valor de una variable entera a una cadena de caracteres.  
  
## <a name="solution"></a>Soluciones  
 Asegúrese de que el valor de entrada que escribe en la ventana del depurador o en el cuadro de diálogo Inspección rápida representa un valor válido para la variable que está intentando establecer.  
  
## <a name="see-also"></a>Vea también  
 [Expresiones en el depurador](../debugger/expressions-in-the-debugger.md)