---
title: "DEBUG_ADDRESS | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_ADDRESS"
helpviewer_keywords: 
  - "Estructura DEBUG_ADDRESS"
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# DEBUG_ADDRESS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta estructura representa una dirección.  
  
## Sintaxis  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```c#  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## términos  
 ulAppDomainID  
 El identificador de proceso  
  
 guidModule  
 GUID del módulo que contiene esta dirección.  
  
 tokClass  
 El token que identifica la clase o el tipo de esta dirección.  
  
> [!NOTE]
>  Este valor es específico de un proveedor de token y por consiguiente no tiene ningún significado general distinto de como identificador para un tipo de clase.  
  
 addr  
 Una estructura de [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , que contiene una combinación de estructuras que describen los tipos individuales de dirección.  el valor `addr`.`dwKind` procede de la enumeración de [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) , que explica cómo interpretar la combinación.  
  
## Comentarios  
 Esta estructura se pasa al método de [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) que se completará.  
  
 **Advertencia \[sólo C\+\+\]**  
  
 Si `addr.dwKind` es `ADDRESS_KIND_METADATA_LOCAL` y si `addr.addr.addrLocal.pLocal` no es un valor null, debe llamar a `Release` en el puntero de token:  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)