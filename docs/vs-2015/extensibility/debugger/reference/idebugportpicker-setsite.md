---
title: IDebugPortPicker::SetSite | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 57f3ada6c5a1b2434e5b88b077f71c678321db68
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575558"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugPortPicker::SetSite](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportpicker-setsite).  
  
Establece el proveedor de servicios.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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

