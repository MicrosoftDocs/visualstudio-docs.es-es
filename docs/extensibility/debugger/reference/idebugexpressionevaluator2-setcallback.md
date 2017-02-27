---
title: "IDebugExpressionEvaluator2::SetCallback | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator2::SetCallback"
  - "SetCallback"
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionEvaluator2::SetCallback
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Permite al evaluador \(EE\) de expresiones para especificar la interfaz de devolución de llamada que el motor del \(DE\) depurador usará para leer valores métrica.  
  
## Sintaxis  
  
```cpp#  
HRESULT SetCallback (  
   IDebugSettingsCallback2* pCallback  
);  
```  
  
```c#  
int SetCallback (  
   IDebugSettingsCallback2 pCallback  
);  
```  
  
#### Parámetros  
 `pCallback`  
 \[in\]  Interfaz a utilizar para la devolución de valores.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método proporciona una interfaz al administrador de depuración de la sesión que un evaluador de expresiones puede utilizar para leer valores métrica.  Es útil en la depuración remota leer métricas en el equipo de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  
  
## Ejemplo  
 Los ejemplos siguientes se muestra cómo implementar este método para un objeto **de la repetición** que expone la interfaz de [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) .  
  
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
  
## Vea también  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)