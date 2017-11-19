---
title: IDebugDocumentHost::GetFileName | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHost.GetFileName
apilocation: scrobj.dll
helpviewer_keywords: IDebugDocumentHost::GetFileName
ms.assetid: b814a848-8a3d-468d-9282-c5c0354b22a1
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 909c431a389a2589d48b6228534b16675ea41383
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthostgetfilename"></a>IDebugDocumentHost::GetFileName
Devuelve el nombre del documento sin información de ruta de acceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetFileName(  
   BSTR*  pbstrShortName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrShortName`  
 [out] Una cadena que contiene el nombre corto del documento.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve el nombre corto del documento sin información de ruta de acceso. El nombre corto se utiliza normalmente en situaciones como la **Guardar como...**  cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentHost (Interfaz)](../../winscript/reference/idebugdocumenthost-interface.md)