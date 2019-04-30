---
title: IDispatchEx (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispatchEx interface, about IDispatchEx
- IDispatchEx interface
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df3fd7d46fdcb1f3e86bddd53700d7bce6e21381
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000839"
---
# <a name="idispatchex-interface"></a>IDispatchEx (Interfaz)
`IDispatchEx`, una extensión de la `IDispatch` admite características de interfaz, adecuados para lenguajes dinámicos como lenguajes de scripting. Esta sección se describe la `IDispatchEx` interfaz propia, las diferencias entre `IDispatch` y `IDispatchEx`y el razonamiento de las extensiones. Se espera que los lectores están familiarizados con `IDispatch` y tener acceso a la `IDispatch` documentación.  
  
## <a name="remarks"></a>Comentarios  
 `IDispatch` Básicamente, se desarrolló para Microsoft Visual Basic. La principal limitación de `IDispatch` es que se supone que los objetos son estáticos. En otras palabras, puesto que los objetos no cambian durante el tiempo de ejecución, información de tipo puede describir completamente ellos en tiempo de compilación. Los modelos de tiempo de ejecución dinámicos que se encuentran en lenguajes como Visual Basic Scripting Edition (VBScript) y [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] y modelos de objeto como HTML dinámico requieren una interfaz más flexible.  
  
 `IDispatchEx` se desarrolló para proporcionar todos los servicios de `IDispatch` , así como algunas extensiones que sean adecuados para los lenguajes de tiempo de ejecución más dinámicos como lenguajes de scripting. Las características adicionales de `IDispatchEx` más allá de los proporcionados por `IDispatch` son:  
  
- Agregar nuevos miembros a un objeto ("expando"), utilice `GetDispID` con el `fdexNameEnsure` marca.  
  
- Eliminar miembros de un objeto, utilice `DeleteMemberByName` o `DeleteMemberByDispID`.  
  
- Las operaciones de envío entre mayúsculas y minúsculas, utilice `fdexNameCaseSensitive` o `fdexNameCaseInsensitive`.  
  
- Búsqueda de miembros con nombre implícito, utilice `fdexNameImplicit`.  
  
- Enumerar envío (DISPID) de un objeto, utilice `GetNextDispID`.  
  
- Mapa de DISPID al nombre de elemento, utilice `GetMemberName`.  
  
- Obtener propiedades de los miembros de objeto, utilice `GetMemberProperties`.  
  
- Invocación de método con `this` puntero: usar `InvokeEx` con DISPATCH_METHOD.  
  
- Permitir que los exploradores que admiten el concepto de espacios de nombres para obtener el elemento primario de espacio de nombre de un objeto, utilice `GetNameSpaceParent`.  
  
  Los objetos que admiten `IDispatchEx` también podría admitir `IDispatch` para compatibilidad con versiones anteriores. La naturaleza dinámica de objetos que admiten `IDispatchEx` tiene algunas implicaciones para el `IDispatch` interfaz de dichos objetos. Por ejemplo, `IDispatch` hace que las hipótesis siguientes:  
  
- El miembro y el parámetro DISPID debe permanecer constante durante la vigencia del objeto. Esto permite que un cliente obtener el DISPID una vez y almacenarlos en memoria caché para su uso posterior.  
  
  Puesto que `IDispatchEx` permite la adición y eliminación de miembros, el conjunto de identificadores DispId válido no permanezca constante. Sin embargo, `IDispatchEx` requiere que la asignación entre el nombre de miembro y DISPID permanezca constante. Esto significa que si se elimina un miembro:  
  
- No se puede reutilizar el identificador de envío hasta que se crea un miembro con el mismo nombre.  
  
- El identificador DISPID debe seguir siendo válido para `GetNextDispID`.  
  
- El DISPID debe ser aceptado correctamente mediante cualquiera de los `IDispatch` o `IDispatchEx` métodos, se debe reconocer el miembro como eliminada y devolver un código de error adecuado (normalmente DISP_E_MEMBERNOTFOUND o S_FALSE).  
  
## <a name="examples"></a>Ejemplos  
 Esto [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] código en la función de test() hace lo siguiente:  
  
- Crea un nuevo objeto mediante una llamada a la `Object` constructor y le asigna un puntero al nuevo objeto a la variable obj.  
  
- Crea un nuevo elemento denominado Elem en el objeto y se asigna a este elemento de un puntero a la cat de función.  
  
- Llama a esta función. Puesto que se llama como un método, el `this` puntero hace referencia al objeto obj. La función agrega un nuevo elemento, barra al objeto.  
  
  El código HTML completo es:  
  
```html
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
  
function test()  
{  
   // Construct new object  
   Obj = new Object();  
  
   // Create new element and assign function pointer  
   Obj.Elem = cat;  
  
   // Call Elem method ("this" == Obj)  
   Obj.Elem();  
  
   // Obj.Bar now exists  
}  
test();  
</script>  
</body>  
</html>  
```  
  
 Un control que se coloca en esta misma página Web pudo obtener un puntero de envío para los motores de script desde el explorador. El control, a continuación, podría implementar test() de la función:  
  
```html
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
</script>  
<object id="test" <CLASSID="CLSID:9417DB5D-FA2A-11D0-8CB3-00C04FC2B085">>  
</object>  
</body>  
</html>  
```  
  
 Desde el control de código, probar, hace lo mismo que el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] función `test()`. Tenga en cuenta que estas llamadas de envío se realizan en el que se ejecuta [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] del motor y cambiar el estado del motor de:  
  
