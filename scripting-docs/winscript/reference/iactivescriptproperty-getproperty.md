---
title: "IActiveScriptProperty::GetProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProperty.GetProperty
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetProperty (método), IActiveScriptProperty (interfaz)"
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# IActiveScriptProperty::GetProperty
Obtiene la propiedad especificada por el parámetro.  
  
## Sintaxis  
  
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
  
#### Parámetros  
 `dwProperty`  
 El valor de propiedad que se va a obtener.  
  
 `pvarIndex`  
 No se utiliza.  
  
 `pvarValue`  
 Valor de la propiedad.  
  
 Los valores permitidos para `dwProperty` se describen en la tabla siguiente.  
  
|Constante|Valor|Significado|  
|---------------|-----------|-----------------|  
|SCRIPTPROP\_INTEGERMODE|0x00003000|Fuerza el motor de script para dividir en modo integer en lugar de modo de punto flotante.|  
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
 El host puede utilizar la propiedad de SCRIPTPROP\_ABBREVIATE\_GLOBALNAME\_RESOLUTION para informar a un motor de scripting que ningún otro los motores de scripting existen para contribuir al objeto global.  Por ejemplo, Internet Explorer puede informar al motor de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que la página que muestra sólo contiene los scripts de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  Así, solo el motor de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] puede agregar nuevas propiedades a la ventana del objeto global, y no hay motor de búsqueda de Visual Basic scripting edition \(VBScript\) para hacer lo mismo.  El motor puede omitir este marcador o puede utilizarlo para optimizar la administración de los nuevos miembros agregados al objeto global.  
  
 El host puede utilizar la propiedad de SCRIPTPROP\_INVOKEVERSIONING para seleccionar el conjunto de características de lenguaje que se admitirá cuando se inicia el motor de script de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  Si esta propiedad se establece en 1 \(SCRIPTLANGUAGEVERSION\_5\_7\), las características de lenguaje disponibles son los mismos que los que se produjeron en la versión 5,7 del motor de script de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  Si se establece en 2 \(SCRIPTLANGUAGEVERSION\_5\_8\), las características de lenguaje disponibles son las que se produjeron en la versión 5,7 además de las características que se agregaron en la versión 5,8.  De forma predeterminada, esta propiedad se establece en 0 \(SCRIPTLANGUAGEVERSION\_DEFAULT\), que es equivalente a la característica de lenguaje establecida que se produjo en la versión 5,7, a menos que el host admita otro comportamiento predeterminado.  Por ejemplo, Internet Explorer 8 opta en las características de lenguaje de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] admitidas por el motor de script de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] de la versión 5,8 de forma predeterminada cuando el modo del documento para Internet Explorer 8 es “modo de estándares de Internet Explorer 8”.  
  
## Vea también  
 [Definición de compatibilidad del documento](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Información de versiones](../../javascript/reference/javascript-version-information.md)