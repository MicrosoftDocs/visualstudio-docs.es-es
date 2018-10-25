---
title: ADDRESS_KIND | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 40a1473fce75e8b54ca65fd84c5dbb68c3c7d682
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923074"
---
# <a name="addresskind"></a>ADDRESS_KIND
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
 Una dirección nativa, representada por la [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) estructura.  
  
 ADDRESS_KIND_UNMANAGED_THIS_RELATIVE  
 Una dirección no administrada respecto a un `this` (`Me` en Visual Basic) puntero y representado por la [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) estructura.  
  
 ADDRESS_KIND_UNMANAGED_PHYSICAL  
 Una dirección física no administrada, representada por la [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) estructura.  
  
 ADDRESS_KIND_METHOD  
 Un método de una clase, representado por la [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) estructura.  
  
 ADDRESS_KIND_FIELD  
 Un campo de una clase, representado por la [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) estructura.  
  
 ADDRESS_KIND_LOCAL  
 La dirección es una variable local y se representa mediante el [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) estructura.  
  
 ADDRESS_KIND_PARAM  
 Un parámetro de método o función, representado por la [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) estructura.  
  
 ADDRESS_KIND_ARRAYELEM  
 Un elemento de matriz, representado por la [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) estructura.  
  
 ADDRESS_KIND_RETVAL  
 Un valor devuelto, representado por la [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) estructura.  
  
## <a name="remarks"></a>Comentarios  
 El [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) método devuelve el [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) estructura que contiene una unión de las posibles estructuras, la [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) estructura. El `dwKind` campo de la `DEBUG_ADDRESS_UNION` estructura contiene el `ADDRESS_KIND` de valor y se describe cómo interpretar el campo union.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)

