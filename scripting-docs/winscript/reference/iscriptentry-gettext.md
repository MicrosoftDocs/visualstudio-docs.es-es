---
title: 'Iscriptentry (:: GetText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetText
ms.assetid: 105b8244-1972-4b39-ac18-965f1f345ef2
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b25c1667f1df7e0394dd2ebfb0fea452da1b47d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575403"
---
# <a name="iscriptentrygettext"></a>IScriptEntry::GetText
Devuelve el texto que corresponde al `IScriptEntry` bloque de script o el código fuente contenido en el controlador de eventos `IScriptScriptlet`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetText(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstr`  
 enuncia El texto del bloque de script de `IScriptEntry` o el código fuente incluido en el controlador de eventos `IScriptScriptlet`.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IScriptEntry (Interfaz)](../../winscript/reference/iscriptentry-interface.md)