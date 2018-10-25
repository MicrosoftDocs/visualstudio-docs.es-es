---
title: IDebugProgram2::GetDebugProperty | Documentos de Microsoft
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
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 870c4e80b6fa942ff3dc950376039fc7a7d84ac3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919629"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene las propiedades del programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```csharp  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppProperty`  
 [out] Devuelve un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto que representa las propiedades del programa.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Las propiedades que devuelve este método son específicas del programa. Si el programa necesita devolver más de una propiedad, el [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto devuelto por este método es un contenedor de propiedades adicionales y una llamada a la [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) método devuelve un lista de todas las propiedades.  
  
 Un programa puede exponer cualquier número y tipo de propiedades adicionales que se pueden describir mediante el `IDebugProperty2` interfaz. Un IDE puede mostrar las propiedades adicionales del programa mediante una interfaz de usuario del explorador de propiedades genéricas.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)