- Obtiene el puntero de envío a la función cat mediante `GetDispID()`.  
  
- Obtiene el puntero de envío para el objeto de función mediante `GetDispID()`.  
  
- Crea un objeto mediante una llamada a la función del objeto con `InvokeEx()` y obtiene un puntero de envío para el objeto recién creado.  
  
- Crea un nuevo elemento, Elem, en el objeto con `GetDispID()` con el `fdexNameEnsure` marca.  
  
- Coloca el puntero de envío a cat en el elemento mediante `InvokeEx()`.  
  
- Llama al puntero de envío a cat como un método mediante una llamada a `InvokeEx()` y pasar el puntero de envío para el objeto construido, como el `this` puntero.  
  
- El método cat crea un nuevo elemento, barras, en la actual `this` objeto.  
  
- Comprueba que el nuevo elemento, barras, se creó en el objeto construido mediante la enumeración a través de los elementos mediante `GetNextDispID()`.  
  
  El código para el control de prueba:  
  
```cpp
   BOOL test(IDispatchEx *pdexScript)  
   {  
      HRESULT hr;  
      VARIANT var;  
      DISPID dispid, putid;  
      BOOL retval = FALSE;  
      BSTR bstrName = NULL;  
      IDispatch   *pdispObj = NULL, *pdispCat = NULL;  
      IDispatchEx *pdexObj = NULL;  
      DISPPARAMS dispparams, dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
      // Get dispatch pointer for "cat"  
      bstrName = SysAllocString(OLESTR("cat"));  
         if (bstrName == NULL) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispCat = var.pdispVal;  
  
      // Create object by calling "Object" constructor  
      bstrName = SysAllocString(OLESTR("Object"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_CONSTRUCT, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispObj = var.pdispVal;  
      hr = pdispObj->QueryInterface(IID_IDispatchEx, (void **)&pdexObj);  
         if (FAILED(hr)) goto LDone;  
  
      // Create new element in object  
      bstrName = SysAllocString(OLESTR("Elem"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexObj->GetDispID(bstrName, fdexNameEnsure, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
  
      // Assign "cat" dispatch pointer to element  
      putid = DISPID_PROPERTYPUT;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispCat;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYPUTREF, &dispparams,  
         NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Invoke method with "this" pointer  
      putid = DISPID_THIS;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispObj;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_METHOD, &dispparams,  
            NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Confirm that new element "Bar" is in object  
      hr = pdexObj->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
      while (hr == NOERROR)  
      {  
            hr = pdexObj->GetMemberName(dispid, &bstrName);  
            if (FAILED(hr)) goto LDone;  
            retval = !wcscmp(bstrName, OLESTR("Bar"));  
            SysFreeString(bstrName);  
            bstrName = NULL;  
            if (retval) goto LDone;  
         hr = pdexObj->GetNextDispID(fdexEnumAll, dispid, &dispid);  
      }  
LDone:  
   SysFreeString(bstrName);  
   if (pdispCat != NULL)  
      pdispCat->Release();  
   if (pdispObj != NULL)  
      pdispObj->Release();  
   if (pdexObj != NULL)  
      pdexObj->Release();  
  
   return retval;  
   }  
```  
  
## <a name="methods"></a>Métodos  
 [IDispatchEx (Métodos)](../../winscript/reference/idispatchex-methods.md)