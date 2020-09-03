---
title: 'IDebugModule2:: GetInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 476ffb2901dfe6a8d09ca707fc47089f4d99d97d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162498"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene información acerca de este módulo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetInfo(   
   MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO*       pInfo  
);  
```  
  
```cpp#  
int GetInfo(   
   enum_MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO[]           pInfo  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwFields`  
 de Combinación de marcas de la enumeración [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) que especifican los campos de que `pInfo` se van a rellenar.  
  
 `pInfo`  
 [in, out] [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) estructura que se rellena con una descripción del módulo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La estructura [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) contiene el nombre del módulo que se muestra en la ventana **módulos** .  
  
## <a name="see-also"></a>Consulte también  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
