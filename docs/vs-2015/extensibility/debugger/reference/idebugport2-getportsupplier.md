---
title: IDebugPort2::GetPortSupplier | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPort2::GetPortSupplier
helpviewer_keywords:
- IDebugPort2::GetPortSupplier
ms.assetid: 7a7b0615-df6b-4726-ab35-39dfa1ebed8f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cfe864e09ac86b393c4cc2aa38873d5b79da7c76
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818177"
---
# <a name="idebugport2getportsupplier"></a>IDebugPort2::GetPortSupplier
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene el proveedor del puerto para este puerto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetPortSupplier(   
   IDebugPortSupplier2** ppSupplier  
);  
```  
  
```csharp  
int GetPortSupplier(   
   out IDebugPortSupplier2 ppSupplier  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppSupplier`  
 [out] Devuelve un [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) objeto representa el proveedor del puerto para un puerto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)

