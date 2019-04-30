---
title: IDispError::GetNext | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetNext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetNext
ms.assetid: 3e5267f8-ba62-41c3-bd3e-eced2ad85e8e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4af2d239c26c156fad0be7fb45bc04f601d35c83
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437272"
---
# <a name="idisperrorgetnext"></a>IDispError::GetNext
Recupera el siguiente `IDispError` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetNext(  
   IDispError**  ppde  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppde`  
 [out] A continuación especifica `IDispError` objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método recupera el siguiente `IDispError` objeto. Si esta es la última `IDispError` de objeto, este método devuelve NULL.  
  
> [!NOTE]
> Este método no se implementa.  
  
## <a name="see-also"></a>Vea también  
 [IDispError (Interfaz)](../../winscript/reference/idisperror-interface.md)