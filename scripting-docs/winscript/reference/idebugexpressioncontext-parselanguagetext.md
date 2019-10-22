---
title: Idebugexpressioncontext (::P arseLanguageText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionContext.ParseLanguageText
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext::ParseLanguageText
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0493adde76e029088b637be3c6aaf02c55caaace
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573157"
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
Crea una expresión de depuración para el texto especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstrCode`  
 de Proporciona el texto de la expresión o instrucciones.  
  
 `nRadix`  
 de Base que se va a usar.  
  
 `pstrDelimiter`  
 de El delimitador de bloque de script. Cuando `pstrCode` se analiza desde un flujo de texto, el host normalmente usa un delimitador, como dos comillas simples (' '), para detectar el final del bloque de script. Este parámetro especifica el delimitador utilizado por el host, lo que permite que el motor de scripting proporcione algún preprocesamiento primitivo condicional (por ejemplo, reemplazando una comilla simple ['] con dos comillas simples para su uso como delimitador). Exactamente cómo (y si) el motor de scripting utiliza esta información depende del motor de scripting. Establezca este parámetro en `NULL` si el host no usó un delimitador para marcar el final del bloque de script.  
  
 `dwFlags`  
 de Combinación de las siguientes marcas de texto de depuración:  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Indica que el texto es una expresión en lugar de una instrucción. Esta marca puede afectar a la manera en que algunos lenguajes analizan el texto.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Si hay un valor devuelto disponible, el autor de la llamada lo utilizará.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|No permitir efectos secundarios. Si se establece esta marca, la evaluación de la expresión no debe cambiar el estado de tiempo de ejecución.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Permite puntos de interrupción durante la evaluación del texto. Si no se establece esta marca, los puntos de interrupción se omiten durante la evaluación del texto.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Permite informes de errores durante la evaluación del texto. Si no se establece esta marca, los errores no se envían al host durante la evaluación.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Indica que la expresión se va a evaluar en un contexto de código en lugar de ejecutar la propia expresión|  
  
 `ppe`  
 enuncia Devuelve la expresión de depuración para el texto especificado.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método crea una expresión de depuración para el texto especificado.  
  
## <a name="see-also"></a>Vea también  
 [IDebugExpressionContext (Interfaz)](../../winscript/reference/idebugexpressioncontext-interface.md)