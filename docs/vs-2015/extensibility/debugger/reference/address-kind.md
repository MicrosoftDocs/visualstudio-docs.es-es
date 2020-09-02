---
title: ADDRESS_KIND | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6152ff5f493134812916f28e0b908bf98ecdbb35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62561878"
---
# <a name="address_kind"></a>ADDRESS_KIND
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica los tipos de direcciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
typedef DWORD ADDRESS_KIND;  
```  
  
```csharp  
public enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
```  
  
## <a name="terms"></a>Términos  
 ADDRESS_KIND_NATIVE  
 Una dirección nativa, representada por la estructura [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) .  
  
 ADDRESS_KIND_UNMANAGED_THIS_RELATIVE  
 Una dirección no administrada relativa a un `this` `Me` puntero (en Visual Basic) y representada por la estructura de [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) .  
  
 ADDRESS_KIND_UNMANAGED_PHYSICAL  
 Dirección física no administrada, representada por la estructura [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) .  
  
 ADDRESS_KIND_METHOD  
 Método de una clase, representado por la estructura [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) .  
  
 ADDRESS_KIND_FIELD  
 Campo de una clase, representado por la estructura [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) .  
  
 ADDRESS_KIND_LOCAL  
 La dirección es para una variable local y se representa mediante la estructura [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) .  
  
 ADDRESS_KIND_PARAM  
 Un método o parámetro de función, representado por la estructura [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) .  
  
 ADDRESS_KIND_ARRAYELEM  
 Elemento de matriz, representado por la estructura [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) .  
  
 ADDRESS_KIND_RETVAL  
 Valor devuelto, representado por la estructura de [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) .  
  
## <a name="remarks"></a>Comentarios  
 El método [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) devuelve el [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) estructura que contiene una Unión de estructuras posibles, la estructura de [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) . El `dwKind` campo de la `DEBUG_ADDRESS_UNION` estructura contiene el `ADDRESS_KIND` valor y describe cómo interpretar el campo de Unión.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: SH. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetAddress (](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
