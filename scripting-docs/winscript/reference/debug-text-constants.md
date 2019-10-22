---
title: Constantes de DEBUG_TEXT | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: facbdc1258b3fca72a239d9d5cc41772cf577f13
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577367"
---
# <a name="debug_text-constants"></a>Constantes DEBUG_TEXT
Se utiliza durante [idebugexpressioncontext (::P arselanguagetext](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>Constantes  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|Indica que el texto es una expresión en lugar de una instrucción. Esta marca puede afectar a la manera en que algunos lenguajes analizan el texto.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Si hay un valor devuelto disponible, el autor de la llamada lo utilizará.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|No permita efectos secundarios. Si se establece esta marca, la evaluación de la expresión no debe cambiar el estado de tiempo de ejecución.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Permitir puntos de interrupción durante la evaluación del texto. Si no se establece esta marca, se omitirán los puntos de interrupción durante la evaluación del texto.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Permite los informes de errores durante la evaluación del texto. Si no se establece esta marca, no se informará de los errores en el host durante la evaluación.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Indica que la expresión se va a evaluar en un contexto de código en lugar de ejecutar la propia expresión.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)