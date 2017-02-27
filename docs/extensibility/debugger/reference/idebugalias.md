---
title: "IDebugAlias | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAlias"
helpviewer_keywords: 
  - "Interfaz IDebugAlias"
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugAlias
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está obsoleta. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresiones administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Representa un alias de una variable numérico. Un alias es simplemente un nombre diferente para una variable.  
  
## Sintaxis  
  
```  
IDebugAlias : IUnknown  
```  
  
## Notas para los implementadores  
 El evaluador de expresiones \(EE\) implementa esta interfaz para admitir alias numéricos para las variables.  
  
## Notas para los llamadores  
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) crea un alias para un objeto determinado. Para buscar los alias, utilice [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) o [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).  
  
## Métodos en orden de Vtable  
 Los métodos siguientes se definen en el `IDebugAlias` interfaz.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Obtiene el objeto al que hace referencia este alias.|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Obtiene el nombre de alias.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Recupera un `ICorDebugValue` administrado de interfaz que proporciona acceso a información de código sobre este objeto \(sólo para el código administrado\).|  
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Marca este alias como ya no se utilizan.|  
  
## Comentarios  
 Un alias es un número decimal en forma de cadena, seguido por el carácter \#, por ejemplo, \# 1001.  
  
## Requisitos  
 Encabezado: ee.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de evaluación de expresión](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)   
 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)