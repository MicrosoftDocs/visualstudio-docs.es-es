---
title: "Serializaci&#243;n de par&#225;metros de ensamblado de interoperabilidad de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "solucionar problemas de ensamblados de interoperabilidad de SDK de Visual Studio"
  - "ensamblados de interoperabilidad, serialización de parámetros"
  - "ensamblados de interoperabilidad, solución de problemas"
ms.assetid: 89123eae-0fef-46d5-bd36-3d2a166b14e3
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# Serializaci&#243;n de par&#225;metros de ensamblado de interoperabilidad de Visual Studio
VSPackages que se escribe en código administrado se podría tener que llamar a o llamar mediante código COM no administrados.  Normalmente, los argumentos de método se transformen, o formados, automáticamente el contador de referencias de interoperabilidad.  Sin embargo, los argumentos no se pueden transformar en ocasiones de manera sencilla.  En esos casos, los parámetros del prototipo del ensamblado de interoperabilidad se usan para buscar los parámetros COM de la función lo posible.  Para obtener más información, vea [Interop Marshaling](../Topic/Interop%20Marshaling.md).  
  
## sugerencias generales  
  
##### lea la documentación de referencia  
 Una manera eficaz de detectar problemas de interoperabilidad es leer la documentación de referencia para cada método.  
  
 Documentación de referencia para cada método contiene tres secciones importantes:  
  
-   el prototipo COM de la función de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] .  
  
-   El prototipo del ensamblado de interoperabilidad.  
  
-   Una lista de los parámetros COM y una breve descripción de cada uno.  
  
##### busque las diferencias entre los dos prototipos  
 La mayoría de los problemas de interoperabilidad se derivan de los casos entre la definición de un tipo determinado en una interfaz COM y la definición del mismo tipo en los ensamblados de interoperabilidad de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  por ejemplo, considere la diferencia en la capacidad de pasar un valor de `null` en \[out\] un parámetro.  Debe buscar diferencias entre los dos prototipos y ver las ramificaciones para los datos que se pasan.  
  
##### Lea las definiciones de parámetro  
 Lea las definiciones de parámetro.  COM es menos estricto que Common Language \(CLR\) Runtime sobre mezclar diferentes tipos de datos en un solo parámetro.  Las interfaces COM de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usen completo de esta flexibilidad.  Cualquier parámetro que puede pasar o requiere un valor no estándar o tipo de datos, como un valor constante en un parámetro de puntero, debe describir como tales en la documentación.  
  
### Objetos de IUnknown pasados como tipo void \*\*  
 Busque \[out\] los parámetros que se definen como `void **` escrito en la interfaz COM, pero que está definido como `[``iid_is``]` en el prototipo del ensamblado de interoperabilidad de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  
  
 A veces, una interfaz COM genera un objeto de `IUnknown` , y la interfaz COM se pasa como `void **`escrito.  Estas interfaces son especialmente importantes porque si la variable se define como \[out\] en el archivo IDL, el objeto de `IUnknown` referencia\-se cuenta con el método de `AddRef` .  Una pérdida de memoria aparece si el objeto no se controla correctamente.  
  
> [!NOTE]
>  Un objeto de `IUnknown` creado por la interfaz COM y devuelto en \[out\] una variable provoca una pérdida de memoria si no se libera.  
  
 Los métodos administrados que controlan estos objetos deben tratar <xref:System.IntPtr> como un puntero a un objeto de `IUnknown` , y llama al método de <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> para obtener el objeto.  El llamador debe a convertir el valor devuelto a aquello que sea adecuado.  Cuando el objeto ya no se necesite, llame a <xref:System.Runtime.InteropServices.Marshal.Release%2A> para liberarlo.  
  
 A continuación se muestra un ejemplo de llamada al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> y administrar el objeto de `IUnknown` correctamente:  
  
```  
MyClass myclass;  
Object object;  
IntPtr pObj;  
Guid iid = Typeof(MyClass).Guid;  
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);     
if (NativeMethods.Succeeded(hr))   
{  
    try   
    {  
        object = Marshal.GetObjectForIUnknown(pObj);  
        myclass = object;  
    }  
    finally   
    {  
        Marshal.Release(pObj);  
    }  
}  
else   
{  
    // error calling QueryViewInterface  
}  
```  
  
