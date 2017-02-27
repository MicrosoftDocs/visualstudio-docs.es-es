---
title: "IDebugAlias2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaz IDebugAlias2"
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugAlias2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está obsoleta. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresiones administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Representa un alias de una variable numérico y permite a un evaluador de expresiones \(EE\) para obtener el dominio de aplicación para el alias.  
  
## Sintaxis  
  
```  
IDebugAlias2 : IDebugAlias  
```  
  
## Notas para los implementadores  
 Esta interfaz se implementa mediante el motor de depuración administrado \(DE\).  
  
## Métodos  
 Además de los métodos en el [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Recupera el identificador del dominio de aplicación.|  
  
## Comentarios  
 Un alias es un número decimal en forma de cadena, seguido por el carácter \#, por ejemplo, \# 1001.  
  
## Requisitos  
 Encabezado: Ee.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll