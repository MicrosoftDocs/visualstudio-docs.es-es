---
title: IActiveScriptProperty::GetProperty | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d55fb2d816931a74827d318e13860b3f97f0fd23
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726055"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
Obtiene la propiedad especificada por el parámetro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
 No usado.  
  
 `pvarValue`  
 El valor de la propiedad.  
  
 Los valores permiten para `dwProperty` se describen en la tabla siguiente.  
  
|Constante|Valor|Significado|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Fuerza al motor de scripting que se divide en modo de entero en lugar del modo de punto flotante.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Permite que la función de comparación de cadena del motor de scripting que se debe reemplazar.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Notifica al motor de scripting que no existen ningún otros motores de secuencias de comandos para contribuir en el objeto global.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Fuerza el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor de scripting para seleccionar un conjunto de características del lenguaje que se deben admitir. El conjunto predeterminado de características del lenguaje compatible con la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] es equivalente al conjunto de características de lenguaje que aparecían en la versión 5.7 del motor de scripting el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor de scripting.|  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no es válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting se aún no ha cargado o inicializar).|  
  
## <a name="remarks"></a>Comentarios  
 El host puede utilizar la propiedad SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION para informar a un motor de scripting que no existen ningún otros motores de secuencias de comandos para contribuir en el objeto global. Por ejemplo, Internet Explorer puede informar a la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor incluidos en la página que se va a representar solo [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] secuencias de comandos. Por lo tanto, solo el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor puede agregar nuevas propiedades a la ventana de objetos globales, y no hay ningún motor de Visual Basic Scripting Edition (VBScript) para hacer lo mismo. El motor puede omitir esta marca o puede usar para optimizar la administración de los miembros nuevos que se agregan al objeto global.  
  
 El host puede utilizar la propiedad SCRIPTPROP_INVOKEVERSIONING para seleccionar el conjunto de características de lenguaje que se admiten cuando la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se inicia el motor de scripting. Si esta propiedad se establece en 1 (SCRIPTLANGUAGEVERSION_5_7), las características de lenguaje disponibles son los mismos que los que aparecían en la versión 5.7 de la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor de scripting. Si se establece en 2 (SCRIPTLANGUAGEVERSION_5_8), las características de lenguaje disponibles son aquellos que aparecían en la versión 5.7 Además de las funciones que se agregaron en la versión 5.8. De forma predeterminada, esta propiedad se establece en 0 (SCRIPTLANGUAGEVERSION_DEFAULT), que es equivalente al conjunto de características de lenguaje que aparecían en la versión 5.7, a menos que el host admite un comportamiento predeterminado distinto. Por ejemplo, Internet Explorer 8 opta por participar en la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] características del lenguaje admitidos por la versión 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor de scripting de forma predeterminada cuando el modo de documento para Internet Explorer 8 es el modo de "Estándar de Internet Explorer 8".  
  
## <a name="see-also"></a>Vea también  
 [Definir la compatibilidad de documentos](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Información de versiones](../../javascript/reference/javascript-version-information.md)