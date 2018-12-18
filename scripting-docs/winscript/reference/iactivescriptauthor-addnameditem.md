---
title: IActiveScriptAuthor::AddNamedItem | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 83d2597f8468bb97d20da655a56a751191ec4b55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645615"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
Agrega el nombre de un elemento de nivel de raíz para el espacio de nombres del motor de creación de script. A *elemento de nivel raíz* es un objeto que puede contener métodos y propiedades, y que también puede contener un origen de eventos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
 [in] Los marcadores que están asociados con el elemento con nombre. Puede ser una combinación de los siguientes valores:  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|Indica que el nombre del elemento está disponible en el espacio de nombres de la secuencia de comandos. Esto permite el acceso a propiedades, métodos y eventos del elemento.<br /><br /> Por convención, las propiedades del elemento incluyen a los miembros secundarios del elemento. Por lo tanto, todas las propiedades del objeto secundario y métodos (y sus miembros secundarios, de forma recursiva) son accesibles.|  
|SCRIPTITEM_ISSOURCE|0x00000004|Indica que la secuencia de comandos puede tener controladores de eventos de secuencia de comandos los eventos del origen del elemento.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|Indica que el elemento es una colección de propiedades globales y los métodos que están asociados a la secuencia de comandos. Sus miembros se crean como métodos y variables globales.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|Indica que se debe guardar el elemento si se guarda el motor de creación de script.|  
|SCRIPTITEM_CODEONLY|0x00000200|Indica que el elemento con nombre representa un objeto solo código, y no tiene un miembro a crear.|  
|SCRIPTITEM_NOCODE|0x00000400|Indica que el elemento con nombre es simplemente un nombre que se agrega y no tiene nada que crear.|  
  
 `pdisp`  
 [in] El `IDispatch` de la `NamedItem` objeto que se usa para recopilar métodos, propiedades o el origen del evento.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptAuthor (interfaz)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)