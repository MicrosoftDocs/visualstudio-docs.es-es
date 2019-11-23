---
title: 'IActiveScriptProperty:: SetProperty | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 0f8307a82f181be20205c7bfcc47e881b0fa1e90
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571305"
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
 No usado.  
  
 `pvarValue`  
 Valor de la propiedad.  
  
 En la tabla siguiente se describen los valores permitidos para `dwProperty`.  
  
|Constante|Valor|Significado|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Obliga al motor de scripting a dividir en el modo de entero en lugar de en el modo de punto flotante. El valor predeterminado es `False`.|  
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
 Para habilitar o deshabilitar la división de enteros, invoque `SetProperty` y convierta un `Boolean` en un `Object`. De forma predeterminada, el valor de la propiedad es `False`. Si se establece en `True`, las operaciones de división devolverán solo enteros.  
  
 Para habilitar o deshabilitar la comparación de cadenas personalizadas, invoque `SetProperty` y pase un valor `Object`. El objeto que se pasa debe implementar la interfaz [iactivescriptstringcompare (](../../winscript/reference/iactivescriptstringcompare-interface.md)de la interfaz. Se llama al método [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) de la interfaz de la [interfaz iactivescriptstringcompare (](../../winscript/reference/iactivescriptstringcompare-interface.md) cada vez que se ejecuta una función de comparación de cadenas.  
  
 Para seleccionar el conjunto de características del lenguaje que se admitirán cuando se inicialice el motor de scripting de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], invoque `SetProperty` y pase un valor que se corresponda con el conjunto de características del lenguaje que se va a habilitar para SCRIPTPROP_INVOKEVERSIONING. Si esta propiedad se establece en 1 (SCRIPTLANGUAGEVERSION_5_7), las características de lenguaje disponibles son las mismas que las que aparecían en la versión 5,7 del motor de scripting de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Si se establece en 2 (SCRIPTLANGUAGEVERSION_5_8), las características de lenguaje disponibles son las que aparecían en la versión 5,7, además de las nuevas características que se agregaron en la versión 5,8. De forma predeterminada, esta propiedad se establece en 0 (SCRIPTLANGUAGEVERSION_DEFAULT), que es equivalente al conjunto de características de lenguaje que aparecía en la versión 5,7, a menos que el host admita un comportamiento predeterminado diferente. Por ejemplo, Internet Explorer 8 opta por las características del lenguaje [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que son compatibles con la versión 5,8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor de scripting de forma predeterminada cuando el modo de documento predeterminado para Internet Explorer 8 es el modo "estándar de Internet Explorer 8". Al cambiar el modo de documento de Internet Explorer 8 a los estándares o el modo no estándar de Internet Explorer 7, se restablece el motor de scripting de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] para admitir solo el conjunto de características de lenguaje que existía en la versión 5,7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motor de scripting.  
  
> [!NOTE]
> SCRIPTPROP_INVOKEVERSIONING debe establecerse solo cuando se está inicializando el motor de scripting de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo forzar que el motor de scripting utilice División de enteros y cómo permitir la sobrecarga de la función de comparación.  
  
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