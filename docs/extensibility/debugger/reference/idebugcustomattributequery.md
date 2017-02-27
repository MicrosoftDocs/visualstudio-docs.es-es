---
title: "IDebugCustomAttributeQuery | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaz IDebugCustomAttributeQuery"
ms.assetid: b804b619-70eb-4c38-80d9-c8b32b65ed3e
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugCustomAttributeQuery
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

representa una consulta para los atributos personalizados en un método o un tipo.  
  
## Sintaxis  
  
```  
IDebugCustomAttributeQuery : IUnknown  
```  
  
## Métodos  
 Esta interfaz implementa los siguientes métodos:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery-getcustomattributebyname.md)|Recupera un atributo personalizado con su nombre.|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery-iscustomattributedefined.md)|determina en el atributo personalizado especificado es definido.|  
  
## Requisitos  
 encabezado: Sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll