---
title: IDebugPointerField | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 82656209181d02aa6514def10af1cff17ae1bcf5
ms.lasthandoff: 04/05/2017

---
# <a name="idebugpointerfield"></a>IDebugPointerField
Esta interfaz representa un tipo de puntero.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El proveedor de símbolos implementa esta interfaz para representar un puntero.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Use [QueryInterface](/cpp/atl/queryinterface) para obtener esta interfaz desde el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaz si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) devuelve `FIELD_TYPE_POINTER`.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos en el `IDebugField` y `IDebugContainerField` interfaces, esta interfaz se implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Devuelve un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que describe el destino del puntero.|  
  
## <a name="remarks"></a>Comentarios  
 En C o C++, un puntero puede ser un contenedor si se utiliza con una notación de matriz. Por ejemplo, si tenemos `char *pString`, `pString` tiene un tipo de puntero a `char`. `pString[3]`tiene el tipo de un contenedor que es un puntero a `char` que hace referencia el cuarto elemento de ese contenedor.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
