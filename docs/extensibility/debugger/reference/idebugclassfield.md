---
title: IDebugClassField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField
helpviewer_keywords:
- IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 681a426cc95ead710fbb8dab151bb5a23b6f1206
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62922601"
---
# <a name="idebugclassfield"></a>IDebugClassField
Esta interfaz representa una clase como un tipo.

## <a name="syntax"></a>Sintaxis

```
IDebugClassField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de símbolos implementa esta interfaz en el mismo objeto que implementa el [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaz. Esta interfaz es una especialización que representa un tipo de clase.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Un número de interfaces tiene métodos que pueden devolver esta interfaz, incluido [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), y [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md). Además, puede usar [QueryInterface](/cpp/atl/queryinterface) para obtener esta interfaz desde el [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaz si el [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) método devuelve la marca `FIELD_TYPE_CLASS`.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos en el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) y [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaces, esta interfaz implementa lo siguiente:

|Método|Descripción|
|------------|-----------------|
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|Crea un enumerador para las clases base de esta clase.|
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|Determina si se define una interfaz específica en la clase.|
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Crea un enumerador para las clases anidadas de esta clase.|
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Obtiene la clase que contiene esta clase.|
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|Crea un enumerador para las interfaces implementadas por esta clase.|
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Crea un enumerador para los constructores de esta clase.|
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Obtiene el nombre del indizador predeterminado.|
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Crea un enumerador para los enumeradores anidados de esta clase.|

## <a name="requirements"></a>Requisitos
 Encabezado: sh.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)