---
title: IScriptEntry::GetRange | Microsoft Docs
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
ms.openlocfilehash: 7baa284be4fa7f45f247df7f4b3d140869f254b1
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151874"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Devuelve la posición inicial y longitud de una entrada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pichMin`  
 [out] Para `IScriptEntry` objetos que especifican un bloque de script, devuelve 0.  
  
 Para `IScriptEntry` objetos que especifican un objeto de función devuelve la posición inicial de la función en el bloque de script actual.  
  
 Para `IScriptScriptlet` los objetos, devuelve 0.  
  
 `pcch`  
 [out] Para `IScriptEntry` objetos que especifican un bloque de script, se devuelve la longitud del texto.  
  
 Para `IScriptEntry` objetos que especifican un objeto de función devuelve la longitud de la definición de función.  
  
 Para `IScriptScriptlet` los objetos, devuelve la longitud de la entrada.  
  
## <a name="return-value"></a>Valor devuelto  
 Una clase `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IScriptEntry (Interfaz)](../../winscript/reference/iscriptentry-interface.md)