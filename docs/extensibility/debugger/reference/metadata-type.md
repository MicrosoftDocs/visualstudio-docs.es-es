---
title: "METADATA_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_TYPE"
helpviewer_keywords: 
  - "Estructura METADATA_TYPE"
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# METADATA_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta estructura especifica información sobre un tipo de campo que se toman de metadatos.  
  
## Sintaxis  
  
```cpp#  
typedef struct _tagTYPE_METADATA {  
   ULONG32  ulAppDomainID;  
   GUID     guidModule;  
   _mdToken tokClass;  
} METADATA_TYPE;  
```  
  
```c#  
public struct METADATA_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public int  tokClass;  
};  
```  
  
#### Parámetros  
 ulAppDomainID  
 Identificador de la aplicación del que proviene el símbolo. Esto se utiliza para identificar de forma exclusiva una instancia de la aplicación.  
  
 guidModule  
 El GUID del módulo que contiene este campo.  
  
 tokClass  
 El identificador del token de metadatos de este tipo.  
  
 \[C\+\+\] `_mdToken` es un `typedef` de 32 bits `int`.  
  
## Comentarios  
 Esta estructura aparece como parte de la unión en el [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) estructura cuando el `dwKind` campo de la `TYPE_INFO` estructura se establece en `TYPE_KIND_METADATA` \(un valor de la [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) \(enumeración\)\).  
  
 El `tokClass` valor es un símbolo \(token\) de metadatos que identifica un tipo. Para obtener más información sobre cómo interpretar los bits superiores del identificador de token de metadatos, consulte la `CorTokenType` \(enumeración\) en el archivo corhdr.h el [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK.  
  
## Requisitos  
 Encabezado: sh.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)