---
title: IActiveScriptProperty::SetProperty | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptProperty.SetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- SetProperty method, IActiveScriptProperty interface
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc9b5f4c0d02789988bb41f46417651414beed7f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
Establece la propiedad especificada por el parámetro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT SetProperty(  
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
 Valor de la propiedad que se establecerá.  
  
 `pvarIndex`  
 No usado.  
  
 `pvarValue`  
 El valor de la propiedad.  
  
 Los valores permiten para `dwProperty` se describen en la tabla siguiente.  
  
|Constante|Valor|Significado|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Fuerza al motor de scripting que se divide en modo de entero en lugar del modo de punto flotante. El valor predeterminado es `False`.|  
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
 Para habilitar o deshabilitar la división de enteros, invocar `SetProperty` y convertir un `Boolean` a una `Object`. De forma predeterminada, el valor de propiedad es `False`. Si se establece en `True`, operaciones de división devolverá únicamente números enteros.  
  
 Para habilitar o deshabilitar la comparación de cadenas personalizadas, invocar `SetProperty` y pase un `Object` valor. El objeto que se pasa debe implementar la interfaz [IActiveScriptStringCompare (interfaz)](../../winscript/reference/iactivescriptstringcompare-interface.md). El [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) método de la [IActiveScriptStringCompare (interfaz)](../../winscript/reference/iactivescriptstringcompare-interface.md) interfaz se llama cada vez que se ejecuta una función de comparación de cadena.  
  
 Para seleccionar el conjunto de características del lenguaje que se deben admitir cuando la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se inicializa el motor de scripting, invoque `SetProperty` y pasar un valor que corresponde a la característica de lenguaje que se estableció para habilitarse para SCRIPTPROP_INVOKEVERSIONING. Si esta propiedad se establece en 1 (SCRIPTLANGUAGEVERSION_5_7), las características de lenguaje disponibles son los mismos que los que aparecían en la versión 5.7 de la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor de scripting. Si se establece en 2 (SCRIPTLANGUAGEVERSION_5_8), las características de lenguaje disponibles son aquellos que aparecían en la versión 5.7 Además de nuevas características que se agregaron en la versión 5.8. De forma predeterminada, esta propiedad se establece en 0 (SCRIPTLANGUAGEVERSION_DEFAULT), que es equivalente al conjunto de características de lenguaje que aparecían en la versión 5.7, a menos que el host admite un comportamiento predeterminado distinto. Por ejemplo, Internet Explorer 8 opta por participar en la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] características del lenguaje que son compatibles con la versión 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor de scripting de forma predeterminada cuando el modo de documento predeterminado para Internet Explorer 8 es el modo de "Estándar de Internet Explorer 8". Cambiar el modo de documento de Internet Explorer 8 a los estándares de Internet Explorer 7 o modo Quirks restablece el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor de scripting para admitir solo el conjunto de características de lenguaje que existían en la versión 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor de scripting.  
  
> [!NOTE]
>  SCRIPTPROP_INVOKEVERSIONING se debe establecer únicamente cuando el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor de scripting que se está inicializando.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo forzar que el motor de scripting para usar la división de enteros y cómo permitir que la sobrecarga de la función de comparación.  
  
```c#  
BMLScriptEngine bmlScriptEngine = new BMLScriptEngine();  
IActiveScriptProperty scriptProperties = bmlScriptEngine as   
    IActiveScriptProperty;  
  
// Force the scripting engine to use integer division.  
Boolean enableIntegerDivision = true;  
Object vtIntegerDivInstance = (Object)enableIntegerDivision;  
                scriptProperties.SetProperty(SCRIPTPROP_INTEGERDIVISION,   
    System.IntPtr.Zero, ref vtIntegerDivInstance);  
  
// Allow overloading of the compare function.  
BMLScriptStringCompare bmlScriptStringCompareInstance = new   
    BMLScriptStringCompare();  
Object vtStrCmpInstance = (Object)bmlScriptStringCompareInstance;  
scriptProperties.SetProperty(SCRIPTPROP_STRCOMPINST,   
    System.IntPtr.Zero, ref vtStrCmpInstance);  
```  
  
## <a name="see-also"></a>Vea también  
 [Definir la compatibilidad de documentos](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Información de versiones](../../javascript/reference/javascript-version-information.md)