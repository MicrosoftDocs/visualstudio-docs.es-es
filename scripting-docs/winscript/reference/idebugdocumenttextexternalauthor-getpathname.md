---
title: 'Idebugdocumenttextexternalauthor (:: GetPathName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.GetPathName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::GetPathName
ms.assetid: 445152a1-9cf8-402e-93d6-3d4bf2b81d17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e876b41ce1bde4defffd11267c6665f9d57da077
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575962"
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
Devuelve la ruta de acceso completa y el nombre de archivo del documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrLongName`  
 enuncia Cadena que contiene la ruta de acceso completa y el nombre de archivo.  
  
 `pfIsOriginalFile`  
 enuncia Valor booleano que indica si la ruta de acceso y el nombre de archivo hacen referencia al documento original.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|No se puede crear o determinar el archivo de código fuente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve la ruta de acceso completa y el nombre de archivo del documento.  
  
 Si `pfIsOriginalFile` es FALSE, la ruta de acceso y el nombre de archivo en `pbstrLongName` hacen referencia a un archivo temporal recién creado.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentTextExternalAuthor (Interfaz)](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)