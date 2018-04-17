---
title: IDebugAlias2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 15fbf639c15e62b19e112ad140517f096d49f9d4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Representa un alias para una variable numérico y permite a un evaluador de expresiones (EE) para obtener el dominio de aplicación para el alias.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugAlias2 : IDebugAlias  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz se implementa mediante el motor de depuración administrado (Alemania).  
  
## <a name="methods"></a>Métodos  
 Además de los métodos en el [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interfaz, esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Recupera el identificador para el dominio de aplicación.|  
  
## <a name="remarks"></a>Comentarios  
 Un alias es un número decimal en forma de cadena seguido por el carácter #, por ejemplo, 1001#.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll