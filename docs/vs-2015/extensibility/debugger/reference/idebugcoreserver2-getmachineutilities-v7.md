---
title: 'IDebugCoreServer2:: GetMachineUtilities_V7 | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843223"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método obtiene las utilidades del equipo para un servidor.  
  
> [!NOTE]
> Este método está obsoleto: no use ( [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] siempre devuelve `E_NOTIMPL` si se llama a este método). Se conserva por motivos históricos.  
  
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
 enuncia Devuelve una `IDebugMDMUtil2_V7` interfaz que representa la información de las utilidades del equipo.  
  
## <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `E_NOTIMPL` , que indica que no se ha implementado el método.  
  
## <a name="remarks"></a>Notas  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] siempre devuelve `E_NOTIMPL` si se llama a este método.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
