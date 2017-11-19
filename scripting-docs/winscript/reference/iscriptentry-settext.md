---
title: IScriptEntry::SetText | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.SetText
apilocation: scrobj.dll
helpviewer_keywords: ISetEntry::SetText
ms.assetid: 4605481b-7707-43d1-ab78-a9207d0cf6fe
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62f1d113dc23dca85db02bf23b2c79551108f3b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrysettext"></a>IScriptEntry::SetText
Establece el texto que se corresponde con un `IScriptEntry` bloque de scripts o el código fuente que se encuentra en un `IScriptScriptlet` controlador de eventos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT SetText(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `psz`  
 [in] El texto de la `IScriptEntry` bloque de scripts o el código fuente de la `IScriptScriptlet` controlador de eventos.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IScriptEntry (Interfaz)](../../winscript/reference/iscriptentry-interface.md)