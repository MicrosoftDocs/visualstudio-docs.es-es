---
title: 'IDebugBinder3:: FindAlias | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 47aaaec73d2c364e974b7430335404bf8caf406c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68142961"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método busca un alias, dado un nombre. Se buscarán todos los alias del programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pcstrName`  
 de Nombre del alias que se va a buscar.  
  
 `ppAlias`  
 enuncia Alias encontrado (si existe) representado por la interfaz [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) .  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve `S_FALSE` (si no se encuentra el alias) o un código de error.  
  
## <a name="remarks"></a>Observaciones  
 Este método inicializa el objeto de destino en NULL antes de llamar a; después, prueba un valor NULL después para determinar si se encontró o no el alias.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
