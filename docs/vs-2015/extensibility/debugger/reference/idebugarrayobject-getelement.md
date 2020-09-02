---
title: 'IDebugArrayObject:: GetElement | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac59a14a2d3be06c9e1523bcdc0d0ad026e0a7d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423691"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene un elemento de la matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetElement(   
   DWORD          dwIndex,  
   IDebugObject** ppElement  
);  
```  
  
```csharp  
int GetElement(  
   [In] uint dwIndex,   
   out IDebugObject ppElement  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwIndex`  
 de Índice del elemento.  
  
 `ppElement`  
 enuncia Devuelve una interfaz [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa el elemento.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método ve todos los elementos de un objeto de matriz como una matriz unidimensional, incluso si el objeto de matriz es multidimensional. Por ejemplo, dada la matriz `myarray[3][2][6]` y un `dwIndex` parámetro de 20, este método devolverá el elemento de y `myarray[1][1][2]` un `dwIndex` parámetro de 21 devolverá el elemento de `myarray[1][1][3]` . Use el método [getCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) para determinar el número total de elementos de la matriz.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
