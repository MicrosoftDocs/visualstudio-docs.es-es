---
title: IActiveScriptAuthorProcedure::ParseProcedureText | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthorProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthorProcedure::ParseProcedureText
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 893dc36c066426ad1de7346c7ce1fea24b191ba3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090693"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Analiza un procedimiento de código, agrega texto del procedimiento de código para el motor de creación de script y crea un `IScriptEntry` objeto que se corresponde con el procedimiento de código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszCode`  
 [in] Para analizar el texto del script.  
  
 `pszFormalParams`  
 [in] La dirección de los nombres de parámetro formal para el procedimiento. Los nombres de parámetro deben estar separados por los delimitadores apropiados para el motor de creación de script. Los nombres no deben incluirse entre paréntesis.  
  
 `pszProcedureName`  
 [in] La dirección del nombre del procedimiento que se va a analizar.  
  
 `pszItemName`  
 [in] La dirección de búfer que contiene el nombre del elemento asociado con el `IScriptEntry` objeto.  
  
 `pszDelimiter`  
 [in] La dirección del delimitador final del bloque de script. Cuando `pszCode` se analiza desde una secuencia de texto, el host normalmente utiliza un delimitador (por ejemplo, dos comillas simples), para detectar el final del bloque de script. Establezca este parámetro en NULL si no hay ningún delimitador para marcar el final del bloque de script.  
  
 `dwCookie`  
 [in] Un valor definido por la aplicación que está asociado con el nuevo `IScriptEntry` objeto.  
  
 `dwFlags`  
 [in] No se utiliza.  
  
 `pdispFor`  
 [in] No se utiliza.  
  
## <a name="return-value"></a>Valor devuelto  
 Una clase `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Actual [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor no implementa este método.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptAuthorProcedure (Interfaz)](../../winscript/reference/iactivescriptauthorprocedure-interface.md)