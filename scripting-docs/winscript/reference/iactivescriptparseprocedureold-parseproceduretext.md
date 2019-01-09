---
title: IActiveScriptParseProcedureOld::ParseProcedureText | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld.ParseProcedureText
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld::ParseProcedureText
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec100214a43be6e1faf5e229ce6452432065002b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093397"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Analiza el procedimiento de código dado y agrega un procedimiento anónimo para el espacio de nombres.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstrCode`  
 [in] El texto del procedimiento para evaluar. La interpretación de esta cadena depende del lenguaje de scripting.  
  
 `pstrFormalParams`  
 [in] Nombres de parámetros formales para el procedimiento. Los nombres de parámetro deben estar separados con los delimitadores apropiados para el motor de scripting. Los nombres no se deben incluir entre paréntesis.  
  
 `pstrItemName`  
 [in] El nombre del elemento con nombre que proporciona el contexto en el que el procedimiento se va a evaluar. Si este parámetro es `NULL`, el código se evalúa en el contexto global del motor de scripting.  
  
 `punkContext`  
 [in] El objeto de contexto. Este objeto está reservado para su uso en un entorno de depuración, donde el depurador para representar un contexto de tiempo de ejecución activo puede proporcionar un contexto de este tipo. Si este parámetro es `NULL`, el motor utiliza `pstrItemName` para identificar el contexto.  
  
 `pstrDelimiter`  
 [in] El delimitador final del procedimiento. Cuando `pstrCode` se analiza desde una secuencia de texto, el host normalmente utiliza un delimitador, como dos comillas ("), para detectar el final del procedimiento. Este parámetro especifica el delimitador que utiliza el host, lo que permite proporcionar algunos condicional, el motor de scripting de preprocesamiento primitivo (por ejemplo, reemplazando una comilla sencilla ['] con dos comillas simples para su uso como un delimitador). Exactamente cómo (y si) utiliza el motor de scripting, esta información depende del motor de scripting. Establezca este parámetro en `NULL` si el host no utilizó un delimitador para marcar el final del procedimiento.  
  
 `dwSourceContextCookie`  
 [in] Valor definido por la aplicación que se usa con fines de depuración.  
  
 `ulStartingLineNumber`  
 [in] Valor de base cero que especifica en qué línea empezará el análisis.  
  
 `dwFlags`  
 [in] Marcas asociadas con el procedimiento. Puede ser una combinación de estos valores.  
  
|Constante|Valor|Significado|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|Indica que el código en `pstrCode` es una expresión que representa el valor devuelto del procedimiento.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|Indica que el `this` puntero se incluye en el ámbito del procedimiento.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|Indica que los elementos primarios de la `this` puntero se incluyen en el ámbito del procedimiento.|  
  
 `ppdisp`  
 [out] Devuelve un contenedor de envío donde el método predeterminado es el procedimiento que se puede analizado por este método.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
|`E_NOTIMPL`|No se admite este método. El motor de scripting no admite la adición de tiempo de ejecución de procedimientos para el espacio de nombres.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting está en el estado no inicializado o cerrado).|  
|`OLESCRIPT_E_SYNTAX`|Se produjo un error de sintaxis no especificado en el procedimiento.|  
|`S_FALSE`|El motor de scripting no admite un objeto de envío; el `ppdisp`parámetro está establecido en `NULL`.|  
  
## <a name="remarks"></a>Comentarios  
 No hay código de script se evalúa durante esta llamada; en su lugar, el procedimiento se compila en un método en `ppdisp` donde se puede llamar mediante el script más tarde.  
  
 Esta interfaz está en desuso en favor de la `IActiveScriptParseProcedure` interfaz. El `IActiveScriptParseProcedure::ParseProcedureText` método es similar a este método, pero permite especificar el nombre del procedimiento. En todas las circunstancias, `IActiveScriptParseProcedure::ParseProcedureText` debe usarse.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptParseProcedureOld (interfaz)](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)