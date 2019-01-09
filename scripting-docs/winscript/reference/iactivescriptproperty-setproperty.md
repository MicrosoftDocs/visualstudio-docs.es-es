---
title: IActiveScriptProperty::SetProperty | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.SetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- SetProperty method, IActiveScriptProperty interface
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 683041b50002cb926a36e4f10d6758246af91726
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090781"
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
Establece la propiedad especificada por el parámetro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
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
 No se utiliza.  
  
 `pvarValue`  
 El valor de la propiedad.  
  
 Los valores permiten para `dwProperty` se describen en la tabla siguiente.  
  
|Constante|Valor|Significado|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Fuerza el motor de scripting que se divide en modo de entero en lugar del modo de punto flotante. El valor predeterminado es `False`.|  
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
 Para habilitar o deshabilitar la división de enteros, invocar `SetProperty` y convertir un `Boolean` a un `Object`. De forma predeterminada, el valor de propiedad es `False`. Si se establece en `True`, operaciones de división devolverá sólo números enteros.  
  
 Para habilitar o deshabilitar la comparación de cadenas personalizadas, invocar `SetProperty` y pase un `Object` valor. El objeto que se pasa debe implementar la interfaz [IActiveScriptStringCompare (interfaz)](../../winscript/reference/iactivescriptstringcompare-interface.md). El [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) método de la [IActiveScriptStringCompare (interfaz)](../../winscript/reference/iactivescriptstringcompare-interface.md) interfaz se llama cada vez que se ejecuta una función de comparación de cadena.  
  
 Para seleccionar el conjunto de características del lenguaje que se deben admitir cuando la [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se inicializa el motor de scripting, invocar `SetProperty` y pasar un valor que corresponde a la característica de lenguaje que se estableció para habilitarse para SCRIPTPROP_INVOKEVERSIONING. Si esta propiedad se establece en 1 (SCRIPTLANGUAGEVERSION_5_7), las características de lenguaje disponibles son los mismos que los que ha aparecido en la versión 5.7 del [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor de scripting. Si se establece en 2 (SCRIPTLANGUAGEVERSION_5_8), las características de lenguaje disponibles son aquellos que apareció en la versión 5.7 Además de nuevas características que se han agregado en la versión 5.8. De forma predeterminada, esta propiedad se establece en 0 (SCRIPTLANGUAGEVERSION_DEFAULT), que es equivalente al conjunto de características de lenguaje que apareció en la versión 5.7, a menos que el host admite un comportamiento predeterminado distinto. Por ejemplo, Internet Explorer 8 incluye el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] características del lenguaje que son compatibles con la versión 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor de scripting de forma predeterminada cuando el modo de documento predeterminado para Internet Explorer 8 es el modo de "Estándar de Internet Explorer 8". Cambiar el modo de documento de Internet Explorer 8 a los estándares de Internet Explorer 7 o el modo de interpretación restablece el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor de scripting para admitir sólo el conjunto de características de lenguaje que existían en la versión 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor de scripting.  
  
> [!NOTE]
>  Se debe establecer SCRIPTPROP_INVOKEVERSIONING solo cuando el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se está inicializando el motor de scripting.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo forzar que el motor de scripting para usar la división de enteros y cómo permitir que la sobrecarga de la función de comparación.  
  
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
 [Definir la compatibilidad de documentos](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Información de versiones](../../javascript/reference/javascript-version-information.md)