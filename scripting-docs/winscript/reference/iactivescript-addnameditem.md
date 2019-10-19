---
title: 'IActiveScript:: AddNamedItem | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- AddNamedItem method, IActiveScript interface
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a343e38b944ca36da221da39832046c19b332230
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575825"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
Agrega el nombre de un elemento de nivel de raíz al espacio de nombres del motor de scripting. Un elemento de nivel de raíz es un objeto con propiedades y métodos, un origen de evento o los tres.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstrName`  
 de Dirección de un búfer que contiene el nombre del elemento tal como se ve en el script. El nombre debe ser único y puede ser persistente.  
  
 `dwFlags`  
 de Marcas asociadas a un elemento. Puede ser una combinación de estos valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|Indica que el elemento con nombre representa un objeto de solo código y que el host no tiene ningún `IUnknown` que asociar a este objeto de solo código. El host solo tiene un nombre para este objeto. En los lenguajes orientados a C++objetos como, esta marca crearía una clase. No todos los lenguajes admiten esta marca.|  
|SCRIPTITEM_GLOBALMEMBERS|Indica que el elemento es una colección de propiedades y métodos globales asociados con el script. Normalmente, un motor de scripting omitiría el nombre de objeto (distinto de para usarlo como una cookie para el método [IActiveScriptSite:: GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) o para resolver el ámbito explícito) y exponer sus miembros como variables y métodos globales. Esto permite al host extender la biblioteca (funciones en tiempo de ejecución, etc.) disponible para el script. Se deja al motor de scripting para tratar los conflictos de nombres (por ejemplo, cuando dos elementos SCRIPTITEM_GLOBALMEMBERS tienen métodos del mismo nombre), aunque no se debería devolver un error debido a esta situación.|  
|SCRIPTITEM_ISPERSISTENT|Indica que se debe guardar el elemento si se guarda el motor de scripting. Del mismo modo, el establecimiento de esta marca indica que una transición de vuelta al estado inicializado debe conservar el nombre del elemento y la información de tipo (el motor de scripting debe, sin embargo, liberar todos los punteros a las interfaces en el objeto real).|  
|SCRIPTITEM_ISSOURCE|Indica que el elemento origina eventos que el script puede recibir. Los objetos secundarios (propiedades del objeto que se encuentran en sí mismos objetos) también pueden incluir eventos en el script. Esto no es recursivo, pero proporciona un mecanismo conveniente para el caso común, por ejemplo, para crear un contenedor y todos sus controles miembro.|  
|SCRIPTITEM_ISVISIBLE|Indica que el nombre del elemento está disponible en el espacio de nombres del script, lo que permite el acceso a las propiedades, los métodos y los eventos del elemento. Por Convención, las propiedades del elemento incluyen los elementos secundarios del elemento; por lo tanto, se podrá acceder a todas las propiedades y métodos de los objetos secundarios (y sus elementos secundarios, de forma recursiva).|  
|SCRIPTITEM_NOCODE|Indica que el elemento es simplemente un nombre que se agrega al espacio de nombres del script y no debe tratarse como un elemento para el que se debe asociar el código. Por ejemplo, si no se establece esta marca, VBScript creará un módulo independiente para el elemento con nombre C++ y podría crear una clase contenedora independiente para el elemento con nombre.|  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se ha especificado un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting aún no se ha cargado o inicializado).|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)