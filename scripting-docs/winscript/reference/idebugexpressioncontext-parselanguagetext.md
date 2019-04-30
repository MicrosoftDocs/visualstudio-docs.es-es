---
title: IDebugExpressionContext::ParseLanguageText | Microsoft Docs
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
ms.openlocfilehash: 50f9f398b9193c776f8e2a823b78ce7b8da438b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946282"
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
 [in] Proporciona el texto de la expresión o instrucción o instrucciones.  
  
 `nRadix`  
 [in] Base a utilizar.  
  
 `pstrDelimiter`  
 [in] El delimitador final del bloque de script. Cuando `pstrCode` se analiza desde una secuencia de texto, el host normalmente utiliza un delimitador, como dos comillas ("), para detectar el final del bloque de script. Este parámetro especifica el delimitador que utiliza el host, lo que permite el motor de scripting proporcione algún preprocesamiento primitivo condicional (por ejemplo, que reemplaza una comilla sencilla ['] con dos comillas simples para su uso como un delimitador). Exactamente cómo (y si) utiliza el motor de scripting, esta información depende del motor de scripting. Establezca este parámetro en `NULL` si el host no utilizó un delimitador para marcar el final del bloque de script.  
  
 `dwFlags`  
 [in] Combinación de los siguientes marcadores de texto de depuración:  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Indica que el texto es una expresión en lugar de una instrucción. Este indicador puede afectar a la manera en que se analiza el texto por algunos idiomas.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Si un valor devuelto está disponible, se utilizará el llamador.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|No se permiten efectos secundarios. Si se establece esta marca, la evaluación de la expresión no debe cambiar ningún estado en tiempo de ejecución.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Permite que los puntos de interrupción durante la evaluación del texto. Si no se establece esta marca se omiten los puntos de interrupción durante la evaluación del texto.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Permite que los informes de error durante la evaluación del texto. Si no se establece esta marca, a continuación, no se notifican al host durante la evaluación.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Indica la expresión se evaluará un contexto de código, en lugar de ejecutar la expresión|  
  
 `ppe`  
 [out] Devuelve la expresión de depuración para el texto especificado.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método crea una expresión de depuración para el texto especificado.  
  
## <a name="see-also"></a>Vea también  
 [IDebugExpressionContext (Interfaz)](../../winscript/reference/idebugexpressioncontext-interface.md)