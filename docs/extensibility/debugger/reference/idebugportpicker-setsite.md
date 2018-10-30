---
title: IDebugPortPicker::SetSite | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 00730a5338a3355f2397a91bc7a3693b30dca31b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930614"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
Establece el proveedor de servicios.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetSite(  
   IServiceProvider * pSP  
);  
```  
  
```csharp  
public int SetSite(  
   IServiceProvider pSP  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pSP`  
 [in] Referencia a la interfaz del proveedor de servicios.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método se llamará antes de llamar a ningún otro método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)