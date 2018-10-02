---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 217118d96fbcf50f267570bcd1c26abd5d8128c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574332"
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugCoreServer2::GetMachineUtilities_V7](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7).  
  
Este método obtiene las utilidades de equipo para un servidor.  
  
> [!NOTE]
>  Este método está obsoleto: no use ([!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] siempre devuelve `E_NOTIMPL` si se llama a este método). Se conserva por motivos históricos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```csharp  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppUtil`  
 [out] Devuelve un `IDebugMDMUtil2_V7` interfaz que representa la información de las utilidades de la máquina.  
  
## <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `E_NOTIMPL`, que indica que no se implementa el método.  
  
## <a name="remarks"></a>Comentarios  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] siempre devuelve `E_NOTIMPL` si se llama a este método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)

