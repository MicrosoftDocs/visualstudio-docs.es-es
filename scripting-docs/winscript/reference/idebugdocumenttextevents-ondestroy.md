---
title: IDebugDocumentTextEvents::onDestroy | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentTextEvents.onDestroy
apilocation: scrobj.dll
helpviewer_keywords: IDebugDocumentTextEvents::onDestroy
ms.assetid: 1b7eb341-6bad-403f-9821-19112f8732f3
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd63128fa5222d829b9f676614ffeef83922db27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttexteventsondestroy"></a>IDebugDocumentTextEvents::onDestroy
Indica que el documento subyacente se ha destruido y ya no es válido.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT onDestroy();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método indica que el documento subyacente se ha destruido y ya no es válido.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentTextEvents (Interfaz)](../../winscript/reference/idebugdocumenttextevents-interface.md)