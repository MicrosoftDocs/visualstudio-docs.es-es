---
title: IActiveScriptAuthor::AddNamedItem | Documentos de Microsoft
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
ms.openlocfilehash: 95bc529db8129c4e9af1ed9f9dc3d91de9686223
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63411391"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
Agrega el nombre de un elemento de nivel de raíz para el espacio de nombres del motor de creación de script. Un *elemento de nivel de raíz* es un objeto que puede contener métodos y propiedades, y que también puede contener un origen de eventos.  
  
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
 [in] El nombre del elemento tal como se ve desde la secuencia de comandos. El nombre debe ser único y con persistencia.  
  
 `dwFlags`  
 [in] Marcas que están asociadas con el elemento con nombre. Puede ser una combinación de los siguientes valores:  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|Indica que el nombre del elemento está disponible en el espacio de nombres de la secuencia de comandos. Esto permite el acceso a propiedades, métodos y eventos del elemento.<br /><br /> Por convención, las propiedades del elemento son a miembros de secundarios del elemento. Por lo tanto, todas las propiedades del objeto secundario y métodos (y sus miembros secundarios, de forma recursiva) son accesibles.|  
|SCRIPTITEM_ISSOURCE|0x00000004|Indica que el script puede tener controladores de eventos de script de eventos de elemento de origen.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|Indica que el elemento es una colección de propiedades y métodos que están asociados con la secuencia de comandos globales. Sus miembros se crean como métodos y variables globales.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|Indica que el elemento debe guardarse si se guarda el script de motor de creación.|  
|SCRIPTITEM_CODEONLY|0x00000200|Indica que el elemento con nombre representa un objeto de sólo código, y no tiene un miembro a crear.|  
|SCRIPTITEM_NOCODE|0x00000400|Indica que el elemento con nombre es simplemente un nombre que se va a agregar, y no tiene nada que crear.|  
  
 `pdisp`  
 [in] El `IDispatch` de la `NamedItem` objeto que se usa para recopilar el origen del evento, propiedades o métodos.  
  
## <a name="return-value"></a>Valor devuelto  
 Una clase `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptAuthor (interfaz)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)