---
title: IActiveScript::AddNamedItem | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: db65361e4bde14e803d9085a4530a505ccaf9fcb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24642025"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
Agrega el nombre de un elemento de nivel de raíz al espacio de nombres del motor de scripting. Un elemento de nivel raíz es un objeto con propiedades y métodos, un origen de eventos o los tres.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstrName`  
 [in] Dirección de un búfer que contiene el nombre del elemento tal como se ve desde la secuencia de comandos. El nombre debe ser único y con persistencia.  
  
 `dwFlags`  
 [in] Marcas asociadas a un elemento. Puede ser una combinación de estos valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|Indica que el elemento con nombre representa un objeto solo código, y que el host no tiene `IUnknown` que desee asociar a este objeto solo código. El host sólo tiene un nombre para este objeto. En lenguajes orientados a objetos como C++, esta marca crearía una clase. No todos los lenguajes son compatibles con esta marca.|  
|SCRIPTITEM_GLOBALMEMBERS|Indica que el elemento es una colección de propiedades globales y los métodos asociados con la secuencia de comandos. Normalmente, un motor de scripting omitiría el nombre del objeto (que no sea con el fin de utilizarla como una cookie para la [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) método, o para resolver el ámbito explícita) y exponer sus miembros como global las variables y métodos. Esto permite que el host extender la biblioteca (funciones de tiempo de ejecución y así sucesivamente) disponible para la secuencia de comandos. Se deja al motor de scripting para tratar con nombre está en conflicto (por ejemplo, cuando dos elementos SCRIPTITEM_GLOBALMEMBERS tienen métodos del mismo nombre), aunque no se debe devolver un error debido a esta situación.|  
|SCRIPTITEM_ISPERSISTENT|Indica que se debe guardar el elemento si se guarda el motor de scripting. De forma similar, si se establece esta marca indica que una transición al estado inicializado debe conservar información de nombre y el tipo del elemento (el motor de scripting no obstante, debe liberar todos los punteros a las interfaces del objeto real).|  
|SCRIPTITEM_ISSOURCE|Indica que el elemento de orígenes de eventos que puede recibir la secuencia de comandos. Los objetos secundarios (propiedades del objeto que se encuentran en los propios objetos) también pueden obtener eventos para la secuencia de comandos. Esto no es recursiva, pero proporciona un mecanismo conveniente para el caso común, por ejemplo, de creación de controles de un contenedor y todos sus miembros.|  
|SCRIPTITEM_ISVISIBLE|Indica que el nombre del elemento está disponible en el espacio de nombres de la secuencia de comandos, permitiendo el acceso a las propiedades, métodos y eventos del elemento. Por convención las propiedades del elemento son a elementos secundarios del elemento; por lo tanto, todas las propiedades del objeto secundario y métodos (y sus elementos secundarios, de forma recursiva) será accesible.|  
|SCRIPTITEM_NOCODE|Indica que el elemento es simplemente un nombre que se va a agregar al espacio de nombres de la secuencia de comandos y no debe tratarse como un elemento para el que debe asociarse código. Por ejemplo, sin esta marca se establece, VBScript creará un módulo independiente para el elemento con nombre y C++ podría crear una clase contenedora independiente para el elemento con nombre.|  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting se aún no ha cargado o inicializar).|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)