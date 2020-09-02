---
title: 'IDebugProgram2:: Getdebugproperty (| Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29b86a1aa144e553b126445a865330a8edb786ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187906"
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
 enuncia Devuelve un objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que representa las propiedades del programa.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Observaciones  
 Las propiedades devueltas por este método son específicas del programa. Si el programa necesita devolver más de una propiedad, el objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) devuelto por este método es un contenedor de propiedades adicionales y al llamar al método [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) se devuelve una lista de todas las propiedades.  
  
 Un programa puede exponer cualquier número y tipo de propiedades adicionales que se pueden describir a través de la `IDebugProperty2` interfaz. Un IDE puede mostrar las propiedades del programa adicional a través de una interfaz de usuario del explorador de propiedades genérica.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
