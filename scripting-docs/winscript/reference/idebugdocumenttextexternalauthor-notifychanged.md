---
title: IDebugDocumentTextExternalAuthor::NotifyChanged | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.NotifyChanged
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::NotifyChanged
ms.assetid: f0de7984-3a15-49e2-bd29-f768f34d2a4d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1290de76f8bec5018ad83eb4499c3d92cbf9eba9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978541"
---
# <a name="idebugdocumenttextexternalauthornotifychanged"></a>IDebugDocumentTextExternalAuthor::NotifyChanged
Notifica al host que ha cambiado el código fuente del documento.  
  
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
 Un editor externo llama a este método después de un documento basado en archivos depurador se puede modificar y guardar para notificar al host que ha cambiado el código fuente del documento. El host, a continuación, actualiza el documento desde el archivo de origen.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentTextExternalAuthor (Interfaz)](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)