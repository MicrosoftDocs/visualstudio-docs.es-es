---
title: IActiveScriptParseProcedure::ParseProcedureText | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptParseProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedure_ParseProcedureText
ms.assetid: 345a74ae-b4e8-42b2-abd8-633a370e8e7f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c2a877f6ebc692f9f54d69597e06db501f642802
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedureparseproceduretext"></a>IActiveScriptParseProcedure::ParseProcedureText
Analiza el procedimiento de código especificada y agrega el procedimiento para el espacio de nombres.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstrCode`  
 [in] Dirección del texto del procedimiento que se va a evaluar. La interpretación de esta cadena depende el lenguaje de scripting.  
  
 `pstrFormalParams`  
 [in] Dirección de los nombres de parámetro formal para el procedimiento. Los nombres de parámetro deben separarse con los delimitadores apropiados para el motor de scripting. Los nombres no deben incluirse entre paréntesis.  
  
 `pstrProcedureName`  
 [in] Dirección del nombre del procedimiento para analizarse.  
  
 `pstrItemName`  
 [in] Dirección del nombre del elemento que proporciona el contexto en el que se evaluará el procedimiento. Si este parámetro es `NULL`, el código se evalúa en el contexto global del motor de scripting.  
  
 `punkContext`  
 [in] Dirección del objeto de contexto. Este objeto está reservado para su uso en un entorno de depuración, donde el depurador para representar un contexto de tiempo de ejecución activo pueden proporcionar un contexto de este tipo. Si este parámetro es `NULL`, el motor utiliza `pstrItemName` para identificar el contexto.  
  
 `pstrDelimiter`  
 [in] Dirección del delimitador final del procedimiento. Cuando `pstrCode` se analiza desde una secuencia de texto, el host normalmente usa un delimitador, como dos comillas ("), para detectar el final del procedimiento simples. Este parámetro especifica el delimitador que utiliza el host, lo que el motor de scripting proporcionar algunos condicional preprocesamiento primitivos (por ejemplo, reemplace una comilla simple ['] con dos comillas simples para su uso como un delimitador). Exactamente cómo (y si) el scripting hace motor depende del uso de esta información en el motor de scripting. Establezca este parámetro en `NULL` si el host no usó un delimitador para marcar el final del procedimiento.  
  
 `dwSourceContextCookie`  
 [in] Valor definido por la aplicación que se usa para fines de depuración.  
  
 `ulStartingLineNumber`  
 [in] Valor basado en cero que especifica la línea que el análisis se iniciará en.  
  
 `dwFlags`  
 [in] Marcas asociadas con el procedimiento. Puede ser una combinación de estos valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Indica que el código en `pstrCode` es una expresión que representa el valor devuelto del procedimiento. De forma predeterminada, el código puede contener una expresión, una lista de instrucciones o cualquier persona permitido en un procedimiento por el lenguaje de script.|  
|SCRIPTPROC_IMPLICIT_THIS|Indica que el `this` puntero se incluye en el ámbito del procedimiento.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Indica que los elementos primarios de la `this` puntero se incluyen en el ámbito del procedimiento.|  
  
 `ppdisp`  
 [out] Dirección del puntero para el objeto que contiene los métodos globales y propiedades de la secuencia de comandos. Si el motor de scripting no admite este tipo de objeto, `NULL` se devuelve.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
|`E_NOTIMPL`|No se admite este método. El motor de scripting no admite la adición de tiempo de ejecución de procedimientos para el espacio de nombres.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting está en el estado sin inicializar o cerrado).|  
|`OLESCRIPT_E_SYNTAX`|Se produjo un error de sintaxis no especificado en el procedimiento.|  
|`S_FALSE`|El motor de scripting no es compatible con un objeto de envío; el `ppdisp` parámetro está establecido en `NULL`.|  
  
## <a name="remarks"></a>Comentarios  
 Ningún código de script se evalúa durante esta llamada; en su lugar, el procedimiento se compila en el estado de secuencia de comandos que se puede llamar mediante la secuencia de comandos más adelante.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)