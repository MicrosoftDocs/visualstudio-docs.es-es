---
title: 'IDebugField:: Equal | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa630a6f2084f7ff79a9c89b685658cf694fcab9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547317"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método compara el campo con el campo especificado para determinar si son iguales.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```csharp  
int Equal(  
   IDebugField pField  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pField`  
 de Campo que se va a comparar con este.  
  
## <a name="return-value"></a>Valor devuelto  
 Si los campos son iguales, devuelve `S_OK` . Si los campos son diferentes, devuelve `S_FALSE.` en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
