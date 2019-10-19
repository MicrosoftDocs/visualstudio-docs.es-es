---
title: 'Iscriptentry (:: GetRange | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetRange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a6e1b1600c93aa05bbe9669fb57a23a8c9344a1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575430"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Devuelve la posición inicial y la longitud de una entrada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pichMin`  
 enuncia Para `IScriptEntry` objetos que especifican un bloque de script, devuelve 0.  
  
 Para `IScriptEntry` objetos que especifican un objeto de función, devuelve la posición inicial de la función en el bloque de script actual.  
  
 Para los objetos `IScriptScriptlet`, devuelve 0.  
  
 `pcch`  
 enuncia Para `IScriptEntry` objetos que especifican un bloque de script, devuelve la longitud del texto.  
  
 Para `IScriptEntry` objetos que especifican un objeto de función, devuelve la longitud de la definición de función.  
  
 Para los objetos `IScriptScriptlet`, devuelve la longitud de la entrada.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IScriptEntry (Interfaz)](../../winscript/reference/iscriptentry-interface.md)