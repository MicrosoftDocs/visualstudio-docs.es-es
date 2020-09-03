---
title: 'IDebugProcess3:: GetEngineFilter | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetEngineFilter
- IDebugProcess3::GetEngineFilter
ms.assetid: ccb7ecb0-f189-4e80-b5b2-221a095e01f5
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9ebcec7a26bac7126d97c14f330664924da959cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200985"
---
# <a name="idebugprocess3getenginefilter"></a>IDebugProcess3::GetEngineFilter
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera una matriz de identificadores únicos para los motores de depuración disponibles.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetEngineFilter(  
   GUID_ARRAY *pEngineArray  
);  
```  
  
```csharp  
public int GetEngineFilter(  
   out GUID_ARRAY[] pEngineArray  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pEngineArray`  
 enuncia Referencia a una estructura que contiene identificadores únicos para los motores de depuración.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md)
