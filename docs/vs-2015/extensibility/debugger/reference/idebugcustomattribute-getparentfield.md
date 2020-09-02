---
title: 'IDebugCustomAttribute:: GetParentField | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7b6d6ceadc8ee0dc6099d6463a75f1c792837e81
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62569581"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene el campo al que está asociado el atributo personalizado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetParentField(   
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetParentField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppField`  
 enuncia Devuelve el objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa el campo al que está asociado el atributo personalizado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Llame al método [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) en el objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) devuelto para determinar el tipo de campo del elemento primario.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
