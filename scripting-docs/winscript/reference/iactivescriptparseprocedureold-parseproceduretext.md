---
title: IActiveScriptParseProcedureOld::ParseProcedureText | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld.ParseProcedureText
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld::ParseProcedureText
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cab546deb390535fa8ff71e116a0ad42d33cc104
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Analiza el procedimiento de código especificada y se agrega un procedimiento anónimo para el espacio de nombres.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
 [in] El texto del procedimiento para evaluar. La interpretación de esta cadena depende el lenguaje de scripting.  
  
 `pstrFormalParams`  
 [in] Nombres de parámetros formales para el procedimiento. Los nombres de parámetro deben separarse con los delimitadores apropiados para el motor de scripting. Los nombres no deben incluirse entre paréntesis.  
  
 `pstrItemName`  
 [in] El nombre del elemento con nombre que proporciona el contexto en el que se evaluará el procedimiento. Si este parámetro es `NULL`, el código se evalúa en el contexto global del motor de scripting.  
  
 `punkContext`  
 [in] El objeto de contexto. Este objeto está reservado para su uso en un entorno de depuración, donde el depurador para representar un contexto de tiempo de ejecución activo pueden proporcionar un contexto de este tipo. Si este parámetro es `NULL`, el motor utiliza `pstrItemName` para identificar el contexto.  
  
 `pstrDelimiter`  
 [in] El delimitador final del procedimiento. Cuando `pstrCode` se analiza desde una secuencia de texto, el host normalmente usa un delimitador, como dos comillas ("), para detectar el final del procedimiento simples. Este parámetro especifica el delimitador que utiliza el host, lo que el motor de scripting proporcionar algunos condicional, preprocesamiento primitivos (por ejemplo, reemplazar una comilla simple ['] con dos comillas simples para su uso como un delimitador). Exactamente cómo (y si) los usos de motor de scripting en función de esta información en el motor de scripting. Establezca este parámetro en `NULL` si el host no usó un delimitador para marcar el final del procedimiento.  
  
 `dwSourceContextCookie`  
 [in] Valor definido por la aplicación que se usa para fines de depuración.  
  
 `ulStartingLineNumber`  
 [in] Valor basado en cero que especifica en qué línea se iniciará el análisis.  
  
 `dwFlags`  
 [in] Marcas asociadas con el procedimiento. Puede ser una combinación de estos valores.  
  
|Constante|Valor|Significado|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|Indica que el código en `pstrCode` es una expresión que representa el valor devuelto del procedimiento.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|Indica que el `this` puntero se incluye en el ámbito del procedimiento.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|Indica que los elementos primarios de la `this` puntero se incluyen en el ámbito del procedimiento.|  
  
 `ppdisp`  
 [out] Devuelve un contenedor de distribución donde el método predeterminado es el procedimiento analizado por este método.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
|`E_NOTIMPL`|No se admite este método. El motor de scripting no admite la adición de tiempo de ejecución de procedimientos para el espacio de nombres.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting está en el estado sin inicializar o cerrado).|  
|`OLESCRIPT_E_SYNTAX`|Se produjo un error de sintaxis no especificado en el procedimiento.|  
|`S_FALSE`|El motor de scripting no es compatible con un objeto de envío; el `ppdisp`parámetro está establecido en `NULL`.|  
  
## <a name="remarks"></a>Comentarios  
 Ningún código de script se evalúa durante esta llamada; en su lugar, el procedimiento se compila en un método en `ppdisp` donde se puede llamar mediante la secuencia de comandos más adelante.  
  
 Esta interfaz está en desuso en favor de la `IActiveScriptParseProcedure` interfaz. El `IActiveScriptParseProcedure::ParseProcedureText` método es similar a este método, pero sí permite especificar el nombre del procedimiento. En todas las circunstancias, `IActiveScriptParseProcedure::ParseProcedureText` debe utilizarse.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptParseProcedureOld (interfaz)](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)