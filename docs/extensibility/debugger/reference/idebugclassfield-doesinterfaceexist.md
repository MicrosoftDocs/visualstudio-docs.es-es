---
title: IDebugClassField::DoesInterfaceExist | Documentos de Microsoft
ms.date: 11/04/2016
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
ms.openlocfilehash: 8d54afbe331eaf80fedb2dc102f831fcc616fde7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53871361"
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
 [in] Una cadena que contiene el nombre de la interfaz que se busca.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK, devuelve S_FALSE si no existe la interfaz; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 En efecto, este método obtiene una enumeración de todas las interfaces y busca en la lista para una interfaz de búsqueda de coincidencias.  
  
## <a name="see-also"></a>Vea también  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)