---
title: 'IDebugMethodField:: GetThis | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 786f3986875518470ed5756a0f7b57f4f93f5ca2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62563616"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene el `this` `Me` puntero (en [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] ) del objeto que contiene el método.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetThis(   
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetThis(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppClass`  
 enuncia Devuelve un objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que representa el puntero "this".  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 En los lenguajes orientados a objetos, suele haber un puntero implícito a la creación de instancias actual de una clase. Esto se conoce como `this` en C#/c + + y como `Me` en [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .  
  
## <a name="see-also"></a>Consulte también  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
