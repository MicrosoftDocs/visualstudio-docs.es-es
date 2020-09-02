---
title: IDebugContainerField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2656d3f5a3313a4538e3e0e6454dd671da635904
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686971"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz representa un símbolo o tipo que es un contenedor para otros símbolos o tipos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugContainerField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un proveedor de símbolos implementa esta interfaz en el mismo objeto que implementa la interfaz [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) . Esta interfaz también es la clase base para todas las interfaces que representan contenedores.  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 Muchos métodos de muchas interfaces devuelven esta interfaz. Dado que se trata de una clase base para todos los contenedores, las interfaces más especializadas se pueden obtener de esta interfaz mediante [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3). Estas interfaces incluyen [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)y [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos de la interfaz [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Crea un enumerador para los campos del contenedor.|  
  
## <a name="remarks"></a>Observaciones  
 Las matrices (contenedores para variables), las clases (contenedores de métodos y variables) y los métodos (contenedores para parámetros y variables locales) son ejemplos de contenedores.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: SH. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
