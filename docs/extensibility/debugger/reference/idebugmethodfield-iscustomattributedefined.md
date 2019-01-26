---
title: IDebugMethodField::IsCustomAttributeDefined | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ecb0e2c068e3ddd0aae246fe782f808c95ced52
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992326"
---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
Determina si se ha definido un atributo personalizado específico.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT IsCustomAttributeDefined(   
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```csharp  
int IsCustomAttributeDefined(  
   [In] string pszCustomAttributeName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszCustomAttributeName`  
 [in] Una cadena que contiene el nombre del atributo personalizado para buscar.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve que S_OK si el atributo personalizado se define en este método, en caso contrario, devuelve S_FALSE.  
  
## <a name="see-also"></a>Vea también  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)