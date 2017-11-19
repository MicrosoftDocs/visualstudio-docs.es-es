---
title: IDebugClassField::DoesInterfaceExist | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField::DoesInterfaceExist
helpviewer_keywords: IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 07a4760064003a45af55aa747192e044edca8e0c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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