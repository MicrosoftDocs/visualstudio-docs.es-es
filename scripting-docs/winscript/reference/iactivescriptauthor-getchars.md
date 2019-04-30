---
title: IActiveScriptAuthor::GetChars | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetChars
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetChars
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 69cdeb16fa0791b3ff8c0cce4a4e67fe110eefc2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935378"
---
# <a name="iactivescriptauthorgetchars"></a>IActiveScriptAuthor::GetChars
Devuelve el conjunto de caracteres de finalización para un contexto de finalización solicitado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fRequestedList`  
 [in] El contexto solicitado de finalización.  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|0x0001|Solicita la enumeración del lado izquierdo.|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0x0002|Solicita el contexto de la finalización de miembros.|  
|SCRIPT_CMPL_PARAM_TRIGGER|0x0003|Solicita la lista de parámetros.|  
|SCRIPT_CMPL_COMMIT|0x0004|Finalización de las solicitudes de la lista de parámetros.|  
  
 `pbstrChars`  
 [out] Los caracteres que se corresponden con el contexto de finalización solicitado.  
  
|`fRequestedList` Parámetro|Devuelve caracteres adicionales.|  
|--------------------------------|-------------------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|"."|  
|SCRIPT_CMPL_MEMBER_TRIGGER|"="|  
|SCRIPT_CMPL_PARAM_TRIGGER|"(,"|  
|SCRIPT_CMPL_COMMIT|"()"|  
  
## <a name="return-value"></a>Valor devuelto  
 Una clase `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptAuthor (Interfaz)](../../winscript/reference/iactivescriptauthor-interface.md)