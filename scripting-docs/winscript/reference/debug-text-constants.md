---
title: Constantes DEBUG_TEXT | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5126a9efefaab611cd27d2104c40918f8dc7c7e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641065"
---
# <a name="debugtext-constants"></a>Constantes DEBUG_TEXT
Usa durante la [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>Constantes  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|Indica que el texto es una expresión en lugar de una instrucción. Este indicador puede afectar a la manera en la que se analiza el texto de algunos lenguajes.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Si un valor devuelto está disponible, se utilizará por el llamador.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|No admite efectos secundarios. Si se establece esta marca, la evaluación de la expresión no debe cambiar ningún estado en tiempo de ejecución.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Permitir que los puntos de interrupción durante la evaluación del texto. Si no se establece esta marca, los puntos de interrupción se omitirá durante la evaluación del texto.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Permitir informes de errores durante la evaluación del texto. Si no se establece esta marca, a continuación, errores no notificará al host durante la evaluación.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Indica que la expresión se evalúa a un contexto de código, en lugar de ejecutar la propia expresión.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)