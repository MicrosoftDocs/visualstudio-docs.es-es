---
title: IDebugProcess3::DisableENC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2da464c82332f6fc4f9bcd57ee8197e111e9fa0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116635"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Este método explícitamente deshabilita Editar y continuar en este proceso (y todos los programas contiene). Siempre debe devolver un proveedor de puerto personalizado `E_NOTIMPL`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
);  
```  
  
```csharp  
   EncUnavailableReason reason  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `reason`  
 [in] Un valor de la [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) enumeración.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve el código de error.  
  
> [!NOTE]
>  Siempre debe devolver un proveedor de puerto personalizado `E_NOTIMPL`.  
  
## <a name="remarks"></a>Comentarios  
 Una vez editar y continuar está deshabilitada para un proceso, puede volver a habilitar reiniciando el proceso.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)