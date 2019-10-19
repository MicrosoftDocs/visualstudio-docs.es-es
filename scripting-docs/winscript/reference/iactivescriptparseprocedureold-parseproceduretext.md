---
title: Iactivescriptparseprocedureold (::P arseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 116cbc7fac0d53b55c9766945d56ecebd27b6785
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577448"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Analiza el procedimiento de código dado y agrega un procedimiento anónimo al espacio de nombres.  
  
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
 de Texto del procedimiento que se va a evaluar. La interpretación de esta cadena depende del lenguaje de scripting.  
  
 `pstrFormalParams`  
 de Nombres de parámetros formales para el procedimiento. Los nombres de los parámetros deben estar separados por los delimitadores adecuados para el motor de scripting. Los nombres no se deben incluir entre paréntesis.  
  
 `pstrItemName`  
 de Nombre del elemento con nombre que proporciona el contexto en el que se va a evaluar el procedimiento. Si este parámetro es `NULL`, el código se evalúa en el contexto global del motor de scripting.  
  
 `punkContext`  
 de Objeto de contexto. Este objeto se reserva para su uso en un entorno de depuración, donde el depurador puede proporcionar un contexto de este tipo para representar un contexto de tiempo de ejecución activo. Si este parámetro se `NULL`, el motor utiliza `pstrItemName` para identificar el contexto.  
  
 `pstrDelimiter`  
 de Delimitador de fin de procedimiento. Cuando `pstrCode` se analiza desde un flujo de texto, el host normalmente usa un delimitador, como dos comillas simples (' '), para detectar el final del procedimiento. Este parámetro especifica el delimitador utilizado por el host, lo que permite que el motor de scripting proporcione algún preprocesamiento condicional y primitivo (por ejemplo, reemplazando una comilla simple ['] con dos comillas simples para su uso como delimitador). Exactamente cómo (y si) el motor de scripting utiliza esta información depende del motor de scripting. Establezca este parámetro en `NULL` si el host no usó un delimitador para marcar el final del procedimiento.  
  
 `dwSourceContextCookie`  
 de Valor definido por la aplicación que se usa para la depuración.  
  
 `ulStartingLineNumber`  
 de Valor basado en cero que especifica en qué línea comenzará el análisis.  
  
 `dwFlags`  
 de Marcas asociadas al procedimiento. Puede ser una combinación de estos valores.  
  
|Constante|Valor|Significado|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|Indica que el código de `pstrCode` es una expresión que representa el valor devuelto del procedimiento.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|Indica que el puntero `this` está incluido en el ámbito del procedimiento.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|Indica que los elementos primarios del puntero `this` están incluidos en el ámbito del procedimiento.|  
  
 `ppdisp`  
 enuncia Devuelve un contenedor de envío donde el método predeterminado es el procedimiento analizado por este método.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se ha especificado un puntero no válido.|  
|`E_NOTIMPL`|No se admite este método. El motor de scripting no admite la adición de procedimientos en tiempo de ejecución al espacio de nombres.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting está en estado no inicializado o cerrado).|  
|`OLESCRIPT_E_SYNTAX`|Se produjo un error de sintaxis no especificado en el procedimiento.|  
|`S_FALSE`|El motor de scripting no admite un objeto Dispatch; la `ppdisp`parameter se establece en `NULL`.|  
  
## <a name="remarks"></a>Comentarios  
 No se evalúa ningún código de script durante esta llamada; en su lugar, el procedimiento se compila en un método en `ppdisp` donde el script puede llamarlo más adelante.  
  
 Esta interfaz está en desuso en favor de la interfaz `IActiveScriptParseProcedure`. El método `IActiveScriptParseProcedure::ParseProcedureText` es similar a este método, pero permite especificar el nombre del procedimiento. En todas las circunstancias, se debe usar `IActiveScriptParseProcedure::ParseProcedureText`.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz iactivescriptparseprocedureold (](../../winscript/reference/iactivescriptparseprocedureold-interface.md)  
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)