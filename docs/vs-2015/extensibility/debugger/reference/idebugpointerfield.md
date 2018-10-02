---
title: IDebugPointerField | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e8dd3e0a817de4b86bc6fae83bcdfa88d510c953
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576269"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugPointerField](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugpointerfield).  
  
Esta interfaz representa un tipo de puntero.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El proveedor de símbolos implementa esta interfaz para representar un puntero.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Use [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para obtener esta interfaz desde el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaz si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) devuelve `FIELD_TYPE_POINTER`.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos en el `IDebugField` y `IDebugContainerField` interfaces, esta interfaz se implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Devuelve un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que describe el destino del puntero.|  
  
## <a name="remarks"></a>Comentarios  
 En C/C ++, un puntero puede ser un contenedor si se usa con la notación de matriz. Por ejemplo, dada `char *pString`, `pString` tiene un tipo de puntero a `char`. `pString[3]` tiene el tipo de un contenedor que es un puntero a `char` que hace referencia al cuarto elemento de ese contenedor.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)

