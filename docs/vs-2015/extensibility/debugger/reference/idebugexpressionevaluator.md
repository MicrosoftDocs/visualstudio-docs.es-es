---
title: IDebugExpressionEvaluator | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a198acd0ff5812c68d603c349dfa395419f88751
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49172346"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz representa el evaluador de expresiones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugExpressionEvaluator : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El evaluador debe implementar esta interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Para obtener esta interfaz, cree una instancia el evaluador de expresiones a través de la `CoCreateInstance` método utilizando el identificador de clase (CLSID) del evaluador de. Vea el ejemplo.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugExpressionEvaluator`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Analizar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Convierte una cadena de expresión en una expresión analizada.|  
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Obtiene las variables locales, argumentos y otras propiedades de un método.|  
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Convierte una ubicación de método y el desplazamiento en una dirección de memoria.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Determina el idioma que desea usar para crear resultados imprimibles.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Establece la raíz del registro. Se utiliza para la depuración en paralelo.|  
  
## <a name="remarks"></a>Comentarios  
 En una situación típica, el motor de depuración (DE), crea una instancia el evaluador de expresiones (EE) como resultado de una llamada a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Ya sabe que la del idioma y el proveedor de lo EE desea usar, la DE obtiene CLSID del EE del registro (el [aplicaciones auxiliares de SDK para depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) función, `GetEEMetric`, ayuda con esta recuperación).  
  
 Una vez que se crea una instancia de lo EE, llama la DE [analizar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para analizar la expresión y almacenarlo en una [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) objeto. Más adelante, una llamada a [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) evalúa la expresión.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra cómo crear una instancia el evaluador de expresiones proporcionado un proveedor de símbolos y la dirección en el código fuente. En este ejemplo utiliza una función, `GetEEMetric`, desde el [aplicaciones auxiliares de SDK para depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) library, dbgmetric.lib.  
  
```cpp#  
IDebugExpressionEvaluator GetExpressionEvaluator(IDebugSymbolProvider pSymbolProvider,  
                                                 IDebugAddress *pSourceAddress)  
{  
    // This is typically defined globally but is specified here just  
    // for this example.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
  
    IDebugExpressionEvaluator *pEE = NULL;  
    if (pSymbolProvider != NULL && pSourceAddress != NULL) {  
        HRESULT hr         = S_OK;  
        GUID  languageGuid = { 0 };  
        GUID  vendorGuid   = { 0 };  
  
        hr = pSymbolProvider->GetLanguage(pSourceAddress,  
                                          &languageGuid,  
                                          &vendorGuid);  
        if (SUCCEEDED(hr)) {  
            CLSID clsidEE      = { 0 };  
            CComPtr<IDebugExpressionEvaluator> spExpressionEvaluator;  
            // Get the expression evaluator's CLSID from the registry.  
            ::GetEEMetric(languageGuid,  
                          vendorGuid,  
                          metricCLSID,  
                          &clsidEE,  
                          strRegistrationRoot);  
            if (!IsEqualGUID(clsidEE,GUID_NULL)) {  
                // Instantiate the expression evaluator.  
                spExpressionEvaluator.CoCreateInstance(clsidEE);  
            }  
            if (spExpressionEvaluator != NULL) {  
                pEE = spExpressionEvaluator.Detach();  
            }  
        }  
    }  
    return pEE;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de evaluación de expresión](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [Asistentes de SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

