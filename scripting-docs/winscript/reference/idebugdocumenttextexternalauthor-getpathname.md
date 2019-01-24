---
title: IDebugDocumentTextExternalAuthor::GetPathName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: e17d27a320eac95445c083c718f5abcebbbc46cf
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088847"
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
Devuelve la ruta de acceso y el nombre completo del documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrLongName`  
 [out] Cadena que contiene la ruta de acceso y el nombre completo.  
  
 `pfIsOriginalFile`  
 [out] Valor booleano que indica si el nombre de ruta de acceso y hacer referencia al documento original.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|El archivo de origen no puede ser creado o determinado.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve la ruta de acceso y el nombre completo del documento.  
  
 Si `pfIsOriginalFile` es FALSE, la ruta de acceso y nombre en `pbstrLongName` hacen referencia a un archivo temporal recién creado.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentTextExternalAuthor (Interfaz)](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)