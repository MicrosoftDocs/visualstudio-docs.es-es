---
title: 'Iactivescriptauthor (:: AddNamedItem | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddNamedItem
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0d2f08a49fdc768e87152bf486ce48687c79e68
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577256"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
Agrega el nombre de un elemento de nivel de raíz al espacio de nombres del motor de creación de scripts. Un *elemento de nivel de raíz* es un objeto que puede contener propiedades y métodos, y que también puede contener un origen de eventos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszName`  
 de Nombre del elemento tal como se ve en el script. El nombre debe ser único y puede ser persistente.  
  
 `dwFlags`  
 de Marcas asociadas al elemento con nombre. Puede ser una combinación de los siguientes valores:  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|Indica que el nombre del elemento está disponible en el espacio de nombres del script. Esto permite el acceso a las propiedades, los métodos y los eventos del elemento.<br /><br /> Por Convención, las propiedades del elemento incluyen los miembros secundarios del elemento. Por lo tanto, se puede tener acceso a todas las propiedades y métodos de los objetos secundarios (y sus miembros secundarios, de forma recursiva).|  
|SCRIPTITEM_ISSOURCE|0x00000004|Indica los eventos del origen del elemento que el script puede tener controladores de eventos de script.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|Indica que el elemento es una colección de propiedades y métodos globales que están asociados con el script. Sus miembros se crean como variables y métodos globales.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|Indica que se debe guardar el elemento si se guarda el motor de creación de scripts.|  
|SCRIPTITEM_CODEONLY|0x00000200|Indica que el elemento con nombre representa un objeto de solo código y no tiene un miembro para crear.|  
|SCRIPTITEM_NOCODE|0x00000400|Indica que el elemento con nombre es simplemente un nombre que se agrega y no tiene nada que crear.|  
  
 `pdisp`  
 de @No__t_0 del objeto de `NamedItem` que se usa para recopilar métodos, propiedades o el origen del evento.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz iactivescriptauthor (](../../winscript/reference/iactivescriptauthor-interface.md)  
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)