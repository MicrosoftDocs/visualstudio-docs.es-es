---
title: IDispError::GetDescription | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetDescription
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetDescription
ms.assetid: 04deaea6-0265-4e34-952e-634edba0e923
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa0c837be9a98829551b9c7820faf154779479e4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096959"
---
# <a name="idisperrorgetdescription"></a>IDispError::GetDescription
Devuelve una descripción textual del error.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetDescription(  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrDescription`  
 [out] Cadena que contiene una breve descripción del error.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Se devuelve el texto en el idioma especificado por el identificador de configuración regional (LCID) que se pasó a `IDispatchEx::InvokeEx` para el método que encontró el error.  
  
> [!NOTE]
>  Este método no se implementa.  
  
## <a name="see-also"></a>Vea también  
 [IDispError (interfaz)](../../winscript/reference/idisperror-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)