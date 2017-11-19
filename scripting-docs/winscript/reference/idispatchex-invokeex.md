---
title: IDispatchEx::InvokeEx | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispatchEx.InvokeEx
apilocation: scrobj.dll
helpviewer_keywords: InvokeEx method
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6302228b110e2b0a6296190079bf60b3d92980bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Proporciona acceso a propiedades y métodos expuestos por un `IDispatchEx` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 `id`  
 Identifica el miembro. Usa `GetDispID` o `GetNextDispID` para obtener el identificador de envío.  
  
 `lcid`  
 Contexto de la configuración regional en que se interpretan los argumentos. El `lcid` se pasa a `InvokeEx` para permitir que el objeto que se va a interpretar sus argumentos específicos de una configuración regional.  
  
 `wFlags`  
 Los valores legales `wFlags` son:  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 Marcas que describen el contexto de la `InvokeEx` llamar:  
  
|Valor|Significado|  
|-----------|-------------|  
|DISPATCH_METHOD|Se invoca el miembro como un método. Si una propiedad tiene el mismo nombre, se puede establecer este valor y el indicador DISPATCH_PROPERTYGET (definida por `IDispatch`).|  
|DISPATCH_PROPERTYGET|El miembro se recupera como un propiedad o miembro de datos (definida por `IDispatch`).|  
|DISPATCH_PROPERTYPUT|Se cambia el miembro como un propiedad o miembro de datos (definida por `IDispatch`).|  
|DISPATCH_PROPERTYPUTREF|El miembro se modifica una asignación de referencia en lugar de una asignación de valor. Esta marca solo es válida cuando la propiedad acepta una referencia a un objeto (definido por `IDispatch`).|  
|DISPATCH_CONSTRUCT|Se está utilizando el miembro como un constructor. (Se trata de un nuevo valor definido por `IDispatchEx`). Los valores legales `wFlags` son:<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Puntero a una estructura que contiene una matriz de argumentos, una matriz de valores DISPID de argumento para argumentos con nombre y recuentos del número de elementos de cada matriz. Consulte la `IDispatch` documentación para obtener una descripción completa de la estructura DISPPARAMS.  
  
 `pVarRes`  
 Puntero a la ubicación donde está el resultado almacenado o Null si el llamador espera que ningún resultado. Este argumento se omite si se especifica DISPATCH_PROPERTYPUT o DISPATCH_PROPERTYPUTREF.  
  
 `pei`  
 Puntero a una estructura que contiene información de excepciones. Esta estructura debe rellenarse if `DISP_E_EXCEPTION` se devuelve. Puede ser Null. Consulte la `IDispatch` documentación para obtener una descripción completa de la `EXCEPINFO` estructura.  
  
 `pspCaller`  
 Puntero a un objeto de proveedor de servicio proporcionado por el llamador, que permite que el objeto obtener servicios desde el llamador. Puede ser Null.  
  
 `IDispatchEx::InvokeEx`proporciona todas las características `IDispatch::Invoke` y agrega algunas extensiones:  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|Indica que el elemento se está utilizando como constructor.|  
|`pspCaller`|El `pspCaller` permite el acceso a objetos a los servicios proporcionados por el llamador. Servicios específicos que podrán estar controlados por el autor de llamada o delegados a los llamadores aún más la cadena de llamada. Por ejemplo, si un motor de scripts dentro de un explorador realiza una `InvokeEx` llamada a un objeto externo, el objeto puede seguir el `pspCaller` cadena para obtener servicios desde el motor de scripts o el Examinador. (Tenga en cuenta que la cadena de llamada no es igual que la cadena de creación, también conocido como cadena de contenedor o la cadena de sitio. La cadena de creación puede estar disponible a través de algún otro mecanismo como `IObjectWithSite`.)|  
|Puntero `this`|Cuando se establece DISPATCH_METHOD `wFlags`, puede haber un "parámetro con nombre" para el valor de "this". El identificador DISPID será DISPID_THIS y debe ser el primer parámetro con nombre.|  
  
 El sin usar `riid` parámetro `IDispatch::Invoke` se ha quitado.  
  
 El `puArgArr` parámetro `IDispatch::Invoke` se ha quitado.  
  
 Consulte la `IDispatch::Invoke` documentación en los ejemplos siguientes:  
  
 "Llamar a un método sin argumentos"  
  
 "Obtener y establecer propiedades"  
  
 "Pasar parámetros"  
  
 "Propiedades indizadas"  
  
 "Generar excepciones durante la invocación"  
  
 "Devolver errores"  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|||  
|-|-|  
|`S_OK`|Correcto.|  
|DISP_E_BADPARAMCOUNT|El número de elementos que se proporcionan para DISPPARAMS es diferente del número de argumentos aceptado por el método o propiedad.|  
|DISP_E_BADVARTYPE|Uno de los argumentos en `rgvarg` no es un tipo variant válido.|  
|DISP_E_EXCEPTION|La aplicación necesita generar una excepción. En este caso, la estructura se pasa en `pei` debe rellenarse.|  
|DISP_E_MEMBERNOTFOUND|El elemento solicitado no existe, o la llamada a `InvokeEx` se intentó establecer el valor de una propiedad de solo lectura.|  
|DISP_E_NONAMEDARGS|Esta implementación de `IDispatch` no admite argumentos con nombre.|  
|DISP_E_OVERFLOW|Uno de los argumentos en `rgvarg` no pudo convertirse al tipo especificado.|  
|DISP_E_PARAMNOTFOUND|Uno de los parámetros de envío (DISPID) no se corresponde con un parámetro del método.|  
|DISP_E_TYPEMISMATCH|No se pudieran convertir uno o varios de los argumentos.|  
|DISP_E_UNKNOWNLCID|El miembro invocado interpreta argumentos de cadena de acuerdo con el LCID, y no se reconoce el LCID. Si no se necesita el LCID se interpretan los argumentos, no debe aparecer este error.|  
|DISP_E_PARAMNOTOPTIONAL|Se ha omitido un parámetro obligatorio.|  
  
## <a name="example"></a>Ejemplo  
  
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
  
## <a name="see-also"></a>Vea también  
 [IDispatchEx (interfaz)](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)