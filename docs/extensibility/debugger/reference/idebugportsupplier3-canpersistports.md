---
title: IDebugPortSupplier3::CanPersistPorts | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad31d015048d8e0732c32652141b7be060628663
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918020"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método determina si el proveedor del puerto puede conservar los puertos (escribiéndolas en el disco) entre las distintas invocaciones del depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```csharp  
int CanPersistPorts();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Ninguno.  
  
## <a name="return-value"></a>Valor devuelto  
 `S_OK` Si se pueden conservar los puertos, o `S_FALSE` para indicar que no se pueden conservar los puertos.  
  
## <a name="remarks"></a>Comentarios  
 Si el proveedor del puerto puede persistir los puertos, debe hacerlo cuando se destruye y, a continuación, volver a cargarlos cuando se crean instancias de una vez más.  
  
## <a name="see-also"></a>Vea también  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
