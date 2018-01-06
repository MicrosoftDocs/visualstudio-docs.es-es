---
title: IDebugSettingsCallback2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 779550509dd6d30b16f30a47c1b9a2879d5034ab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Habilita el motores para leer la configuración de la métrica de depuración remota.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugSettingsCallback2D : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz se implementa mediante la devolución de llamada de evento del Administrador de sesión de depuración y utilizada por motores de depuración. También puede usar localmente en lugar de Dbgmetric [d] .lib.  
  
## <a name="methods"></a>Métodos  
 La tabla siguiente muestran los métodos de `IDebugSettingsCallback2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Enumera los evaluadores de expresión disponibles dados los identificadores de idioma y el proveedor.|  
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Recupera un objeto local de evaluador de expresiones tiene la métrica.|  
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Recupera un valor que corresponde a la métrica especificada del evaluador de expresiones.|  
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Recupera el archivo de métrica de evaluador de expresiones dado el nombre o la métrica.|  
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Recupera el identificador único para una métrica de evaluador de expresiones dado su nombre.|  
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Recupera la cadena del valor de una métrica de evaluador de expresiones dada su nombre.|  
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Recupera el valor de una métrica de acuerdo con su nombre.|  
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Recupera el identificador único de una métrica de acuerdo con su nombre.|  
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Recupera la cadena del valor de la métrica de acuerdo con su nombre.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra una función que toma un **IDebugSettingsCallback2** objeto como parámetro.  
  
```cpp  
HRESULT GetDebugSettingsCallback (IDebugSettingsCallback2 **ppCallback)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppCallback )  
   {  
        if ( EVAL(m_pdec) )  
            hRes = m_pdec->QueryInterface(IID_IDebugSettingsCallback2, (void **)ppCallback);  
        else  
            hRes = E_FAIL;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```