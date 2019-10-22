---
title: 'Iactivescriptauthor (:: GetChars | Microsoft Docs'
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
ms.openlocfilehash: 2ce2b46d65c2ce92111bc4b6f44f66ce9dc4ce5f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576252"
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
 de Contexto de finalización solicitado.  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|0x0001|Solicita la enumeración del lado izquierdo.|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0x0002|Solicita el contexto de finalización de miembros.|  
|SCRIPT_CMPL_PARAM_TRIGGER|0x0003|Solicita la lista de parámetros.|  
|SCRIPT_CMPL_COMMIT|0x0004|Solicita la finalización de la lista de parámetros.|  
  
 `pbstrChars`  
 enuncia Caracteres que corresponden al contexto de finalización solicitado.  
  
|`fRequestedList` parámetro|Caracteres devueltos|  
|--------------------------------|-------------------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|"."|  
|SCRIPT_CMPL_MEMBER_TRIGGER|"="|  
|SCRIPT_CMPL_PARAM_TRIGGER|"(,"|  
|SCRIPT_CMPL_COMMIT|"()"|  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptAuthor (Interfaz)](../../winscript/reference/iactivescriptauthor-interface.md)