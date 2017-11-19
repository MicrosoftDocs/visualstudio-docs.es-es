---
title: IDebugCustomViewer::DisplayValue | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomViewer::DisplayValue
helpviewer_keywords: IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 701c5e33273dc6d00156e554e1abaa9a003568eb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Se llama a este método para mostrar el valor especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT DisplayValue(  
   HWND             hwnd,  
   DWORD            dwID,  
   IUnknown *       pHostServices,  
   IDebugProperty3* pDebugProperty);  
);  
```  
  
```csharp  
int DisplayValue(  
   IntPtr          hwnd,   
   uint            dwID,   
   object          pHostServices,   
   IDebugProperty3 pDebugProperty  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `hwnd`  
 [in] Ventana primaria  
  
 `dwID`  
 [in] Id. de los visores personalizados que admiten más de un tipo.  
  
 `pHostServices`  
 [in] Reservado. Siempre se establece en null.  
  
 `pDebugProperty`  
 [in] Interfaz que puede usarse para recuperar el valor que se muestre.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve el código de error.  
  
## <a name="remarks"></a>Comentarios  
 La pantalla es "modal", puesto que este método crear la ventana es necesaria, mostrar el valor, esperar la entrada y cerrar la ventana, todos antes de devolver al llamador. Esto significa que el método debe controlar todos los aspectos de mostrar el valor de propiedad, desde la creación de una ventana de salida, a la espera de entrada del usuario, para destruir la ventana.  
  
 Para admitir el cambio del valor en el dado [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) objeto, puede usar el [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) método: si el valor se puede expresar como una cadena. En caso contrario, es necesario crear una interfaz personalizada, exclusivo para el evaluador de expresiones esta implementación `DisplayValue` (método), en el mismo objeto que implementa el `IDebugProperty3` interfaz. Esta interfaz personalizada podría proporcionar métodos para cambiar los datos de un tamaño arbitrario o complejidad.  
  
## <a name="see-also"></a>Vea también  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)