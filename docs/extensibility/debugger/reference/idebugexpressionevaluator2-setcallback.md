---
title: IDebugExpressionEvaluator2::SetCallback | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f4b7c0333ff5328f4bdfd2411356074dc39d567c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31110613"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Permite que el evaluador de expresiones (EE) especificar la interfaz de devolución de llamada que el motor de depuración (Alemania) va a usar para leer los valores de métrica.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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
 [in] Interfaz que se utiliza para la devolución de llamada de configuración.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método proporciona una interfaz para el Administrador de depuración de sesión que un evaluador de expresiones puede utilizar para leer la configuración de la métrica. Resulta útil para la depuración remota para leer las métricas en el [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] equipo.  
  
## <a name="example"></a>Ejemplo  
 Los ejemplos siguientes se muestra cómo implementar este método para un **CEE** objeto que expone la [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) interfaz.  
  
```cpp  
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
  
## <a name="see-also"></a>Vea también  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)