---
title: 'IDebugAlias:: GetICorDebugValue | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 67ab8a7343cd320470515b757dfca905a0a4690e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156280"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera una interfaz de código administrado que representa el valor asociado a este alias.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppUnk`  
 [out] `IUnknown` interfaz que representa el valor asociado a este alias. Esta interfaz se puede consultar para la `ICorDebugValue` interfaz.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método solo se aplica a los valores administrados ( `ICorDebugValue` es una interfaz disponible en [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] y se define en el [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK del archivo Cordebug. idl).  
  
## <a name="see-also"></a>Consulte también  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