> [!NOTE]
>  Los métodos siguientes se sabe que pasar punteros de objeto de `IUnknown` como <xref:System.IntPtr>escrito.  Manéjelos como se describe en esta sección.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
### parámetros \[out\] opcionales  
 Busque los parámetros que se definen como \[out\] tipo de datos \(`int`, `object`, etc.\) en la interfaz COM, pero que está definido como matrices del mismo tipo de datos en el prototipo del ensamblado de interoperabilidad de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  
  
 Algunas interfaces COM, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, tratan \[out\] parámetros como opcionales.  Si un objeto no se requiere, estas interfaces COM devuelven un puntero de `null` como valor del parámetro en lugar de crear \[out\] el objeto.  Esto es intencionado.  Para estas interfaces, punteros de `null` se supone como parte del comportamiento correcto de VSPackage, y no se devuelve ningún error.  
  
 Porque CLR no permite que el valor \[out\] de un parámetro es `null`, la parte del comportamiento diseñado de estas interfaces no es directamente disponibles en código administrado.  Los métodos del ensamblado de interoperabilidad de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para las interfaces afectadas funcionan alrededor del problema definiendo los parámetros pertinentes como matrices porque CLR permite pasar de las matrices de `null` .  
  
 Las implementaciones administradas de estos métodos deben colocar una matriz de `null` en el parámetro cuando no hay nada volver.  Si no, cree una matriz de un elemento del tipo correcto y coloque el valor devuelto en la matriz.  
  
 Los métodos administrados que reciben información de interfaces con parámetros opcionales \[out\] reciben el parámetro como una matriz.  Simplemente examine el valor del primer elemento de la matriz.  si no es `null`, trate el primer elemento como si fuera el parámetro original.  
  
### Pasar constantes en parámetros de puntero  
 Busque los parámetros que se definen como \[in\] punteros de la interfaz COM, pero que son definido como <xref:System.IntPtr> escribir en el prototipo del ensamblado de interoperabilidad de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  
  
 Un problema similar se produce cuando una interfaz COM pasa un valor especial, como 0, \-1, o – 2, en lugar de un puntero de objeto.  A diferencia de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], CLR no permite que las constantes son conversión como objetos.  En su lugar, el ensamblado de interoperabilidad de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] define el parámetro como un tipo de <xref:System.IntPtr> .  
  
 Las implementaciones administradas de estos métodos deben aprovechar el hecho de que la clase de <xref:System.IntPtr> tiene `int` y constructores de `void *` para crear <xref:System.IntPtr> de un objeto o una constante entera, según corresponda.  
  
 Los métodos administrados que reciben los parámetros de <xref:System.IntPtr> de este tipo deben utilizar los operadores de conversión de tipos de <xref:System.IntPtr> para controlar los resultados.  Convertir primero <xref:System.IntPtr> a `int` y pruébelo con constantes enteras pertinentes.  Si coinciden con ningún valor, de un objeto de tipo necesario y continúe.  
  
 Para obtener ejemplos de esto, vea el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> y el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.  
  
### Valores devueltos de OLE pasados como \[out\] parámetros  
 Busque los métodos que tienen un valor devuelto de `retval` en la interfaz COM, pero que tienen un valor devuelto de `int` y un parámetro adicional \[out\] de matriz en el prototipo del ensamblado de interoperabilidad de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  Debe estar claro que estos métodos requieren un control especial porque los prototipos del ensamblado de interoperabilidad de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tienen un más parámetros que los métodos de interfaz COM.  
  
 Las interfaces COM que se encargan de actividad OLE envían información sobre el estado Y de nuevo al programa de llamada almacenado en el valor devuelto de `retval` de interfaz.  En lugar de utilizar un valor devuelto, los métodos correspondientes del ensamblado de interoperabilidad de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] envían la información al programa de llamada almacenado en \[out\] un parámetro de matriz.  
  
 Las implementaciones administradas de estos métodos deben crear una matriz de solo\-elemento del mismo tipo que \[out\] el parámetro y colocarlo en el parámetro.  El valor del elemento de matriz debe ser igual que `retval`COM adecuado.  
  
 Los métodos administrados que llaman interfaces de este tipo deben sacar del primer elemento \[out\] de la matriz.  Este elemento puede tratar como si fuera un valor devuelto de `retval` de interfaz COM correspondiente.  
  
## Vea también  
 [Interop Marshaling](http://msdn.microsoft.com/es-es/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Interop Marshaling](../Topic/Interop%20Marshaling.md)   
 [Solución de problemas de interoperabilidad](/dotnet/visual-basic/programming-guide/com-interop/troubleshooting-interoperability)   
 [VSPackages administrado](../misc/managed-vspackages.md)