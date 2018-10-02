---
title: IDebugTypeFieldBuilder2::CreateArrayOfType | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugTypeFieldBuilder2::CreateArrayOfType
- CreateArrayOfType
ms.assetid: 85166ac9-0bff-49a0-b2fd-ca7f7a8eae4b
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0c652d4ddf80a7ae07159bedea49c816e6e380a8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575832"
---
# <a name="idebugtypefieldbuilder2createarrayoftype"></a>IDebugTypeFieldBuilder2::CreateArrayOfType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugTypeFieldBuilder2::CreateArrayOfType](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype).  
  
Crea una matriz del tipo especificado y el tamaño.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT CreateArrayOfType (  
   IDebugField*  pTypeField,  
   DWORD         rank,  
   IDebugField** pArrayOfTypeField  
);  
```  
  
```csharp  
int CreateArrayOfType (  
   IDebugField     pTypeField,  
   uint            rank,  
   out IDebugField pArrayOfTypeField  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pTypeField`  
 [in] Tipo de elementos que se va a contener la matriz.  
  
 `rank`  
 [in] Número de elementos de la matriz.  
  
 `pArrayOfTypeField`  
 [out] Devuelve el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objetos que representan la nueva matriz.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)

