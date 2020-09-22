---
title: DEBUG_ADDRESS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d001d29433573fedde3b4310f989667538b4b69c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843086"
---
# <a name="debug_address"></a>DEBUG_ADDRESS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta estructura representa una dirección.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```csharp  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## <a name="terms"></a>Términos  
 ulAppDomainID  
 El id. de proceso.  
  
 guidModule  
 GUID del módulo que contiene esta dirección.  
  
 tokClass  
 Token que identifica la clase o el tipo de esta dirección.  
  
> [!NOTE]
> Este valor es específico de un proveedor de símbolos y, por lo tanto, no tiene ningún significado general que no sea un identificador de un tipo de clase.  
  
 addr  
 Estructura de [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) , que contiene una Unión de estructuras que describen los tipos de direcciones individuales. El valor `addr` .`dwKind` procede de la enumeración [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) , que explica cómo interpretar la Unión.  
  
## <a name="remarks"></a>Notas  
 Esta estructura se pasa al método [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) que se va a rellenar.  
  
 **ADVERTENCIA [solo C++]**  
  
 Si `addr.dwKind` es `ADDRESS_KIND_METADATA_LOCAL` y si `addr.addr.addrLocal.pLocal` no es un valor nulo, debe llamar a `Release` en el puntero de token:  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: SH. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetAddress (](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
