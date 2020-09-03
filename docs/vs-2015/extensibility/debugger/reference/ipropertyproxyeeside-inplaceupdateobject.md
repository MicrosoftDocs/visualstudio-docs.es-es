---
title: 'IPropertyProxyEESide:: InPlaceUpdateObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c91497815dd18dc138b2eadc462c43785830a033
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199519"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Actualiza los datos del objeto con el objeto de datos especificado y devuelve un nuevo objeto de datos que representa los datos nuevos del objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT InPlaceUpdateObject(  
   [in] IEEDataStorage*   dataIn,  
   [out] IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int InPlaceUpdateObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dataIn`  
 de Un objeto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) que contiene los nuevos datos.  
  
 `dataOut`  
 enuncia Devuelve un nuevo `IEEDataStorage` objeto que contiene los datos reemplazados.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Observaciones  
 En realidad, este método actualiza los datos del objeto. No es necesario que los datos del objeto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) devuelto sean los mismos que los datos del objeto entrante `IEEDataStorage` , pero el objeto devuelto debe reflejar el valor actual de la propiedad.  
  
 El objeto de datos de entrada no suele ser implementado por EE. Sin embargo, el objeto devuelto por este método siempre se implementa mediante el, que permite a EE implementar la `IEEDataStorage` interfaz en cualquier clase deseada.  
  
 El método [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) crea un objeto de datos basado en el objeto de datos de entrada, pero no afecta a los datos originales de la propiedad.  
  
## <a name="see-also"></a>Consulte también  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
