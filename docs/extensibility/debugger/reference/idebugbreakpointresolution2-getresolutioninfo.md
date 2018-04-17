---
title: IDebugBreakpointResolution2::GetResolutionInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointResolution2::GetResolutionInfo
helpviewer_keywords:
- IDebugBreakpointResolution2::GetResolutionInfo
ms.assetid: 828cbdf6-b87d-4c45-be87-d87087b04a60
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 17e08e335f2f50967da2b566ef595717e07fc2d1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbreakpointresolution2getresolutioninfo"></a>IDebugBreakpointResolution2::GetResolutionInfo
Obtiene la información de resolución de punto de interrupción que describe este punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetResolutionInfo(   
   BPRESI_FIELDS       dwFields,  
   BP_RESOLUTION_INFO* pBPResolutionInfo  
);  
```  
  
```csharp  
int GetResolutionInfo(   
   enum BPRESI_FIELDS   dwFields,  
   BP_RESOLUTION_INFO[] pBPResolutionInfo  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwFields`  
 [in] Una combinación de indicadores de la [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) enumeración que determina qué campos de la `pBPResolutionInfo` parámetro son debe rellenarse.  
  
 `pBPResolutionInfo`  
 [out] El [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) estructura que se rellena con información acerca de este punto de interrupción.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se implementa este método para un sencillo `CDebugBreakpointResolution` objeto que expone la [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) interfaz.  
  
```  
HRESULT CDebugBreakpointResolution::GetResolutionInfo(  
   BPRESI_FIELDS dwFields,  
   BP_RESOLUTION_INFO* pBPResolutionInfo)  
{    
   HRESULT hr;    
  
   if (pBPResolutionInfo)    
   {    
      // Copy the specified fields of the request information from the class  
      // member variable to the local BP_RESOLUTION_INFO variable.    
      hr = CopyBP_RESOLUTION_INFO(m_bpResolutionInfo,  
                                  *pBPResolutionInfo,  
                                  dwFields);    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
  
HRESULT CDebugBreakpointResolution::CopyBP_RESOLUTION_INFO(  
   BP_RESOLUTION_INFO& bpResSrc,  
   BP_RESOLUTION_INFO& bpResDest,  
   DWORD dwFields)    
{    
   HRESULT hr = S_OK;    
  
   // Start with a raw copy.    
   memcpy(&bpResDest, &bpResSrc, sizeof(BP_RESOLUTION_INFO));    
  
   // The fields in the destination is the result of the AND of  
   //  bpInfoSrc.dwFields and dwFields.    
   bpResDest.dwFields = dwFields & bpResSrc.dwFields;    
  
   // Fill in the bp location information if the BPRESI_BPRESLOCATION  
   //  flag is set in BPRESI_FIELDS.    
   if (IsFlagSet(bpResDest.dwFields, BPRESI_BPRESLOCATION))    
   {    
      // Switch based on the BP_TYPE.     
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
            // Clear the BPRESI_BPRESLOCATION flag in the BPRESI_FIELDS  
            // of the destination BP_RESOLUTION_INFO.    
            ClearFlag(bpResDest.dwFields, BPRESI_BPRESLOCATION);    
            break;    
         }    
      }    
   }    
   // AddRef the IDebugProgram2 if the BPRESI_PROGRAM flag is set in BPRESI_FIELDS.  
   if (IsFlagSet(bpResDest.dwFields, BPRESI_PROGRAM))    
   {    
      bpResDest.pProgram->AddRef();    
   }    
   // AddRef the IDebugThread2 if the BPRESI_THREAD flag is set in BPRESI_FIELDS.  
   if (IsFlagSet(bpResDest.dwFields, BPRESI_THREAD))    
   {    
      bpResDest.pThread->AddRef();    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)   
 [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)