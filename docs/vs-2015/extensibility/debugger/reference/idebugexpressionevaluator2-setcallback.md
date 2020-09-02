---
title: 'IDebugExpressionEvaluator2:: SetCallback | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d6f715bb33afe051cdccffbf3219e062b606f57
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179927"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Habilita el evaluador de expresiones (EE) para especificar la interfaz de devolución de llamada que usará el motor DE depuración (DE) para leer la configuración de métricas.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT SetCallback (  
   IDebugSettingsCallback2* pCallback  
);  
```  
  
```csharp  
int SetCallback (  
   IDebugSettingsCallback2 pCallback  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pCallback`  
 de Interfaz que se va a usar para la devolución de llamada de configuración.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Observaciones  
 Este método proporciona una interfaz para el administrador de depuración de la sesión que puede usar un evaluador de expresiones para leer la configuración de métricas. Resulta útil en la depuración remota para leer las métricas del [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] equipo.  
  
## <a name="example"></a>Ejemplo  
 En los siguientes ejemplos se muestra cómo implementar este método para un objeto **CEE** que expone la interfaz [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) .  
  
```cpp#  
HRESULT CEE::SetCallback(IDebugSettingsCallback2* in_pCallback)  
{  
    // precondition  
    INVARIANT( this );  
  
    // function body  
    if (NULL != this->m_LanguageSpecificUseCases.pfSetCallback)  
    {  
        EEDomain::fSetCallback DomainVal =  
        {  
            in_pCallback  
        };  
  
        BOOL bSuccess = (*this->m_LanguageSpecificUseCases.pfSetCallback)(DomainVal);  
        ENSURE( bSuccess );  
    }  
  
    // postcondition  
    INVARIANT( this );  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Consulte también  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
