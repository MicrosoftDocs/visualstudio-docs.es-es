---
title: IDebugErrorBreakpointResolution2::GetResolutionInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugErrorBreakpointResolution2::GetResolutionInfo
helpviewer_keywords:
- IDebugErrorBreakpointResolution2::GetResolutionInfo
ms.assetid: d94c4f60-8796-4848-86ee-186bbaa613f5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 475bfaae3e55af761eb1d19841d9b0aadad7a9e7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877080"
---
# <a name="idebugerrorbreakpointresolution2getresolutioninfo"></a>IDebugErrorBreakpointResolution2::GetResolutionInfo
Obtiene la información de resolución de errores de punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetResolutionInfo(   
   BPERESI_FIELDS            dwFields,  
   BP_ERROR_RESOLUTION_INFO* pErrorResolutionInfo  
);  
```  
  
```csharp  
int GetResolutionInfo(   
   enum_BPERESI_FIELDS        dwFields,  
   BP_ERROR_RESOLUTION_INFO[] pErrorResolutionInfo  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwFields`  
 [in] Una combinación de marcas de la [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) enumeración que determina qué campos de `pErrorResolutionInfo` son para rellenarlo.  
  
 `pErrorResolutionInfo`  
 [in, out] El [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) estructura que se rellena con la descripción de la resolución de punto de interrupción.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se implementa este método para una sencilla `CDebugErrorBreakpointResolution` objeto que expone el [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) interfaz.  
  
```  
HRESULT CDebugErrorBreakpointResolution::GetResolutionInfo(  
   BPERESI_FIELDS dwFields,  
   BP_ERROR_RESOLUTION_INFO* pBPErrorResolutionInfo)    
{    
   HRESULT hr;    
  
   if (pBPErrorResolutionInfo)    
   {    
      // Copy the specified fields of the request information from the class member  
      // variable to the local BP_ERROR_RESOLUTION_INFO variable.    
      hr = CopyBP_ERROR_RESOLUTION_INFO(m_bpErrorResolutionInfo,  
                                        *pBPErrorResolutionInfo,  
                                        dwFields);    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}  
  
HRESULT CDebugErrorBreakpointResolution::CopyBP_ERROR_RESOLUTION_INFO(  
   BP_ERROR_RESOLUTION_INFO& bpResSrc,  
   BP_ERROR_RESOLUTION_INFO& bpResDest,  
   DWORD dwFields)  
{    
   HRESULT hr = S_OK;    
  
   // Start with a raw copy.    
   memcpy(&bpResDest, &bpResSrc, sizeof(BP_ERROR_RESOLUTION_INFO));    
  
   // The fields in the destination is the result of the AND of bpInfoSrc.dwFields  
   // and dwFields.    
   bpResDest.dwFields = dwFields & bpResSrc.dwFields;    
  
   // Fill in the bp location information if the BPERESI_BPRESLOCATION flag  
   // is set in BPERESI_FIELDS.    
   if (IsFlagSet(bpResDest.dwFields, BPERESI_BPRESLOCATION))    
   {    
      // Switch on the BP_TYPE.      
      switch (bpResSrc.bpResLocation.bpType)    
      {    
         case BPT_CODE:    
         {    
            // AddRef the IDebugCodeContext2 of the BP_RESOLUTION_CODE structure.    
            bpResDest.bpResLocation.bpResLocation.bpresCode.pCodeContext->AddRef();    
            break;    
         }    
         case BPT_DATA:    
         {    
            // Copy the bstrDataExpr, bstrFunc, and bstrImage of the  
            // BP_RESOLUTION_DATA structure.    
            bpResDest.bpResLocation.bpResLocation.bpresData.bstrDataExpr =  
               SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrDataExpr);  
            bpResDest.bpResLocation.bpResLocation.bpresData.bstrFunc =  
               SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrFunc);  
            bpResSrc.bpResLocation.bpResLocation.bpresData.bstrImage =  
               SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrImage);  
            break;  
         }  
         default:  
         {  
            assert(FALSE);  
            // Clear the BPERESI_BPRESLOCATION flag of the BPERESI_FIELDS  
            // in the destination BP_ERROR_RESOLUTION_INFO.  
            ClearFlag(bpResDest.dwFields, BPERESI_BPRESLOCATION);  
            break;  
         }    
      }    
   }    
   // AddRef the IDebugProgram2 if the BPRESI_PROGRAM flag is set in the BPRESI_FIELDS.    
   if (IsFlagSet(bpResDest.dwFields, BPERESI_PROGRAM))    
   {    
      bpResDest.pProgram->AddRef();    
   }    
   // AddRef the IDebuThread2 if the BPRESI_THREAD flag is set in the BPRESI_FIELDS.    
   if (IsFlagSet(bpResDest.dwFields, BPERESI_THREAD))    
   {    
      bpResDest.pThread->AddRef();    
   }    
   // Check if the BPERESI_MESSAGE flag is set in the BPRESI_FIELDS.    
   if (IsFlagSet(bpResDest.dwFields, BPERESI_MESSAGE))    
   {    
      // Copy the source bstrMessage into the destination bstrMessage.    
      bpResDest.bstrMessage = SysAllocString(bpResSrc.bstrMessage);    
      // Clear the destination flag if there is no message.    
      if (!bpResDest.bstrMessage)    
      {    
         ClearFlag(bpResDest.dwFields, BPERESI_MESSAGE);    
      }    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)   
 [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)