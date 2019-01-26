---
title: IEEVisualizerService::GetValueDisplayStringCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5bb70d58cb2f419661253f4aab135bef91d3700b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54978508"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Recupera el número de cadenas de valor que se muestra en la propiedad especificada o el campo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetValueDisplayStringCount (  
   DWORD         displayKind,   
   IDebugField * propertyOrField,   
   ULONG *       pcelt  
);  
```  
  
```csharp  
int GetValueDisplayStringCount (  
   uint        displayKind,   
   IDebugField propertyOrField,   
   out ulong   pcelt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `displayKind`  
 [in] Valor de la [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) enumeración.  
  
 `propertyOrField`  
 [in] Un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaz que representa una propiedad o campo.  
  
 `pcelt`  
 [out] Devuelve el número de cadenas de valor para mostrar.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)