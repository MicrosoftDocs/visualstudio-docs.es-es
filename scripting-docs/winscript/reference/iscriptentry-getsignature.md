---
title: IScriptEntry::GetSignature | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetSignature
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 245b5806006ad94740e09e23f881e26e071a3bc1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092734"
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
Devuelve información de tipo para un `IScriptEntry` objeto de función.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppti`  
 [out] Escriba la información asociada a este `IScriptEntry` objeto de función.  
  
 `piMethod`  
 [out] Índice del método en el `ITypeInfo` objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 Una clase `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Establecer información de tipo mediante el uso de [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) o [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). También se puede generar información de tipo con la entrada en función de la representación de la función interna.  
  
## <a name="see-also"></a>Vea también  
 [IScriptEntry (Interfaz)](../../winscript/reference/iscriptentry-interface.md)