---
title: IActiveScriptParseProcedure32::P arseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ede37171-2f1e-4467-a358-17bd4a4f1869
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 52333d13731b5c31329ee812be403c09cf43d63b
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835737"
---
# <a name="iactivescriptparseprocedure32parseproceduretext"></a>IActiveScriptParseProcedure32::ParseProcedureText
Analiza el procedimiento de código dado y agrega el procedimiento al espacio de nombres.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
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
 de Dirección del texto del procedimiento que se va a evaluar. La interpretación de esta cadena depende del lenguaje de scripting.  
  
 `pstrFormalParams`  
 de Dirección de los nombres de parámetros formales para el procedimiento. Los nombres de los parámetros deben estar separados por los delimitadores adecuados para el motor de scripting. Los nombres no se deben incluir entre paréntesis.  
  
 `pstrProcedureName`  
 de Dirección del nombre del procedimiento que se va a analizar.  
  
 `pstrItemName`  
 de Dirección del nombre de elemento que proporciona el contexto en el que se va a evaluar el procedimiento. Si este parámetro es `NULL` , el código se evalúa en el contexto global del motor de scripting.  
  
 `punkContext`  
 de Dirección del objeto de contexto. Este objeto se reserva para su uso en un entorno de depuración, donde el depurador puede proporcionar un contexto de este tipo para representar un contexto de tiempo de ejecución activo. Si este parámetro es `NULL` , el motor utiliza `pstrItemName` para identificar el contexto.  
  
 `pstrDelimiter`  
 de Dirección del delimitador de fin de procedimiento. Cuando `pstrCode` se analiza desde un flujo de texto, el host normalmente usa un delimitador, como dos comillas simples (' '), para detectar el final del procedimiento. Este parámetro especifica el delimitador utilizado por el host, lo que permite que el motor de scripting proporcione algún preprocesamiento primitivo condicional (por ejemplo, reemplazando una comilla simple ['] con dos comillas simples para su uso como delimitador). Exactamente cómo (y si) el motor de scripting hace uso de esta información depende del motor de scripting. Establezca este parámetro en `NULL` si el host no ha utilizado un delimitador para marcar el final del procedimiento.  
  
 `dwSourceContextCookie`  
 de Valor definido por la aplicación que se usa para la depuración.  
  
 `ulStartingLineNumber`  
 de Valor basado en cero que especifica en qué línea comenzará el análisis.  
  
 `dwFlags`  
 de Marcas asociadas al procedimiento. Puede ser una combinación de estos valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Indica que el código de `pstrCode` es una expresión que representa el valor devuelto del procedimiento. De forma predeterminada, el código puede contener una expresión, una lista de instrucciones o cualquier otro elemento que el lenguaje de script permita en un procedimiento.|  
|SCRIPTPROC_IMPLICIT_THIS|Indica que el `this` puntero está incluido en el ámbito del procedimiento.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Indica que los elementos primarios del `this` puntero se incluyen en el ámbito del procedimiento.|  
  
 `ppdisp`  
 enuncia Dirección del puntero para el objeto que contiene los métodos y propiedades globales del script. Si el motor de scripting no admite este tipo de objeto, `NULL` se devuelve.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se ha especificado un puntero no válido.|  
|`E_NOTIMPL`|Este método no se admite. El motor de scripting no admite la adición de procedimientos en tiempo de ejecución al espacio de nombres.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting está en estado no inicializado o cerrado).|  
|`OLESCRIPT_E_SYNTAX`|Se produjo un error de sintaxis no especificado en el procedimiento.|  
|`S_FALSE`|El motor de scripting no admite un objeto Dispatch; el `ppdisp` parámetro se establece en `NULL` .|  
  
## <a name="remarks"></a>Comentarios  
 No se evalúa ningún código de script durante esta llamada; en su lugar, el procedimiento se compila en el estado del script, donde el script puede llamarlo más adelante.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptParseProcedure32](../../winscript/reference/iactivescriptparseprocedure32.md)