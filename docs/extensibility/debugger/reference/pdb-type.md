---
title: "PDB_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PDB_TYPE"
helpviewer_keywords: 
  - "Estructura PDB_TYPE"
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# PDB_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta estructura especifica información sobre un tipo de campo tomado de un símbolo PDB.  
  
## Sintaxis  
  
```cpp#  
typedef struct _tagTYPE_PDB {  
   ULONG32 ulAppDomainID;  
   GUID    guidModule;  
   DWORD   symid;  
} PDB_TYPE;  
```  
  
```c#  
public struct PDB_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public uint symid;  
};  
```  
  
#### Parámetros  
 ulAppDomainID  
 Identificador de la aplicación que el símbolo procede.  Se utiliza para identificar una instancia de la aplicación.  
  
 guidModule  
 GUID del módulo que contiene este campo.  
  
 symid  
 El identificador del token que corresponde a este campo.  
  
## Comentarios  
 Esta estructura aparece como parte de la combinación en la estructura de [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) cuando el campo de `dwKind` de la estructura de `TYPE_INFO` se establece en `TYPE_KIND_PDB` \(un valor de enumeración de [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) \).  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)