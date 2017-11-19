---
title: IRemoteDebugApplicationEx:SetLocale | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplicationEx:SetLocale
apilocation: scrobj.dll
helpviewer_keywords: IRemoteDebugApplicationEx:SetLocale
ms.assetid: cd19f725-f4cd-453a-95e1-0bad676451da
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 19b2d58974e7da7bd40dad1faa9e361b0327e4c6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationexsetlocale"></a>IRemoteDebugApplicationEx:SetLocale
Establece el idioma para la localización de depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT SetLocale(  
   DWORD  dwLangID  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwLangID`  
 [in] El identificador de idioma.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [ISetNextStatement (Interfaz)](../../winscript/reference/isetnextstatement-interface.md)