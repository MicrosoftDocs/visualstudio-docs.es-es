---
title: IActiveScriptAuthor::GetInfoFromContext | Documentos de Microsoft
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
ms.openlocfilehash: 27c13dbe51bb1150554275b5fbeacd00be2e445f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645805"
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
Devuelve el tipo información y las posiciones de delimitación para un carácter determinado en un bloque de código. Esto proporciona información de miembro de IntelliSense, las listas globales y sugerencias sobre parámetros.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
 [in] La dirección de la cadena del bloque de código utilizada para generar los resultados de la información.  
  
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
|SCRIPT_CMPL_ENUMLIST|0 x 0002|Lista de enumeración.|  
|SCRIPT_CMPL_PARAMLIST|0 x 0004|Llame a la lista de parámetros de método.|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|Lista global.|  
  
 El tipo SCRIPT_CMPL_GLOBALLIST se trata como un elemento de finalización de manera predeterminada que se pueden combinar mediante el operador OR con otros elementos de la finalización. El script de creación motor primero intenta rellenar la información de tipos para otros elementos de la lista de finalización. Si se produce un error, el motor se rellena para SCRIPT_CMPL_GLOBALLIST.  
  
 `pdwListTypesProvided`  
 [out] El tipo de la lista proporcionada.  
  
 `pichListAnchorPosition`  
 [out] El índice de inicio del contexto que contiene la posición actual. El índice inicial es relativo al inicio del bloque.  
  
 Esto se rellenará solamente cuando `dwListTypesRequested` incluye SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST o SCRIPT_CMPL_GLOBALLIST. Para otros tipos de lista solicitada, el resultado es indefinido.  
  
 `pichFuncAnchorPosition`  
 [out] Índice inicial de la llamada de función que contiene la posición actual. El índice inicial es relativo al inicio del bloque.  
  
 Esto se rellena únicamente cuando el contexto que contiene la posición actual es una llamada de función y cuando `dwListTypesRequested` incluye SCRIPT_CMPL_PARAMLIST. En caso contrario, el resultado es indefinido.  
  
 `pmemid`  
 [out] MEMBERID de la función, tal como se define un tipo en el `IProvideMultipleClassInfo``ppunk` el parámetro de salida.  
  
 Esto se rellenará solamente cuando `dwListTypesRequested` incluye SCRIPT_CMPL_PARAMLIST.  
  
 `piCurrentParameter`  
 [out] El índice del parámetro que contiene la posición actual. Si la posición actual se encuentra en el nombre de función, se devuelve -1.  
  
 El `piCurrentParameter` valor se rellena únicamente cuando `dwListTypesRequested` incluye SCRIPT_CMPL_PARAMLIST.  
  
 `ppunk`  
 La información de tipo, que se proporciona en forma de una `IProvideMultipleClassInfo` objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Interfaz IProvideMultipleClassInfo](https://msdn.microsoft.com/library/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo.aspx)   
 [IActiveScriptAuthor (Interfaz)](../../winscript/reference/iactivescriptauthor-interface.md)