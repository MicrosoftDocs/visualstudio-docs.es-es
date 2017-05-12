---
title: "IDispatchEx::InvokeEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.InvokeEx
apilocation: scrobj.dll
helpviewer_keywords: 
  - "InvokeEx (método)"
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDispatchEx::InvokeEx
Proporciona acceso a las propiedades y los métodos expuestos por un objeto de `IDispatchEx` .  
  
## Sintaxis  
  
```  
HRESULT InvokeEx(  
   DISPID id,  
   LCID lcid,  
   WORD wFlags,  
   DISPARAMS *pdp,  
   VARIANT *pVarRes,   
   EXCEPINFO *pei,   
   IServiceProvider *pspCaller   
);  
```  
  
#### Parámetros  
 `id`  
 Identifica el miembro.  Aplicaciones `GetDispID` o `GetNextDispID` de obtener el identificador de envío.  
  
 `lcid`  
 Contexto de la configuración regional en que se interpretan los argumentos.  `lcid` se pasa a `InvokeEx` para permitir que el objeto interpretar sus argumentos específicos de la configuración regional.  
  
 `wFlags`  
 Valores válidos para `wFlags` son:  
  
 DISPATCH\_PROPERTYGET &#124; DISPATCH\_METHOD &#124; DISPATCH\_PROPERTYPUT &#124; DISPATCH\_PROPERTYPUTREF &#124; DISPATCH\_CONSTRUCT  
  
 Marcas que describen el contexto de llamada de `InvokeEx` :  
  
|Valor|Significado|  
|-----------|-----------------|  
|DISPATCH\_METHOD|Se invoca el miembro como método.  Si una propiedad tiene el mismo nombre, esto y el indicador de DISPATCH\_PROPERTYGET puede establecer \(definido por `IDispatch`\).|  
|DISPATCH\_PROPERTYGET|Recuperar el miembro como una propiedad o miembro de datos \(definido por `IDispatch`\).|  
|DISPATCH\_PROPERTYPUT|Se cambia el miembro como una propiedad o miembro de datos \(definido por `IDispatch`\).|  
|DISPATCH\_PROPERTYPUTREF|Una asignación de referencia en lugar de una asignación de valor cambia el miembro.  Este marcador solamente es válido cuando la propiedad acepta una referencia a un objeto \(definido por `IDispatch`\).|  
|DISPATCH\_CONSTRUCT|Se utiliza el miembro como constructor.  \(Esto es un nuevo valor definido por `IDispatchEx`\).  Valores válidos para `wFlags` son:<br /><br /> DISPATCH\_PROPERTYGET DISPATCH\_METHOD DISPATCH\_PROPERTYPUT DISPATCH\_PROPERTYPUTREF DISPATCH\_CONSTRUCT|  
  
 `pdp`  
 Puntero a una estructura que contiene una matriz de argumentos, una matriz de valores DISPID de argumento para argumentos con nombre y recuentos del número de elementos de cada matriz.  Vea la documentación de `IDispatch` para obtener una descripción completa de la estructura de DISPPARAMS.  
  
 `pVarRes`  
 Puntero a la ubicación donde va a almacenar el resultado o en Null si el llamador no cuenta con ningún resultado.  Se omite este argumento si se especifica DISPATCH\_PROPERTYPUT o DISPATCH\_PROPERTYPUTREF.  
  
 `pei`  
 Puntero a una estructura que contiene información de excepciones.  Esta estructura se debería rellenar si se devuelve `DISP_E_EXCEPTION` .  Puede ser Null.  Vea la documentación de `IDispatch` para obtener una descripción completa de la estructura de `EXCEPINFO` .  
  
 `pspCaller`  
 Puntero a un objeto de proveedor de servicios proporcionado por el llamador, que permite que el objeto obtener servicios del llamador.  Puede ser Null.  
  
 `IDispatchEx::InvokeEx` proporciona las mismas características que `IDispatch::Invoke` y agrega algunas extensiones:  
  
|||  
|-|-|  
|DISPATCH\_CONSTRUCT|Indica que el elemento se utiliza como constructor.|  
|`pspCaller`|`pspCaller` permite el acceso a los servicios proporcionados por el llamador.  Los servicios específicos se pueden controlar mediante el llamador propio o delegar a los llamadores aún más por la cadena de llamadas.  Por ejemplo, si un motor de script en un explorador realiza una llamada de `InvokeEx` a un objeto externo, el objeto puede seguir a la cadena de `pspCaller` para obtener servicios de motor o el explorador del script.  \(Observe que la cadena de llamada no es igual que la cadena \- también de creación conocida como la cadena de contenedor o cadena de sitio.  La cadena de creación puede estar disponibles a través de algún otro mecanismo como `IObjectWithSite`.\)|  
|Puntero de`this`|Cuando DISPATCH\_METHOD se establece en `wFlags`, podría haber un “parámetro con nombre” por “este” valor.  El identificador de envío se DISPID\_THIS y debe ser el primer parámetro con nombre.|  
  
 El parámetro no de `riid` en `IDispatch::Invoke` se ha quitado.  
  
 El parámetro de `puArgArr` en `IDispatch::Invoke` se ha quitado.  
  
 Vea la documentación de `IDispatch::Invoke` para los ejemplos siguientes:  
  
 “Llamando a un método sin argumentos”  
  
 “Obtener y establecer propiedades”  
  
 “Pasar parámetros”  
  
 “Propiedades indizadas”  
  
 “Iniciando excepciones durante invoca”  
  
 “Devolviendo errores”  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|||  
|-|-|  
|`S_OK`|Correcto.|  
|DISP\_E\_BADPARAMCOUNT|El número de elementos proporcionados a DISPPARAMS es diferente del número de argumentos aceptados por el método o la propiedad.|  
|DISP\_E\_BADVARTYPE|Uno de los argumentos de `rgvarg` no es un tipo válido de variante.|  
|DISP\_E\_EXCEPTION|La aplicación debe provocar una excepción.  En este caso, la estructura pasada en `pei` debe completarse.|  
|DISP\_E\_MEMBERNOTFOUND|El miembro solicitado no existe, o la llamada a `InvokeEx` intentado establecer el valor de una propiedad de sólo lectura.|  
|DISP\_E\_NONAMEDARGS|Esta implementación de `IDispatch` no admite argumentos con nombre.|  
|DISP\_E\_OVERFLOW|Uno de los argumentos de `rgvarg` no pudo forzar al tipo especificado.|  
|DISP\_E\_PARAMNOTFOUND|Uno de parámetro Identificadores no corresponde a un parámetro en el método.|  
|DISP\_E\_TYPEMISMATCH|Uno o más de los argumentos no pudieron convertidos.|  
|DISP\_E\_UNKNOWNLCID|El miembro que se invoca interpreta argumentos de cadena como LCID, y LCID no se reconoce.  Si el LCID no es necesario para interpretar argumentos, este error no se debe devolver.|  
|DISP\_E\_PARAMNOTOPTIONAL|Se omitió un parámetro requerido.|  
  
## Ejemplo  
  
```  
VARIANT var;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
   DISPPARAMS dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
   {  
      pdex->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
   }  
```  
  
## Vea también  
 [IDispatchEx \(Interfaz\)](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)