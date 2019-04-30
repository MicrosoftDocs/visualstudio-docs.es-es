---
title: No se puede cambiar el cuadro de diálogo valor | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f8f9dafe8ada8914591426dea9abc867de2236f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564156"
---
# <a name="cannot-change-value-dialog-box"></a>No se puede cambiar el valor (cuadro de diálogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Error  
 `The value of this variable cannot be changed` &#124;`The name` *nombre* `does not exist in the current context` &#124; *otros mensajes*  
  
 Este cuadro de mensaje aparece al intentar cambiar el contenido de una variable a un valor no válido en una ventana del depurador (ventanas Automático, Inspección o Variables locales) o en el cuadro de diálogo Inspección rápida. Por ejemplo, este cuadro de mensaje aparece si intenta establecer el valor de una variable entera a una cadena de caracteres.  
  
## <a name="solution"></a>Soluciones  
 Asegúrese de que el valor de entrada que escribe en la ventana del depurador o en el cuadro de diálogo Inspección rápida representa un valor válido para la variable que está intentando establecer.  
  
## <a name="see-also"></a>Vea también  
 [Expresiones en el depurador](../debugger/expressions-in-the-debugger.md)
