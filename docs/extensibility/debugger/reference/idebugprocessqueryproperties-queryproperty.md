---
title: IDebugProcessQueryProperties::QueryProperty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessQueryProperties::QueryProperty
ms.assetid: 9a91707d-a590-44ef-b122-69d9816a7a79
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a2ff40f850186e97888fd409d2387e15873851b7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893954"
---
# <a name="idebugprocessquerypropertiesqueryproperty"></a>IDebugProcessQueryProperties::QueryProperty
Consultas de este método para un valor de propiedad especificado al proceso de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT QueryProperty(  
   PROCESS_PROPERTY_TYPE  dwPropType,  
   VARIANT               *pvarPropValue);  
```  
  
```csharp  
int QueryProperty(  
   enum_PROCESS_PROPERTY_TYPE dwPropType,  
   out object                 pvarPropValue);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwPropType`  
 [in] Definición de la propiedad de consulta. Los valores son:  
  
- PROCESS_PROPERTY_COMMAND_LINE = 1  
  
- PROCESS_PROPERTY_CURRENT_DIRECTORY = 2  
  
- PROCESS_PROPERTY_ENVIRONMENT_VARIABLES = 3  
  
  `pvarPropValue`  
  [out] El valor de la propiedad.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método se usa en contadas ocasiones.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcessQueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties.md)