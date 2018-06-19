---
title: IDebugDocumentHost::OnCreateDocumentContext | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.OnCreateDocumentContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::OnCreateDocumentContext
ms.assetid: 080c8604-cfd7-484e-a337-15040870e683
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55598a4191d421d3aea01d27cc7991b70bd6a019
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726725"
---
# <a name="idebugdocumenthostoncreatedocumentcontext"></a>IDebugDocumentHost::OnCreateDocumentContext
Notifica al host que un nuevo contexto de documento se está creando y permite que el host también pueden devolver un control desconocido para el nuevo contexto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppunkOuter`  
 [out] Un objeto que controla el nuevo contexto.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_NOTIMPL`|El host no proporciona un objeto de control.|  
  
## <a name="remarks"></a>Comentarios  
 Este método permite al host agregar nuevas funciones a los contextos de documento proporcionado por el Ayudante. Este método puede devolver **E_NOTIMPL** o un objeto externo null, en cuyo caso el llamador es responsable de crear el contexto.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentHost (Interfaz)](../../winscript/reference/idebugdocumenthost-interface.md)