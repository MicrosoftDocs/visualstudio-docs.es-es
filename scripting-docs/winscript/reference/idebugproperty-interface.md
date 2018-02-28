---
title: IDebugProperty (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugProperty interface
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2888a6d781ecd501128545e483971a47859d9cda
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugproperty-interface"></a>IDebugProperty (Interfaz)
Se utiliza para describir cualquier propiedad de la entidad que se está depura jerárquica que tiene un nombre, tipo y valor. Normalmente, `IDebugProperty` se utiliza para describir el resultado de evaluación de expresiones, evaluación de la instrucción o evaluation de registro.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de la `IDebugProperty` interfaz.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|Obtener el `DebugPropertyInfo` que describe este`IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|Obtiene la información extendida en una propiedad.|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|Establece el valor de una propiedad de una cadena.|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|Enumera a los miembros de una propiedad.|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|Obtiene al elemento primario de una propiedad.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: dbgprop.h