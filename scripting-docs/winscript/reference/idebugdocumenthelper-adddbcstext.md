---
title: IDebugDocumentHelper::AddDBCSText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDBCSText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDBCSText
ms.assetid: 5e5011b2-bbb4-491b-9a11-eb2846be44aa
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d5de41ff83f3ffd5b208445830862138511ba2b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154798"
---
# <a name="idebugdocumenthelperadddbcstext"></a>IDebugDocumentHelper::AddDBCSText
Anexa una cadena DBCS al final de este documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
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
>  Si se llama a este método después de `IDebugDocumentHelper::AddDeferredText` se ha llamado, `E_FAIL` se devuelve.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentHelper (interfaz)](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [IDebugDocumentTextEvents (Interfaz)](../../winscript/reference/idebugdocumenttextevents-interface.md)