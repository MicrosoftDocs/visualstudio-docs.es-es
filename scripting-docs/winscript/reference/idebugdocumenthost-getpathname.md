---
title: IDebugDocumentHost::GetPathName | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetPathName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetPathName
ms.assetid: 8abe2a86-e467-4ac9-8ccb-8761141bfa0d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 42fffa160a1f5b55dc9ba0287c2fdf3073e27e0d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726675"
---
# <a name="idebugdocumenthostgetpathname"></a>IDebugDocumentHost::GetPathName
Devuelve el nombre completo de ruta de acceso y del archivo de código fuente del documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrLongName`  
 [out] Una cadena que contiene el nombre largo.  
  
 `pfIsOriginalFile`  
 [out] Una marca que es true si `pbstrLongName` hace referencia al archivo original para el documento, false en caso contrario.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|Se puede crear ningún archivo de código fuente o determinado.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve el nombre completo de ruta de acceso y del archivo de código fuente del documento.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentHost (Interfaz)](../../winscript/reference/idebugdocumenthost-interface.md)