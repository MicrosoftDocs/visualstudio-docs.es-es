---
title: 'IDebugDocumentHost:: GetFileName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetFileName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetFileName
ms.assetid: b814a848-8a3d-468d-9282-c5c0354b22a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ff2ad2e4ab419f1e503da072aaa550f3cb7cf0e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569394"
---
# <a name="idebugdocumenthostgetfilename"></a>IDebugDocumentHost::GetFileName
Devuelve el nombre del documento sin información de ruta de acceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetFileName(  
   BSTR*  pbstrShortName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrShortName`  
 enuncia Cadena que contiene el nombre corto del documento.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve el nombre corto del documento sin información de ruta de acceso. El nombre corto se utiliza normalmente en situaciones como el cuadro de diálogo **Guardar como** ....  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentHost (Interfaz)](../../winscript/reference/idebugdocumenthost-interface.md)