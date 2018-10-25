---
title: IDebugField::GetExtendedInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: b276b2bff8e8ab5af0f007fbc5bd5dd6074c4d9d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896053"
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