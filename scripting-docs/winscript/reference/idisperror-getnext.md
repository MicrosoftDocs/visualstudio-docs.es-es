---
title: IDispError::GetNext | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispError.GetNext
apilocation: scrobj.dll
helpviewer_keywords: IDispError::GetNext
ms.assetid: 3e5267f8-ba62-41c3-bd3e-eced2ad85e8e
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cbe4b044f2d3fb1d8ffb08565fc4093fbbe3ec7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idisperrorgetnext"></a>IDispError::GetNext
Recupera el siguiente `IDispError` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetNext(  
   IDispError**  ppde  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppde`  
 [out] Especifica a continuación `IDispError` objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método recupera el siguiente `IDispError` objeto. Si se trata de la última `IDispError` de objeto, este método devuelve NULL.  
  
> [!NOTE]
>  Este método no se implementa.  
  
## <a name="see-also"></a>Vea también  
 [IDispError (Interfaz)](../../winscript/reference/idisperror-interface.md)