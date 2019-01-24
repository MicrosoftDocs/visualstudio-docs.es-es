---
title: IDispatchEx::InvokeEx | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: e631ecca1181a25fa3cf419f5fc96666f0db3cd6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086533"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Proporciona acceso a propiedades y métodos expuestos por un `IDispatchEx` objeto.  
  
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
 Identifica el miembro. Usa `GetDispID` o `GetNextDispID` para obtener el identificador de envío.  
  
 `lcid`  
 Contexto de la configuración regional en que se interpretan los argumentos. El `lcid` se pasa a `InvokeEx` para permitir que el objeto interpretar sus argumentos a una configuración regional específicas.  
  
 `wFlags`  
 Los valores legales `wFlags` son:  
  
 DISPATCH_PROPERTYGET &AMP;#124; DISPATCH_METHOD &AMP;#124; DISPATCH_PROPERTYPUT &AMP;#124; DISPATCH_PROPERTYPUTREF &AMP;#124; DISPATCH_CONSTRUCT  
  
 Marcas que describen el contexto de la `InvokeEx` llamar:  
  
|Valor|Significado|  
|-----------|-------------|  
|DISPATCH_METHOD|Se invoca el miembro como un método. Si una propiedad tiene el mismo nombre, se puede establecer este valor y la marca DISPATCH_PROPERTYGET (definida por `IDispatch`).|  
|DISPATCH_PROPERTYGET|El miembro se recupera como una propiedad o miembro de datos (definidos por `IDispatch`).|  
|DISPATCH_PROPERTYPUT|El miembro se cambia como una propiedad o miembro de datos (definidos por `IDispatch`).|  
|DISPATCH_PROPERTYPUTREF|El miembro se cambia por una asignación de referencia en lugar de una asignación de valor. Esta marca solo es válida cuando la propiedad acepta una referencia a un objeto (definido por `IDispatch`).|  
|DISPATCH_CONSTRUCT|El miembro que se sirve como un constructor. (Se trata de un nuevo valor definido `IDispatchEx`). Los valores legales `wFlags` son:<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Puntero a una estructura que contiene una matriz de argumentos, una matriz de valores DISPID de argumento para argumentos con nombre y recuentos del número de elementos de cada matriz. Consulte la `IDispatch` documentación para obtener una descripción completa de la estructura DISPPARAMS.  
  
 `pVarRes`  
 Puntero a la ubicación donde es el resultado almacenado o Null si el llamador no espera ningún resultado. Este argumento se omite si se especifica DISPATCH_PROPERTYPUT o DISPATCH_PROPERTYPUTREF.  
  
 `pei`  
 Puntero a una estructura que contiene información de excepciones. Debe estar rellena esta estructura si `DISP_E_EXCEPTION` se devuelve. Puede ser Null. Consulte la `IDispatch` documentación para obtener una descripción completa de la `EXCEPINFO` estructura.  
  
 `pspCaller`  
 Puntero a un objeto de proveedor de servicio proporcionado por el llamador, que permite que el objeto obtener los servicios desde el llamador. Puede ser Null.  
  
 `IDispatchEx::InvokeEx` las mismas características que proporciona `IDispatch::Invoke` y agrega algunas extensiones:  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|Indica que se está usando el elemento como un constructor.|  
|`pspCaller`|El `pspCaller` permite el acceso a objetos a los servicios proporcionados por el llamador. Servicios específicos pueden controlarse por el autor de la llamada o delegar a los llamadores aún más la cadena de llamada. Por ejemplo, si un motor de scripts dentro de un explorador realiza una `InvokeEx` llamada a un objeto externo, el objeto puede seguir el `pspCaller` cadena para obtener los servicios desde el motor de scripts o el explorador. (Tenga en cuenta que la cadena de llamada no es igual que la cadena de creación, también conocido como cadena de contenedor o la cadena de sitio. La cadena de creación puede estar disponible a través de algún otro mecanismo, como `IObjectWithSite`.)|  
|Puntero `this`|Cuando se establece DISPATCH_METHOD `wFlags`, puede haber un "parámetro con nombre" para el valor de "this". El identificador DISPID será DISPID_THIS y debe ser el primer parámetro con nombre.|  
  
 Los no usados `riid` parámetro `IDispatch::Invoke` se ha quitado.  
  
 El `puArgArr` parámetro `IDispatch::Invoke` se ha quitado.  
  
 Consulte la `IDispatch::Invoke` documentación para los ejemplos siguientes:  
  
 "Llamar a un método sin argumentos"  
  
 "Obtener y establecer las propiedades"  
  
 "Pasar parámetros"  
  
 "Propiedades indizadas"  
  
 "Generar excepciones durante la invocación"  
  
 "Devolver errores"  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|||  
|-|-|  
|`S_OK`|Correcto.|  
|DISP_E_BADPARAMCOUNT|El número de elementos proporcionados al DISPPARAMS es diferente del número de argumentos aceptado por el método o propiedad.|  
|DISP_E_BADVARTYPE|Uno de los argumentos en `rgvarg` no es un tipo variant válido.|  
|DISP_E_EXCEPTION|La aplicación debe generar una excepción. En este caso, la estructura pasada en `pei` debe rellenarse.|  
|DISP_E_MEMBERNOTFOUND|El miembro solicitado no existe, o la llamada a `InvokeEx` intentó establecer el valor de una propiedad de solo lectura.|  
|DISP_E_NONAMEDARGS|Esta implementación de `IDispatch` no admite argumentos con nombre.|  
|DISP_E_OVERFLOW|Uno de los argumentos en `rgvarg` no pudo convertirse al tipo especificado.|  
|DISP_E_PARAMNOTFOUND|Uno de los parámetros de envío (DISPID) no corresponde a un parámetro del método.|  
|DISP_E_TYPEMISMATCH|No se pudieran convertir uno o varios de los argumentos.|  
|DISP_E_UNKNOWNLCID|El miembro que se invoca interpreta los argumentos de cadena de acuerdo con el LCID, y no se reconoce el LCID. Si el LCID no es necesaria para interpretar argumentos, no se debe devolver este error.|  
|DISP_E_PARAMNOTOPTIONAL|Se ha omitido un parámetro obligatorio.|  
  
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
 [IDispatchEx (interfaz)](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)