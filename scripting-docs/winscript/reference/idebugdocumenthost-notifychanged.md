---
title: IDebugDocumentHost::NotifyChanged | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.NotifyChanged
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::NotifyChanged
ms.assetid: 33a4a54f-3bcb-4422-b3c0-bdbf46590f34
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e65383bcfe875f0e38fffc870d5176d86433d8f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153843"
---
# <a name="idebugdocumenthostnotifychanged"></a>IDebugDocumentHost::NotifyChanged
Notifica al host que se ha guardado el archivo de código fuente del documento y que se debe actualizar su contenido.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT NotifyChanged();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método notifica al host que se ha guardado el archivo de código fuente del documento y que se debe actualizar su contenido.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentHost (Interfaz)](../../winscript/reference/idebugdocumenthost-interface.md)