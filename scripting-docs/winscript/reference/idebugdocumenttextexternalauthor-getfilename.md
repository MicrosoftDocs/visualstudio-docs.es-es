---
title: IDebugDocumentTextExternalAuthor::GetFileName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.GetFileName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::GetFileName
ms.assetid: 87acdce6-acb2-4936-80dd-d624bb7dbd42
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: edb988751b8a0c0e6450e1fa216a474df2e8c59d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158716"
---
# <a name="idebugdocumenttextexternalauthorgetfilename"></a>IDebugDocumentTextExternalAuthor::GetFileName
Devuelve el nombre del documento sin información de ruta de acceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetFileName(  
   BSTR*  pbstrShortName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrShortName`  
 [out] Cadena que contiene el nombre corto del documento.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve el nombre del documento sin información de ruta de acceso. El nombre corto se utiliza normalmente en los cuadros de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentTextExternalAuthor (Interfaz)](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)