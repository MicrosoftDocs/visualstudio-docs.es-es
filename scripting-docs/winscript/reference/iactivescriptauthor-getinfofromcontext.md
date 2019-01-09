---
title: IActiveScriptAuthor::GetInfoFromContext | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 2d32e2864f42fa9a2bfc30cfe83da7d4e021dfd0
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088873"
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
Devuelve escriba información y las posiciones de delimitador para un carácter dado en un bloque de código. Esto proporciona información de miembro, IntelliSense, listas globales y sugerencias sobre parámetros.  
  
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
 [in] La dirección de la cadena de bloques de código utilizada para generar los resultados de la información.  
  
 `cchCode`  
 [in] La longitud del bloque de código.  
  
 `ichCurrentPosition`  
 [in] La posición del carácter en relación con el inicio del bloque.  
  
 `dwListTypesRequested`  
 [in] Los tipos de lista solicitados. Puede ser una combinación de los siguientes valores:  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|Ninguna lista.|  
|SCRIPT_CMPL_MEMBERLIST|0 x 0001|Lista de miembros.|  
|SCRIPT_CMPL_ENUMLIST|0x0002|Lista de enumeración.|  
|SCRIPT_CMPL_PARAMLIST|0x0004|Llame a la lista de parámetros de método.|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|Lista global.|  
  
 El tipo SCRIPT_CMPL_GLOBALLIST se trata como un elemento de finalización predeterminada que se puede combinar mediante el operador OR con otros elementos de finalización. El script de motor de creación en primer lugar intenta rellenar la información de tipo para otros elementos de la lista de finalización. Si se produce un error, el motor se rellena para SCRIPT_CMPL_GLOBALLIST.  
  
 `pdwListTypesProvided`  
 [out] El tipo de la lista proporcionada.  
  
 `pichListAnchorPosition`  
 [out] Índice inicial del contexto que contiene la posición actual. El índice inicial es relativo al inicio del bloque.  
  
 Este campo se rellena únicamente cuando `dwListTypesRequested` incluye SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST o SCRIPT_CMPL_GLOBALLIST. Para otros tipos de lista solicitado, el resultado es indefinido.  
  
 `pichFuncAnchorPosition`  
 [out] Índice inicial de la llamada de función que contiene la posición actual. El índice inicial es relativo al inicio del bloque.  
  
 Este campo se rellena únicamente cuando el contexto que contiene la posición actual es una llamada de función y cuando `dwListTypesRequested` incluye SCRIPT_CMPL_PARAMLIST. En caso contrario, el resultado es indefinido.  
  
 `pmemid`  
 [out] MEMBERID de la función, tal como se define por un tipo en el `IProvideMultipleClassInfo``ppunk` parámetro out.  
  
 Este campo se rellena únicamente cuando `dwListTypesRequested` incluye SCRIPT_CMPL_PARAMLIST.  
  
 `piCurrentParameter`  
 [out] El índice del parámetro que contiene la posición actual. Si la posición actual está en el nombre de función, se devuelve -1.  
  
 El `piCurrentParameter` valor se rellena únicamente cuando `dwListTypesRequested` incluye SCRIPT_CMPL_PARAMLIST.  
  
 `ppunk`  
 La información de tipo que se proporciona en forma de un `IProvideMultipleClassInfo` objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 Una clase `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Interfaz IProvideMultipleClassInfo](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo)   
 [IActiveScriptAuthor (Interfaz)](../../winscript/reference/iactivescriptauthor-interface.md)