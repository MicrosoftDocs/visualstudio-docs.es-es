---
title: "IActiveScriptProperty::SetProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProperty.SetProperty
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SetProperty (método), IActiveScriptProperty (interfaz)"
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# IActiveScriptProperty::SetProperty
Establece la propiedad especificada por el parámetro.  
  
## Sintaxis  
  
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
  
#### Parámetros  
 `dwProperty`  
 Valor de la propiedad que se va a establecer.  
  
 `pvarIndex`  
 No se utiliza.  
  
 `pvarValue`  
 Valor de la propiedad.  
  
 Los valores permitidos para `dwProperty` se describen en la tabla siguiente.  
  
|Constante|Valor|Significado|  
|---------------|-----------|-----------------|  
|SCRIPTPROP\_INTEGERMODE|0x00003000|Fuerza el motor de script para dividir en modo integer en lugar de modo de punto flotante.  El valor predeterminado es `False`.|  
|SCRIPTPROP\_STRINGCOMPAREINSTANCE|0x00003001|Permite la cadena compara la función del motor de script que se va a reemplazar.|  
|SCRIPTPROP\_ABBREVIATE\_GLOBALNAME\_RESOLUTION|0x70000002|Informa al motor de scripting que ningún otro los motores de scripting existen para contribuir al objeto global.|  
|SCRIPTPROP\_INVOKEVERSIONING|0x00004000|Fuerza el motor de script de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] para seleccionar un conjunto de características de lenguaje que se admitirán.  El conjunto predeterminado de características del lenguaje admitidas por el motor de script de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] es equivalente a la característica de lenguaje establecida que se produjo en la versión 5,7 del motor de script de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .|  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no es válido.|  
|`E_UNEXPECTED`|La llamada no se esperaba \(por ejemplo, el motor de script aún no se han cargado no se ha inicializado\).|  
  
## Comentarios  
 Para habilitar o la división de enteros deshabilitada, invoca `SetProperty` y convierte `Boolean` a `Object`.  De forma predeterminada, el valor de propiedad es `False`.  Si se establece `True`, operaciones de división devuelve sólo números enteros.  
  
 Para habilitar o una comparación de cadenas personalizada deshabilitada, invocar `SetProperty` y pase un valor de `Object` .  El objeto que se pasa debe implementar la interfaz [IActiveScriptStringCompare \(Interfaz\)](../../winscript/reference/iactivescriptstringcompare-interface.md).  El método de [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) de la interfaz de [IActiveScriptStringCompare \(Interfaz\)](../../winscript/reference/iactivescriptstringcompare-interface.md) se llama cada vez que una cadena compara la función se ejecuta.  
  
 Para seleccionar el conjunto de características de lenguaje que se admitirá cuando se inicializa el motor de script de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] , invoque `SetProperty` y pasa un valor correspondiente a la característica de lenguaje establecida en habilitado para SCRIPTPROP\_INVOKEVERSIONING.  Si esta propiedad se establece en 1 \(SCRIPTLANGUAGEVERSION\_5\_7\), las características de lenguaje disponibles son los mismos que los que se produjeron en la versión 5,7 del motor de script de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  Si se establece en 2 \(SCRIPTLANGUAGEVERSION\_5\_8\), las características de lenguaje disponibles son las que se produjeron en la versión 5,7 además de las nuevas características que se agregaron en la versión 5,8.  De forma predeterminada, esta propiedad se establece en 0 \(SCRIPTLANGUAGEVERSION\_DEFAULT\), que es equivalente a la característica de lenguaje establecida que se produjo en la versión 5,7, a menos que el host admita otro comportamiento predeterminado.  Por ejemplo, Internet Explorer 8 opta en las características de lenguaje de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] admitidas por el motor de script de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] de la versión 5,8 de forma predeterminada al predeterminado del documento para Internet Explorer 8 es “modo de estándares de Internet Explorer 8”.  Cambiar al modo de Internet Explorer 8 en modo de normas o de los modos de interpretación de Internet Explorer 7 restablece el motor de script de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] para admitir sólo la característica de lenguaje establecida que existía en el motor de script de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] de la versión 5,7.  
  
> [!NOTE]
>  SCRIPTPROP\_INVOKEVERSIONING establecido cuando se inicializa el motor de script de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo forzar el motor de script para utilizar la división de enteros y cómo permitir sobrecarga de funciones de comparar.  
  
```csharp  
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
  
## Vea también  
 [Definición de compatibilidad del documento](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Información de versiones](../../javascript/reference/javascript-version-information.md)