---
title: "IDispatchEx (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDispatchEx (interfaz)"
  - "IDispatchEx (interfaz), acerca de IDispatchEx"
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDispatchEx (Interfaz)
`IDispatchEx`, una extensión de la interfaz de `IDispatch` , admite representa adecuado para los lenguajes dinámicos como lenguajes de scripting.  Esta sección describe la propia interfaz de `IDispatchEx` , las diferencias entre `IDispatch` y `IDispatchEx`, y la razón de las extensiones.  Se espera que los lectores están familiarizados con `IDispatch` y tienen acceso a la documentación de `IDispatch` .  
  
## Comentarios  
 `IDispatch` se desarrolló básicamente para Microsoft Visual Basic.  La limitación principal de `IDispatch` es que supone que los objetos son estáticos.  Es decir puesto que los objetos no cambian durante el tiempo de ejecución, la información de tipo puede describirlos completamente en tiempo de compilación.  Los modelos dinámicos en tiempo de ejecución que se encuentran en los lenguajes de scripting como Visual Basic scripting edition \(VBScript\) y [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] y los modelos de objetos como HTML dinámico requieren una interfaz más flexible.  
  
 `IDispatchEx` se desarrolló para proporcionar todos los servicios de `IDispatch` así como de algunas extensiones que son adecuados para lenguajes tarde\- enlazados más dinámicos como lenguajes de scripting.  Características adicionales de `IDispatchEx` más allá de los proporcionados por `IDispatch` son:  
  
-   Agregue nuevos miembros a un objeto \(“expando”\) utilizan `GetDispID` con el marcador de `fdexNameEnsure` .  
  
-   Eliminar los miembros de un objeto `DeleteMemberByName` uso o `DeleteMemberByDispID`.  
  
-   Operación\- uso con distinción entre mayúsculas y minúsculas `fdexNameCaseSensitive` o `fdexNameCaseInsensitive`de envío.  
  
-   Buscar el miembro con el nombre\- uso implícito `fdexNameImplicit`.  
  
-   Mostrar identificadores dispid de un objeto `GetNextDispID`uso.  
  
-   Mapa de DISPID al nombre\- uso `GetMemberName`del elemento.  
  
-   Obtiene las propiedades de miembro\- uso `GetMemberProperties`del objeto.  
  
-   Invocación de método con el puntero\-uso `InvokeEx` de `this` con DISPATCH\_METHOD.  
  
-   Permite a los exploradores que admiten el concepto de espacios de nombres que obtiene el elemento primario del espacio de nombres de objeto un uso `GetNameSpaceParent`.  
  
 Objetos que `IDispatchEx` admiten también podría admitir `IDispatch` para la compatibilidad con versiones anteriores.  La naturaleza dinámica de los objetos que `IDispatchEx` admiten tiene algunas implicaciones para la interfaz de `IDispatch` de esos objetos.  Por ejemplo, `IDispatch` crea la hipótesis siguiente:  
  
-   El miembro y el parámetro Identificadores deben permanecer constantes para la duración del objeto.  Esto permite que un cliente obtenga Dispid una vez y los almacena en memoria caché para su uso posterior.  
  
 Puesto que `IDispatchEx` permite la adición y eliminación de miembros, el conjunto de identificadores dispid válido no sigue siendo constante.  Sin embargo, `IDispatchEx` requiere que la asignación entre DISPID y el nombre de miembro permanezca constante.  Esto significa que si se elimina un miembro:  
  
-   El identificador de envío no puede reutilizar hasta que crean un miembro con el mismo nombre.  
  
-   El identificador de envío debe seguir siendo válido para `GetNextDispID`.  
  
-   El identificador de envío se debe aceptar correctamente por `IDispatch` cualquiera de los o `IDispatchEx` que método\- deben reconocer el miembro como eliminado y devolver un código de error adecuado \(normalmente DISP\_E\_MEMBERNOTFOUND o S\_FALSE\).  
  
## Ejemplos  
 Este [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] codificadas en pruebas de función \(\) hace lo siguiente:  
  
-   Crea un nuevo objeto llamando al constructor de `Object` y asigna un puntero al nuevo objeto a la variable Obj.  
  
-   Crea un nuevo elemento denominado Elem en el objeto y las asignaciones a este elemento un puntero al gatos de la función.  
  
-   Llama a esta función.  Puesto que se llama al método, el puntero de `this` hace referencia al objeto Obj.  La función agrega un nuevo elemento, barra, al objeto.  
  
 El código HTML completo es:  
  
```  
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
  
 Un control título en esta misma página Web puede obtener un puntero de envío para los motores de script del explorador.  El control podría implementar pruebas de función \(\):  
  
```  
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
  
 El código del control, prueba, hace lo mismo que la función `test()`de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  Observe que estas llamadas send se realizadas en el motor de ejecución de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] y cambiar el estado del motor:  
  
-   Obtiene el puntero de envío a la función de gatos mediante `GetDispID()`.  
  
-   Obtiene el puntero de envío a la función de objetos mediante `GetDispID()`.  
  
-   Construye un objeto llamando a la función del objeto con `InvokeEx()` y obtiene un puntero de envío al objeto recientemente construido.  
  
-   Crea un nuevo elemento, Elem, en el objeto con `GetDispID()` con el marcador de `fdexNameEnsure` .  
  
-   Coloca el puntero de envío al gatos en el elemento utilizando `InvokeEx()`.  
  
-   Llama al puntero de envío al gatos como método llamando a `InvokeEx()` y pasando el puntero de envío al objeto construido como el puntero de `this` .  
  
-   El método de gatos crea un nuevo elemento, barra, con el objeto actual de `this` .  
  
-   Comprueba que el nuevo elemento, barra, se creó en el objeto construido enumerando a través de los elementos mediante `GetNextDispID()`.  
  
 El código del control de pruebas:  
  
```  
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
  
## Métodos  
 [IDispatchEx \(Métodos\)](../../winscript/reference/idispatchex-methods.md)