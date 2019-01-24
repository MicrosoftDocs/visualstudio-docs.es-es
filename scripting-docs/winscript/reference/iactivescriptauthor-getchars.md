---
title: IActiveScriptAuthor::GetChars | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 06e7a7cf276e589aaaa3c00ecab8cbf881942f82
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094333"
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
|SCRIPT_CMPL_ENUM_TRIGGER|0 x 0001|Solicita la enumeración del lado izquierdo.|  
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