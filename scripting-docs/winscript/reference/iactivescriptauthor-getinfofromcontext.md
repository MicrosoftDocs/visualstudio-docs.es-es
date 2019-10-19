---
title: 'Iactivescriptauthor (:: GetInfoFromContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetInfoFromContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetInfoFromContext
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 457b2ad1bda3226caf3604e3ccd6b976f01bca83
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576213"
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
Devuelve la información de tipo y las posiciones de delimitador de un carácter determinado en un bloque de código. Esto proporciona información para IntelliSense de miembros, listas globales y sugerencias de parámetros.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszCode`  
 de Dirección de la cadena de bloque de código utilizada para generar los resultados de la información.  
  
 `cchCode`  
 de Longitud del bloque de código.  
  
 `ichCurrentPosition`  
 de Posición del carácter relativa al inicio del bloque.  
  
 `dwListTypesRequested`  
 de Tipos de lista solicitados. Puede ser una combinación de los siguientes valores:  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|Ninguna lista.|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|Lista de miembros.|  
|SCRIPT_CMPL_ENUMLIST|0x0002|Lista de enumeración.|  
|SCRIPT_CMPL_PARAMLIST|0x0004|Lista de parámetros del método de llamada.|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|Lista global.|  
  
 El tipo SCRIPT_CMPL_GLOBALLIST se trata como un elemento de finalización predeterminado que se puede combinar mediante el operador OR con otros elementos de finalización. El motor de creación de script intenta primero rellenar la información de tipo para otros elementos de lista de finalización. Si se produce un error, el motor se rellena para SCRIPT_CMPL_GLOBALLIST.  
  
 `pdwListTypesProvided`  
 enuncia Tipo de lista proporcionado.  
  
 `pichListAnchorPosition`  
 enuncia Índice inicial del contexto que contiene la posición actual. El índice inicial es relativo al inicio del bloque.  
  
 Solo se rellena cuando `dwListTypesRequested` incluye SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST o SCRIPT_CMPL_GLOBALLIST. Para otros tipos de lista solicitados, el resultado es indefinido.  
  
 `pichFuncAnchorPosition`  
 enuncia Índice inicial de la llamada de función que contiene la posición actual. El índice inicial es relativo al inicio del bloque.  
  
 Solo se rellena cuando el contexto que contiene la posición actual es una llamada de función y cuando `dwListTypesRequested` incluye SCRIPT_CMPL_PARAMLIST. De lo contrario, el resultado es indefinido.  
  
 `pmemid`  
 enuncia MEMBERID de la función, tal y como lo define un tipo en el parámetro de salida `IProvideMultipleClassInfo``ppunk`.  
  
 Solo se rellena cuando `dwListTypesRequested` incluye SCRIPT_CMPL_PARAMLIST.  
  
 `piCurrentParameter`  
 enuncia Índice del parámetro que contiene la posición actual. Si la posición actual está en el nombre de la función, se devuelve-1.  
  
 El valor `piCurrentParameter` se rellena solo cuando `dwListTypesRequested` incluye SCRIPT_CMPL_PARAMLIST.  
  
 `ppunk`  
 La información de tipo, que se proporciona en forma de un objeto `IProvideMultipleClassInfo`.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz IProvideMultipleClassInfo](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo)  
 [IActiveScriptAuthor (Interfaz)](../../winscript/reference/iactivescriptauthor-interface.md)