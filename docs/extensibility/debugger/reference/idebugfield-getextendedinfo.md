---
title: IDebugField::GetExtendedInfo | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ef431fbc3bf14124ee0ea08a2439c0473e958a91
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945215"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Este método obtiene información sobre un campo adicional.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```csharp  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `guidExtendedInfo`  
 [in] Selecciona la información que se va a devolver. Los valores válidos son:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`guidConstantValue`|El valor como una secuencia de bytes.|  
|`guidConstantType`|El tipo como una signatura de tipo.|  
  
 `prgBuffer`  
 [out] Devuelve la información extendida.  
  
 `pdwLen`  
 [in, out] Devuelve el tamaño de la información extendida, en bytes.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Actualmente, este método devuelve sólo el tipo o valor de una constante. El llamador debe liberar el búfer devuelto en `prgBuffer` por una llamada de COM `CoTaskMemFree` función (C++) o <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#).  
  
## <a name="see-also"></a>Vea también  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)