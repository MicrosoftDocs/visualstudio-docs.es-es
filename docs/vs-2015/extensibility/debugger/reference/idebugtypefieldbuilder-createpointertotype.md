---
title: 'IDebugTypeFieldBuilder:: CreatePointerToType | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- CreatePointerToType
- IDebugTypeFieldBuilder::CreatePointerToType
ms.assetid: 73966e8a-b643-43e0-9b4e-0aa4b402ebbe
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: af549b9b5bb7c70ab8ae9e685c9335836ae757ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202285"
---
# <a name="idebugtypefieldbuildercreatepointertotype"></a>IDebugTypeFieldBuilder::CreatePointerToType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un puntero al tipo especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT CreatePointerToType(  
   IDebugField*  pTypeField,  
   IDebugField** pPtrToTypeField  
);  
```  
  
```csharp  
int CreatePointerToType(  
   IDebugField     pTypeField,  
   out IDebugField pPtrToTypeField  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pTypeField`  
 de Tipo que se va a señalar. Se representa mediante la interfaz [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
 `pPtrToTypeField`  
 enuncia Devuelve el puntero representado por un nuevo objeto **IDebugField** .  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)
