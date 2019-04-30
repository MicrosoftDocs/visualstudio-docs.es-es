---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 131f5a5f276b3f93d2ede3d088556b6832cc3651
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445289"
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método obtiene las utilidades de equipo para un servidor.  
  
> [!NOTE]
> Este método está obsoleto: no use ([!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] siempre devuelve `E_NOTIMPL` si se llama a este método). Se conserva por motivos históricos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```csharp  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
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
