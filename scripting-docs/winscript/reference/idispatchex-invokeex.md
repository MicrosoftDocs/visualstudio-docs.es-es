---
title: 'IDispatchEx:: InvokeEx | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.InvokeEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- InvokeEx method
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a15acb3211c0d3dd19c0d262efb6cbd3327ab9a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575313"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Proporciona acceso a las propiedades y los métodos expuestos por un objeto `IDispatchEx`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
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
  
#### <a name="parameters"></a>Parámetros  
 `id`  
 Identifica el miembro. Utiliza `GetDispID` o `GetNextDispID` para obtener el identificador de envío.  
  
 `lcid`  
 Contexto de la configuración regional en que se interpretan los argumentos. El `lcid` se pasa a `InvokeEx` para permitir que el objeto interprete sus argumentos específicos de una configuración regional.  
  
 `wFlags`  
 Los valores válidos para `wFlags` son:  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 Marcas que describen el contexto de la llamada `InvokeEx`:  
  
|Valor|Significado|  
|-----------|-------------|  
|DISPATCH_METHOD|El miembro se invoca como un método. Si una propiedad tiene el mismo nombre, se pueden establecer tanto esta marca como la marca DISPATCH_PROPERTYGET (definida por `IDispatch`).|  
|DISPATCH_PROPERTYGET|El miembro se recupera como una propiedad o miembro de datos (definido por `IDispatch`).|  
|DISPATCH_PROPERTYPUT|El miembro se cambia como una propiedad o miembro de datos (definido por `IDispatch`).|  
|DISPATCH_PROPERTYPUTREF|Una asignación de referencia cambia el miembro en lugar de una asignación de valores. Esta marca solo es válida cuando la propiedad acepta una referencia a un objeto (definido por `IDispatch`).|  
|DISPATCH_CONSTRUCT|El miembro se utiliza como un constructor. (Se trata de un nuevo valor definido por `IDispatchEx`). Los valores válidos para `wFlags` son:<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Puntero a una estructura que contiene una matriz de argumentos, una matriz de valores DISPID de argumento para argumentos con nombre y recuentos del número de elementos de cada matriz. Consulte la documentación de `IDispatch` para obtener una descripción completa de la estructura DISPPARAMS.  
  
 `pVarRes`  
 Puntero a la ubicación donde se va a almacenar el resultado o null si el llamador no espera ningún resultado. Este argumento se omite si se especifica DISPATCH_PROPERTYPUT o DISPATCH_PROPERTYPUTREF.  
  
 `pei`  
 Puntero a una estructura que contiene información de excepciones. Esta estructura se debe rellenar si se devuelve `DISP_E_EXCEPTION`. Puede ser null. Consulte la documentación de `IDispatch` para obtener una descripción completa de la estructura de `EXCEPINFO`.  
  
 `pspCaller`  
 Puntero a un objeto de proveedor de servicios proporcionado por el autor de la llamada, que permite al objeto obtener servicios del llamador. Puede ser null.  
  
 `IDispatchEx::InvokeEx` proporciona las mismas características que `IDispatch::Invoke` y agrega algunas extensiones:  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|Indica que el elemento se utiliza como un constructor.|  
|`pspCaller`|El `pspCaller` permite que el objeto tenga acceso a los servicios proporcionados por el llamador. Los servicios específicos pueden ser controlados por el propio llamador o delegados a los llamadores más arriba en la cadena de llamadas. Por ejemplo, si un motor de scripts dentro de un explorador realiza una llamada `InvokeEx` a un objeto externo, el objeto puede seguir la cadena de `pspCaller` para obtener servicios del motor de script o del explorador. (Tenga en cuenta que la cadena de llamadas no es la misma que la cadena de creación, también conocida como cadena de contenedores o cadena de sitios. La cadena de creación puede estar disponible a través de otro mecanismo, como `IObjectWithSite`).|  
|Puntero `this`|Cuando DISPATCH_METHOD se establece en `wFlags`, puede haber un "parámetro con nombre" para el valor "this". El DISPID será DISPID_THIS y debe ser el primer parámetro con nombre.|  
  
 Se ha quitado el parámetro `riid` sin usar de `IDispatch::Invoke`.  
  
 Se ha quitado el parámetro `puArgArr` en `IDispatch::Invoke`.  
  
 Consulte la documentación de `IDispatch::Invoke` para obtener los ejemplos siguientes:  
  
 "Llamar a un método sin argumentos"  
  
 "Obtener y establecer propiedades"  
  
 "Pasar parámetros"  
  
 "Propiedades indexadas"  
  
 "Provocar excepciones durante la invocación"  
  
 "Devolver errores"  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|||  
|-|-|  
|`S_OK`|Correcto.|  
|DISP_E_BADPARAMCOUNT|El número de elementos proporcionado a DISPPARAMS es diferente del número de argumentos aceptados por el método o la propiedad.|  
|DISP_E_BADVARTYPE|Uno de los argumentos de `rgvarg` no es un tipo Variant válido.|  
|DISP_E_EXCEPTION|La aplicación debe generar una excepción. En este caso, se debe rellenar la estructura pasada en `pei`.|  
|DISP_E_MEMBERNOTFOUND|El miembro solicitado no existe o la llamada a `InvokeEx` intentó establecer el valor de una propiedad de solo lectura.|  
|DISP_E_NONAMEDARGS|Esta implementación de `IDispatch` no admite argumentos con nombre.|  
|DISP_E_OVERFLOW|Uno de los argumentos de `rgvarg` no se pudo convertir al tipo especificado.|  
|DISP_E_PARAMNOTFOUND|Uno de los parámetros DISPID no corresponde a un parámetro del método.|  
|DISP_E_TYPEMISMATCH|No se pudieron convertir uno o varios argumentos.|  
|DISP_E_UNKNOWNLCID|El miembro que se invoca interpreta los argumentos de cadena según el LCID y no se reconoce el LCID. Si el LCID no es necesario para interpretar argumentos, este error no se debe devolver.|  
|DISP_E_PARAMNOTOPTIONAL|Se omitió un parámetro necesario.|  
  
## <a name="example"></a>Ejemplo  
  
```cpp
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
  
## <a name="see-also"></a>Vea también  
 [IDispatchEx (interfaz](../../winscript/reference/idispatchex-interface.md) )    
 [IDispatchEx:: GetDispID](../../winscript/reference/idispatchex-getdispid.md)    
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)