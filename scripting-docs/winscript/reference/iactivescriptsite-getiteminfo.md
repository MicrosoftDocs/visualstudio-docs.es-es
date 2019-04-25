---
title: IActiveScriptSite::GetItemInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetItemInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetItemInfo
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 997245f8e4fd43ac2162587f07e4c8711af7caac
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148690"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
Permite que el motor de scripting obtener información sobre un elemento agregado con el [IActiveScript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) método.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstrName`  
 [in] El nombre asociado con el elemento, como se especifica en el [IActiveScript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) método.  
  
 `dwReturnMask`  
 [in] Una máscara de bits que especifica qué información sobre el elemento que se debe devolver. El motor de scripting debe solicitar la cantidad mínima de información posible porque algunos de los parámetros de valor devueltos (por ejemplo, `ITypeInfo`) puede tardar bastante tiempo en cargar o generar. Puede ser una combinación de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|Devuelve el `IUnknown` interfaz para este elemento.|  
|SCRIPTINFO_ITYPEINFO|Devuelve el `ITypeInfo` interfaz para este elemento.|  
  
 `ppunkItem`  
 [out] Dirección de una variable que recibe un puntero a la `IUnknown` interfaz asociada con el elemento especificado. Puede usar el motor de scripting el `IUnknown::QueryInterface` método para obtener el `IDispatch` interfaz para el elemento. Este parámetro recibe el valor NULL si `dwReturnMask` no incluye el valor SCRIPTINFO_IUNKNOWN. Además, recibe NULL si no hay ningún objeto asociado con el nombre del elemento; Este mecanismo se usa para crear una clase simple cuando se agregó el elemento con nombre con la marca SCRIPTITEM_CODEONLY establecida el [IActiveScript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) método.  
  
 `ppTypeInfo`  
 [out] Dirección de una variable que recibe un puntero a la `ITypeInfo` asociada al elemento de interfaz. Este parámetro recibe el valor NULL si `dwReturnMask` no incluye el valor SCRIPTINFO_ITYPEINFO, o si no está disponible para este elemento de información de tipo. Si no está disponible la información de tipo, el objeto no puede obtener los eventos y enlaces de nombre deben llevarse a cabo con el `IDispatch::GetIDsOfNames` método. Tenga en cuenta que el `ITypeInfo` interfaz recuperar describe coclase del elemento (TKIND_COCLASS) porque el objeto puede admitir varias interfaces y las interfaces de eventos. Si el elemento admite la `IProvideMultipleTypeInfo` interfaz, el `ITypeInfo` interfaz recuperado es el mismo que el índice cero `ITypeInfo` que podría obtenerse mediante la `IProvideMultipleTypeInfo::GetInfoOfIndex` método.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
|`TYPE_E_ELEMENTNOTFOUND`|No se encontró un elemento del nombre especificado.|  
  
## <a name="remarks"></a>Comentarios  
 Este método sólo recupera la información indicada por el `dwReturnMask` parámetro; Esto mejora el rendimiento. Por ejemplo, si un `ITypeInfo` interfaz no es necesaria para un artículo, simplemente no se especifica en `dwReturnMask`.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)