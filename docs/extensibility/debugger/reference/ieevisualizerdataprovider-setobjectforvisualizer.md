---
title: IEEVisualizerDataProvider::SetObjectForVisualizer | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: feb48452b466301f7987db613997158aed160bac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Este método cambia el objeto que representa el visualizador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```csharp  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pNewObject`  
 [in] Objeto que se va a establecer.  
  
 `error`  
 [out] Si se produjo un error al configurar el objeto, esta cadena contiene el mensaje de error.  
  
 `pException`  
 [out] Si se produjo un error, este objeto contiene la información de excepción.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Es responsabilidad del implementador para determinar cómo se devuelve la información de error. Sin embargo, es posible que algunos llamadores pueden solo vistazo para ver si se devuelve un objeto de excepción para que sepan que hay produjo un error, por lo que este método siempre debe devolver un objeto de excepción si se produjo un error. También se debe proporcionar la cadena de error en caso de que el llamador desea hacer uso de ella.  
  
## <a name="see-also"></a>Vea también  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)