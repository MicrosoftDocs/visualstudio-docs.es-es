---
title: IDispatchEx::DeleteMemberByName | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByName
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByName method
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1866b5135d2c98ccacb34c2c776c69dd7d25db3f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096439"
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
Elimina a un miembro por su nombre.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `bstrName`  
 Nombre del miembro que se va a eliminar.  
  
 `grfdex`  
 Determina si el nombre de miembro distingue mayúsculas de minúsculas. Esto puede ser uno de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|fdexNameCaseSensitive|Solicitudes que se realiza la búsqueda de nombre en minúsculas. Se pueden omitir si el objeto que no es compatible con la búsqueda distingue mayúsculas de minúsculas.|  
|fdexNameCaseInsensitive|Solicitudes que se realiza la búsqueda de nombre en mayúsculas y minúsculas. Se pueden omitir si el objeto que no es compatible con la búsqueda de mayúsculas y minúsculas.|  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|||  
|-|-|  
|`S_OK`|Correcto.|  
|`S_FALSE`|Miembro existe pero no se puede eliminar.|  
  
## <a name="remarks"></a>Comentarios  
 Si se elimina el miembro, debe permanecer válido para el identificador DISPID `GetNextDispID`.  
  
 Si se elimina un miembro con un nombre determinado y posteriormente se vuelve a crear un miembro con el mismo nombre, el identificador DISPID debe ser el mismo. (Si los miembros que difieran solo por caso son "iguales" es el objeto dependiente).  
  
## <a name="example"></a>Ejemplo  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Vea también  
 [IDispatchEx (Interfaz)](../../winscript/reference/idispatchex-interface.md)