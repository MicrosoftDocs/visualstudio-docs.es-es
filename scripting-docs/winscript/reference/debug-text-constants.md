---
title: DEBUG_TEXT (constantes) | Microsoft Docs
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
ms.openlocfilehash: 2342555c4ee92b403aa01cc0ca15bb805f2b002e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152803"
---
# <a name="debugtext-constants"></a>Constantes DEBUG_TEXT
Utilizado durante [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>Constantes  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|Indica que el texto es una expresión en lugar de una instrucción. Este indicador puede afectar a la manera en que se analiza el texto por algunos idiomas.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Si un valor devuelto está disponible, se utilizará el llamador.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|No se permiten efectos secundarios. Si se establece esta marca, la evaluación de la expresión no debe cambiar ningún estado en tiempo de ejecución.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Permitir que los puntos de interrupción durante la evaluación del texto. Si no se establece esta marca, los puntos de interrupción se omitirá durante la evaluación del texto.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Permitir informes de errores durante la evaluación del texto. Si no se establece esta marca, a continuación, los errores no se notificarán al host durante la evaluación.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Indica que la expresión se evalúa a un contexto de código, en lugar de ejecutar la propia expresión.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)