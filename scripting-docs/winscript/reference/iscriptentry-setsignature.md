---
title: IScriptEntry::SetSignature | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.SetSignature
apilocation: scrobj.dll
helpviewer_keywords: IScriptEntry::SetSignature
ms.assetid: 8513587d-9df2-4621-afe7-56eacbb5e688
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9ff480f8e5c3192a7e2b355d39825cc3a084370
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrysetsignature"></a>IScriptEntry::SetSignature
Conjuntos de información de tipo para un `IScriptEntry` objeto de función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pti`  
 [in] La información de tipo.  
  
 `iMethod`  
 [in] El índice de método en el `ITypeInfo` objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Establecer información de tipo mediante el uso de `IScriptEntry::SetSignature` o [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Información de tipos también puede generarse con la entrada en función de la representación de la función interna.  
  
## <a name="see-also"></a>Vea también  
 [IScriptEntry (Interfaz)](../../winscript/reference/iscriptentry-interface.md)