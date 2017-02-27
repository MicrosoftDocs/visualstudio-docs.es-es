---
title: "IDebugClassField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField"
helpviewer_keywords: 
  - "Interfaz IDebugClassField"
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugClassField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

esta interfaz representa una clase como tipo.  
  
## Sintaxis  
  
```  
IDebugClassField : IDebugContainerField  
```  
  
## Notas para los implementadores  
 Un proveedor de token implementa esta interfaz en el mismo objeto que implementa la interfaz de [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) .  esta interfaz es una especialización que representa un tipo de clase.  
  
## Notas para los llamadores  
 Varias interfaces tienen métodos que pueden devolver esta interfaz incluidos [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), y [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md).  Además, puede utilizar [QueryInterface](/visual-cpp/atl/queryinterface) para obtener esta interfaz de la interfaz de [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) si el método de [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) devuelve el marcador `FIELD_TYPE_CLASS`.  
  
## métodos en el orden de Vtable  
 Además de los métodos de las interfaces de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) y de [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) , esta interfaz implementa lo siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|Crea un enumerador para las clases base de esta clase.|  
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|Determina si una interfaz concreto está definido en la clase.|  
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Crea un enumerador para las clases anidadas de esta clase.|  
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Obtiene la clase envolvente esta clase.|  
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|Crea un enumerador para las interfaces implementadas por esta clase.|  
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Crea un enumerador para los constructores de esta clase.|  
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Obtiene el nombre del indizador predeterminado.|  
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Crea un enumerador para los enumeradores anidada de esta clase.|  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)