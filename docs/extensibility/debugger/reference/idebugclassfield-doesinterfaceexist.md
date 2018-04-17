---
title: IDebugClassField::DoesInterfaceExist | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a7c4a09af356951e7e26b6c9b6b0af5922b9f53b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
Determina si se define una interfaz específica en la clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT DoesInterfaceExist(   
   LPCOLESTR pszInterfaceName  
);  
```  
  
```csharp  
int DoesInterfaceExist(  
   [In] string pszInterfaceName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszInterfaceName`  
 [in] Una cadena que contiene el nombre de la interfaz para buscar.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK, devuelva S_FALSE si la interfaz no existe; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 En efecto, este método obtiene una enumeración de todas las interfaces y busca en la lista para una interfaz de búsqueda de coincidencias.  
  
## <a name="see-also"></a>Vea también  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)