---
title: IDebugErrorBreakpointResolution2::GetBreakpointType | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugErrorBreakpointResolution2::GetBreakpointType
helpviewer_keywords:
- IDebugErrorBreakpointResolution2::GetBreakpointType
ms.assetid: 0bdb1152-4752-4464-ae7c-6d666dc293b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c001e47b7393daa07b799ff78f31019d21ec5ee2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951488"
---
# <a name="idebugerrorbreakpointresolution2getbreakpointtype"></a>IDebugErrorBreakpointResolution2::GetBreakpointType
Obtiene el tipo de punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetBreakpointType(   
   BP_TYPE* pBPType  
);  
```  
  
```csharp  
int GetBreakpointType(   
   out enum_BP_TYPE pBPType  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pBPType`  
 [out] Devuelve un valor de la [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) enumeración que describe el tipo de punto de interrupción.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve el tipo del punto de interrupción que no se pudo enlazar, por lo que requiere un evento de error de punto de interrupción.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo implementar este método para una sencilla `CDebugErrorBreakpointResolution` objeto que expone el [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) interfaz.  
  
```  
HRESULT CDebugErrorBreakpointResolution::GetBreakpointType(BP_TYPE* pBPType)    
{    
   HRESULT hr;    
  
   if (pBPType)    
   {    
      // Set default BP_TYPE.    
      *pBPType = BPT_NONE;    
  
      // Check if the BPERESI_BPRESLOCATION flag is set in BPERESI_FIELDS.    
      if (IsFlagSet(m_bpErrorResolutionInfo.dwFields, BPERESI_BPRESLOCATION))    
      {    
         // Set the new BP_TYPE.    
         *pBPType = m_bpErrorResolutionInfo.bpResLocation.bpType;    
         hr = S_OK;    
      }    
      else    
      {    
         hr = E_FAIL;    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)