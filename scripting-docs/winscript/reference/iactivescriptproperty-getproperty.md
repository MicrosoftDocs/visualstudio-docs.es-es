---
title: IActiveScriptProperty::GetProperty | Microsoft Docs
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
ms.openlocfilehash: e10d72e289fc2dc31464ce4505cea5c03e8d7f9d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992789"
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
 Para obtener el valor de propiedad.  
  
 `pvarIndex`  
 No se utiliza.  
  
 `pvarValue`  
 Valor de la propiedad.  
  
 Los valores permiten para `dwProperty` se describen en la tabla siguiente.  
  
|Constante|Valor|Significado|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Fuerza el motor de scripting que se divide en modo de entero en lugar del modo de punto flotante.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Permite que la función de comparación de cadena del motor de scripting que se debe reemplazar.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Notifica al motor de scripting que no existen ningún otros motores de secuencias de comandos para contribuir al objeto global.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Fuerza el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor de scripting para seleccionar un conjunto de características del lenguaje que se deben admitir. El conjunto predeterminado de las características de lenguaje admitidas por la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] es equivalente al conjunto de características de lenguaje que apareció en la versión 5.7 del motor de scripting el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor de scripting.|  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no es válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting no se ha cargado o inicializado).|  
  
## <a name="remarks"></a>Comentarios  
 El host puede utilizar la propiedad SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION para informar al motor de scripting que no existen ningún otros motores de secuencias de comandos para contribuir al objeto global. Por ejemplo, puede informar Internet Explorer el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor de la página que se procesa solo contiene [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] secuencias de comandos. Por lo tanto, solo el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor puede agregar nuevas propiedades a la ventana del objeto global y no hay ningún motor de Visual Basic Scripting Edition (VBScript) para hacer lo mismo. El motor puede omitir esta marca o puede usar para optimizar la administración de los miembros nuevos que se agregan al objeto global.  
  
 El host puede utilizar la propiedad SCRIPTPROP_INVOKEVERSIONING para seleccionar el conjunto de características de lenguaje que se admiten cuando la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se inicia el motor de scripting. Si esta propiedad se establece en 1 (SCRIPTLANGUAGEVERSION_5_7), las características de lenguaje disponibles son los mismos que los que ha aparecido en la versión 5.7 del [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor de scripting. Si se establece en 2 (SCRIPTLANGUAGEVERSION_5_8), las características de lenguaje disponibles son aquellos que apareció en la versión 5.7 Además de las características que se han agregado en la versión 5.8. De forma predeterminada, esta propiedad se establece en 0 (SCRIPTLANGUAGEVERSION_DEFAULT), que es equivalente al conjunto de características de lenguaje que apareció en la versión 5.7, a menos que el host admite un comportamiento predeterminado distinto. Por ejemplo, Internet Explorer 8 incluye el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] características del lenguaje compatibles con la versión 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor de scripting de forma predeterminada cuando el modo de documento para Internet Explorer 8 es el modo de "Estándar de Internet Explorer 8".  
  
## <a name="see-also"></a>Vea también  
 [Definir la compatibilidad de documentos](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Información de versiones](../../javascript/reference/javascript-version-information.md)