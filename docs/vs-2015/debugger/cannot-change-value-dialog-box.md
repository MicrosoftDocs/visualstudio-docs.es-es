---
title: No se puede cambiar el cuadro de diálogo valor | Documentos de Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a464be8e52a96da027e26ae48c5efb73ca2b5bf3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567558"
---
# <a name="cannot-change-value-dialog-box"></a>No se puede cambiar el valor (cuadro de diálogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [no cuadro de diálogo de cambio de valor](https://docs.microsoft.com/visualstudio/debugger/cannot-change-value-dialog-box).  
  
Error  
 `The value of this variable cannot be changed` &#124;`The name` *nombre* `does not exist in the current context` &#124; *otros mensajes*  
  
 Este cuadro de mensaje aparece al intentar cambiar el contenido de una variable a un valor no válido en una ventana del depurador (ventanas Automático, Inspección o Variables locales) o en el cuadro de diálogo Inspección rápida. Por ejemplo, este cuadro de mensaje aparece si intenta establecer el valor de una variable entera a una cadena de caracteres.  
  
## <a name="solution"></a>Soluciones  
 Asegúrese de que el valor de entrada que escribe en la ventana del depurador o en el cuadro de diálogo Inspección rápida representa un valor válido para la variable que está intentando establecer.  
  
## <a name="see-also"></a>Vea también  
 [Expresiones en el depurador](../debugger/expressions-in-the-debugger.md)



