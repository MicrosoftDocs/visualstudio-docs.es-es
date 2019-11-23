---
title: 'IActiveScriptProperty:: GetProperty | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.GetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetProperty method, IActiveScriptProperty interface
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1eeec6472a067d18a8b8962cfac70c25c0ff971
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571416"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
Obtiene la propiedad especificada por el parámetro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetProperty(  
// The property value:  
    uint dwProperty,    
// Not used:  
    IntPtr pvarIndex,    
// The value of the property:   
    out object pvarValue,    
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwProperty`  
 Valor de propiedad que se va a obtener.  
  
 `pvarIndex`  
 No usado.  
  
 `pvarValue`  
 Valor de la propiedad.  
  
 En la tabla siguiente se describen los valores permitidos para `dwProperty`.  
  
|Constante|Valor|Significado|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Obliga al motor de scripting a dividir en el modo de entero en lugar de en el modo de punto flotante.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Permite reemplazar la función de comparación de cadenas del motor de scripting.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Informa al motor de scripting de que no existen otros motores de scripting para contribuir al objeto global.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Fuerza al motor de scripting de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] a seleccionar un conjunto de características de lenguaje que se admitirán. El conjunto predeterminado de características del lenguaje admitido por el motor de scripting de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] es equivalente al conjunto de características del lenguaje que aparecía en la versión 5,7 del motor de scripting de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].|  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no es válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting aún no se ha cargado o inicializado).|  
  
## <a name="remarks"></a>Comentarios  
 El host puede utilizar la propiedad SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION para informar a un motor de scripting de que no existen otros motores de scripting que contribuyan al objeto global. Por ejemplo, Internet Explorer puede informar al motor de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] de que la página que se representa contiene solo [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] scripts. Por lo tanto, solo el motor de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] puede agregar nuevas propiedades a la ventana de objeto global y no hay ningún motor de Visual Basic Scripting Edition (VBScript) para hacer lo mismo. El motor puede omitir esta marca o puede utilizarla para optimizar la administración de nuevos miembros que se agregan al objeto global.  
  
 El host puede utilizar la propiedad SCRIPTPROP_INVOKEVERSIONING para seleccionar el conjunto de características del lenguaje que se admitirán cuando se inicie el motor de scripting de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Si esta propiedad se establece en 1 (SCRIPTLANGUAGEVERSION_5_7), las características de lenguaje disponibles son las mismas que las que aparecían en la versión 5,7 del motor de scripting de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Si se establece en 2 (SCRIPTLANGUAGEVERSION_5_8), las características de lenguaje disponibles son las que aparecían en la versión 5,7, además de las características que se agregaron en la versión 5,8. De forma predeterminada, esta propiedad se establece en 0 (SCRIPTLANGUAGEVERSION_DEFAULT), que es equivalente al conjunto de características de lenguaje que aparecía en la versión 5,7, a menos que el host admita un comportamiento predeterminado diferente. Por ejemplo, Internet Explorer 8 opta por las características del lenguaje [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que admite la versión 5,8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor de scripting de forma predeterminada cuando el modo de documento para Internet Explorer 8 es el modo "estándar de Internet Explorer 8".  
  
## <a name="see-also"></a>Vea también  
 [Definir la compatibilidad de documentos](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Información de versiones](../../javascript/reference/javascript-version-information.md)