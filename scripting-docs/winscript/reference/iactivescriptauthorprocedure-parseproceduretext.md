---
title: Iactivescriptauthorprocedure (::P arseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 11a34843f30274ec78f1652c5ed5cd4dbcf2884a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572819"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Analiza un procedimiento de código, agrega el texto del procedimiento de código al motor de creación de scripts y crea un objeto `IScriptEntry` que corresponde al procedimiento de código.  
  
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
 de Texto del script que se va a analizar.  
  
 `pszFormalParams`  
 de Dirección de los nombres de parámetros formales para el procedimiento. Los nombres de los parámetros deben estar separados por los delimitadores adecuados para el motor de creación de scripts. Los nombres no se deben incluir entre paréntesis.  
  
 `pszProcedureName`  
 de Dirección del nombre del procedimiento que se va a analizar.  
  
 `pszItemName`  
 de La dirección del búfer que contiene el nombre del elemento asociado al objeto de `IScriptEntry`.  
  
 `pszDelimiter`  
 de Dirección del delimitador de bloque de script final. Cuando `pszCode` se analiza desde un flujo de texto, el host normalmente usa un delimitador (como dos comillas simples) para detectar el final del bloque de script. Establezca este parámetro en NULL si no hay ningún delimitador para marcar el final del bloque de script.  
  
 `dwCookie`  
 de Un valor definido por la aplicación que está asociado al nuevo objeto `IScriptEntry`.  
  
 `dwFlags`  
 de No se usa.  
  
 `pdispFor`  
 de No se usa.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 El motor de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] actual no implementa este método.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptAuthorProcedure (Interfaz)](../../winscript/reference/iactivescriptauthorprocedure-interface.md)