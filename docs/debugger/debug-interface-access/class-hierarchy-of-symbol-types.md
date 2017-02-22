---
title: "Jerarqu&#237;a de clases de tipos de s&#237;mbolos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "símbolos [SDK de DIA], jerarquías de clase"
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Jerarqu&#237;a de clases de tipos de s&#237;mbolos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La tabla siguiente se describen los tipos de símbolo en la jerarquía de clases.  
  
## Tipos de símbolos  
  
|Tipo de símbolo|Descripción|  
|---------------------|-----------------|  
|[UDT](../../debugger/debug-interface-access/udt.md)|Símbolo utilizado para representar cada clase, estructura, y union.|  
|[Enumeración \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|símbolo para los tipos enumerados.|  
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|símbolo para los tipos de puntero.|  
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|símbolo para los tipos de matriz.|  
|[BaseType](../../debugger/debug-interface-access/basetype.md)|símbolo para los tipos base|  
|[Typedef \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|Símbolo que presenta los nombres para otros tipos.|  
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|símbolo utilizado para cada clase base de un tipo definido por el usuario \(UDT\).|  
|[Friend \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Símbolos para las clases de confianza y las funciones friend.|  
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|símbolo para cada firma única de la función.|  
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|símbolo para cada parámetro a una función.|  
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|Token del tamaño de la tabla virtual.|  
|[VTable](../../debugger/debug-interface-access/vtable.md)|símbolo para una tabla virtual.|  
|[CustomType](../../debugger/debug-interface-access/customtype.md)|Token del tipo proveedor\-definido.|  
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|Símbolo de un tipo definido en metadatos.|  
|[Dimensión](../../debugger/debug-interface-access/dimension.md)|Símbolo para las dimensiones de la matriz.|  
  
> [!NOTE]
>  Cada token puede tener propiedades que información de bloqueo sobre el símbolo, así como referencias a otros símbolos.  Estas propiedades se muestran en temas individuales de símbolos.  
  
## Vea también  
 [CV\_access\_e \(Enumeración\)](../../debugger/debug-interface-access/cv-access-e.md)   
 [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Símbolos y etiquetas de símbolo](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)