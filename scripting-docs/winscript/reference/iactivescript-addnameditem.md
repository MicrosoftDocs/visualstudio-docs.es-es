---
title: 'IActiveScript:: Addnameditem | Documentos de Microsoft'
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
ms.openlocfilehash: 4ae4a84821d0db226cbecb01e329e4f2941a675d
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095100"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
Agrega el nombre de un elemento de nivel de raíz al espacio de nombres del motor de scripting. Un elemento de nivel de raíz es un objeto con propiedades y métodos, un origen de eventos o las tres.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
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
|SCRIPTITEM_CODEONLY|Indica que el elemento con nombre representa un objeto de sólo código, y que el host no tiene ningún `IUnknown` va a asociar a este objeto solo código. El host sólo tiene un nombre para este objeto. En los lenguajes orientados a objetos como C++, esta marca crearía una clase. No todos los lenguajes admiten esta marca.|  
|SCRIPTITEM_GLOBALMEMBERS|Indica que el elemento es una colección de propiedades globales y los métodos asociados a la secuencia de comandos. Normalmente, un motor de scripting, se ignoraría el nombre de objeto (que no sea con el fin de utilizarlo como una cookie para el [GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) método, o para resolver el ámbito explícito) y exponer sus miembros como global las variables y métodos. Esto permite que el host extender la biblioteca (funciones de tiempo de ejecución y así sucesivamente) disponible para el script. Se deja al motor de scripting para tratar con el nombre entra en conflicto (por ejemplo, cuando dos elementos SCRIPTITEM_GLOBALMEMBERS tienen métodos del mismo nombre), aunque no se debe devolver un error debido a esta situación.|  
|SCRIPTITEM_ISPERSISTENT|Indica que el elemento debe guardarse si se guarda el motor de scripting. De forma similar, al establecer esta marca indica que una transición al estado inicializado debe conservar información de nombre y el tipo del elemento (el motor de scripting no obstante, debe liberar todos los punteros a las interfaces del objeto real).|  
|SCRIPTITEM_ISSOURCE|Indica que el elemento de origen de eventos que puede recibir la secuencia de comandos. Los objetos secundarios (propiedades del objeto que se encuentran en los propios objetos) también pueden obtener los eventos a la secuencia de comandos. Esto no es recursiva, pero proporciona un mecanismo conveniente para el caso común, por ejemplo, de creación de controles de un contenedor y todos sus miembros.|  
|SCRIPTITEM_ISVISIBLE|Indica que el nombre del elemento está disponible en el espacio de nombres de la secuencia de comandos, permitiendo el acceso a las propiedades, métodos y eventos del elemento. Por convención, las propiedades del elemento son a elementos secundarios del elemento; por lo tanto, todas las propiedades del objeto secundario y métodos (y sus elementos secundarios, de forma recursiva) serán accesibles.|  
|SCRIPTITEM_NOCODE|Indica que el elemento es simplemente un nombre que se agregan al espacio de nombres de la secuencia de comandos y no debe tratarse como un elemento para el que se debe asociar código. Por ejemplo, sin esta marca se establece, VBScript creará un módulo independiente para el elemento con nombre y C++ podría crear una clase de contenedor independiente para el elemento con nombre.|  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting no se ha cargado o inicializado).|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)