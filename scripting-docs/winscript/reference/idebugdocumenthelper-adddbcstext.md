---
title: IDebugDocumentHelper::AddDBCSText | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.AddDBCSText
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::AddDBCSText
ms.assetid: 5e5011b2-bbb4-491b-9a11-eb2846be44aa
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37cd0f2953483e23636c3a17d7726bc2c438b303
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperadddbcstext"></a>IDebugDocumentHelper::AddDBCSText
Anexa una cadena DBCS al final de este documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT AddDBCSText(  
   LPCSTR  pszText  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszText`  
 [in] Puntero a una cadena terminada en null que contiene el texto.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|El método no pudo agregar los caracteres.|  
  
## <a name="remarks"></a>Comentarios  
 Este método genera `IDebugDocumentTextEvents` notificaciones.  
  
> [!NOTE]
>  Si se llama a este método después de `IDebugDocumentHelper::AddDeferredText` se ha llamado `E_FAIL` se devuelve.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentHelper (interfaz)](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [IDebugDocumentTextEvents (Interfaz)](../../winscript/reference/idebugdocumenttextevents-interface.md)