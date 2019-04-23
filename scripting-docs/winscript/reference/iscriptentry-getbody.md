---
title: IScriptEntry::GetBody | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetBody
ms.assetid: 419c8c11-a1f8-4b97-ab00-e8af2b2f9bfc
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f8f1ad24660401d575af2724b788387fd546af8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60064923"
---
# <a name="iscriptentrygetbody"></a>IScriptEntry::GetBody
Devuelve el texto que corresponde al cuerpo de un `IScriptEntry` scriptlet, bloque de función o bloque de script.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetBody(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstr`  
 [out] El texto que se encuentra en el cuerpo de una de las siguientes:  
  
- Un `IScriptEntry` bloque de script  
  
- Un `IScriptEntry` función en un bloque de función  
  
- Un `IScriptEntry` scriptlet controlador de eventos  
  
## <a name="return-value"></a>Valor devuelto  
 Una clase `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IScriptEntry (Interfaz)](../../winscript/reference/iscriptentry-interface.md)