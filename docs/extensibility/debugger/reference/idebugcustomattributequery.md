---
title: IDebugCustomAttributeQuery ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
ms.assetid: b804b619-70eb-4c38-80d9-c8b32b65ed3e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 598db5ad711c8b61339e188311c1a437a24d013c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732611"
---
# <a name="idebugcustomattributequery"></a>IDebugCustomAttributeQuery
Representa una consulta de atributos personalizados en un método o tipo.

## <a name="syntax"></a>Sintaxis

```
IDebugCustomAttributeQuery : IUnknown
```

## <a name="methods"></a>Métodos
 Esta interfaz implementa los métodos siguientes:

|Método|Descripción|
|------------|-----------------|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery-getcustomattributebyname.md)|Recupera un atributo personalizado dado su nombre.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery-iscustomattributedefined.md)|Determina en el atributo personalizado especificado se define.|

## <a name="requirements"></a>Requisitos
 Encabezado: Sh.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
