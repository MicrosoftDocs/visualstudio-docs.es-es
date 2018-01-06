---
title: IDebugExpressionEvaluator2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugExpressionEvaluator2 interface
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e8ea51014ae21610b49b76fd553739c67fc4009f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexpressionevaluator2"></a>IDebugExpressionEvaluator2
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Representa una versión mejorada de un evaluador de expresiones (EE).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz se implementa mediante un evaluador de expresiones.  
  
## <a name="methods"></a>Métodos  
 Además de los métodos en el [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) interfaz, esta interfaz implementa los métodos siguientes:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|Recupera un objeto de servicio según su identificador único.|  
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|Carga previamente los módulos designados por el proveedor de símbolo especificado.|  
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|Permite que el evaluador de expresiones (EE) especificar la interfaz de devolución de llamada que el motor de depuración (Alemania) usará para leer la configuración de la métrica.|  
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Establece la ruta de acceso a common language runtime (CLR) cargado en el depurador.|  
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|Permite que un motor de depuración pasar una devolución de llamada para el evaluador de expresiones durante la inicialización.|  
|[Finalizar](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|Detiene y limpia el evaluador de expresiones.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll