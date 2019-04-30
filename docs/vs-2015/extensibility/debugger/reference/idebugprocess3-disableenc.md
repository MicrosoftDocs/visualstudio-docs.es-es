---
title: IDebugProcess3::DisableENC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0db9eb44b8074a5c5e3b35a5a5dadcf04f37fb2f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63405733"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método explícitamente deshabilita Editar y continuar en este proceso (y todos los programas contiene). Siempre debe devolver un proveedor de puerto personalizado `E_NOTIMPL`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
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
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve el código de error.  
  
> [!NOTE]
> Siempre debe devolver un proveedor de puerto personalizado `E_NOTIMPL`.  
  
## <a name="remarks"></a>Comentarios  
 Una vez que editar y continuar está deshabilitado para un proceso, puede volver a habilitar reiniciando el proceso.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
