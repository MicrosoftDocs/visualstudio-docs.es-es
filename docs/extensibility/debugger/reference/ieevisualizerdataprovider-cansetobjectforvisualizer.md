---
title: IEEVisualizerDataProvider::CanSetObjectForVisualizer | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEVisualizerDataProvider::CanSetObjectForVisualizer
helpviewer_keywords: IEEVisualizerDataProvider::CanSetObjectForVisualizer method
ms.assetid: 70fd3c6f-2f82-43a3-993b-c1dc8aa080bf
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1aff8b59e92099ece226f4608b50bd093ca94f4e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ieevisualizerdataprovidercansetobjectforvisualizer"></a>IEEVisualizerDataProvider::CanSetObjectForVisualizer
Este método determina si el visualizador puede tener el objeto de datos que representa actualizado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CanSetObjectForVisualizer(  
   BOOL* b  
);  
```  
  
```csharp  
int CanSetObjectForVisualizer(  
   out int b  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `b`  
 [out] Es distinto de cero (`TRUE`) si el objeto en el visualizador puede actualizarse, es cero (`FALSE`) si no es posible.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Un objeto no sea modificable si está enlazada a la memoria de sólo lectura, por ejemplo.  
  
## <a name="see-also"></a>Vea también  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)