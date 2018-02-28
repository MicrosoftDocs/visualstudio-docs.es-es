---
title: IScriptEntry::GetRange | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptEntry.GetRange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ae0ee34298e03fdd2e9c6bc841d9fbe90967e8f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Devuelve la posición de inicio y la longitud de una entrada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pichMin`  
 [out] Para `IScriptEntry` objetos que especifican un bloque de script, devuelve 0.  
  
 Para `IScriptEntry` objetos que especifican un objeto de función, se devuelve la posición inicial de la función en el bloque de script actual.  
  
 Para `IScriptScriptlet` los objetos, devuelve 0.  
  
 `pcch`  
 [out] Para `IScriptEntry` objetos que especifican un bloque de script, se devuelve la longitud del texto.  
  
 Para `IScriptEntry` objetos que especifican un objeto de función, devuelve la longitud de la definición de función.  
  
 Para `IScriptScriptlet` los objetos, devuelve la longitud de la entrada.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IScriptEntry (Interfaz)](../../winscript/reference/iscriptentry-interface.md)