---
title: IPropertyProxyEESide::GetManagedViewerCreationData | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 47ae1c724542d628e7f3c047efd8ed2da1f6f1f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31124761"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Recupera información sobre el Visor para este tipo de propiedad con el fin de crear una instancia de ese visor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetManagedViewerCreationData(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  className,  
   ASSEMBLYLOCRESOLUTION* alr,  
   BOOL*                  replacementOk  
);  
```  
  
```csharp  
int GetManagedViewerCreationData(  
   out string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     className,  
   out enum_ASSEMBLYLOCRESOLUTION alr,  
   out int                        replacementOk  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `assemName`  
 [out] Devuelve el nombre del ensamblado que contiene este objeto.  
  
 `assemBytes`  
 [out] Devuelve un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto que contiene los bytes de ensamblado de este objeto (este es un valor null si no hay disponibles).  
  
 `assemPdb`  
 [out] Devuelve un `IEEDataStorage` objeto que contiene el símbolo de almacena información para este objeto (este es un valor null si no hay ningún almacén de símbolos).  
  
 `className`  
 [out] Devuelve el nombre de clase que contiene este objeto.  
  
 `alr`  
 [out] Devuelve un valor de la [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) enumeración que indica la ubicación del ensamblado.  
  
 `replacementOk`  
 [out] Devuelve un valor distinto de cero (`TRUE`) si se puede cambiar el valor de este objeto; cero (`FALSE`) si el objeto es de solo lectura.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método se usa por los visualizadores de tipo para crear un visor administrado.  
  
## <a name="see-also"></a>Vea también  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)