---
title: IDebugPointerField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d92b1b4d6efda1b8f05c594368a05bd833c9f34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705825"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz representa un tipo de puntero.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El proveedor de símbolos implementa esta interfaz para representar un puntero.  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 Use [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para obtener esta interfaz de la interfaz [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) devuelve `FIELD_TYPE_POINTER` .  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden vtable  
 Además de los métodos de las `IDebugField` interfaces y `IDebugContainerField` , esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Devuelve un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que describe el destino del puntero.|  
  
## <a name="remarks"></a>Observaciones  
 En C/C++, un puntero puede ser un contenedor si se utiliza con la notación de matriz. Por ejemplo, dado `char *pString` , `pString` tiene un tipo de puntero a `char` . `pString[3]` tiene el tipo de un contenedor que es un puntero a `char` que hace referencia al cuarto elemento de ese contenedor.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: SH. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
