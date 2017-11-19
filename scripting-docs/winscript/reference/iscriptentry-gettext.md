---
title: IScriptEntry::GetText | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.GetText
apilocation: scrobj.dll
helpviewer_keywords: IScriptEntry::GetText
ms.assetid: 105b8244-1972-4b39-ac18-965f1f345ef2
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 548b26be48766fa4eb6c6eba16ae3bca2847a322
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygettext"></a>IScriptEntry::GetText
Devuelve el texto que corresponde a la `IScriptEntry` bloque de scripts o el código fuente que se encuentra en la `IScriptScriptlet` controlador de eventos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetText(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstr`  
 [out] El texto en el `IScriptEntry` bloque de scripts o el código fuente que se encuentra en la `IScriptScriptlet` controlador de eventos.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IScriptEntry (Interfaz)](../../winscript/reference/iscriptentry-interface.md)