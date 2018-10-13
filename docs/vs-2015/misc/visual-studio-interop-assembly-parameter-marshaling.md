---
title: Parámetro de ensamblado de interoperabilidad de Visual Studio el cálculo de referencias | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting Visual Studio SDK interop assemblies
- interop assemblies, parameter marshaling
- interop assemblies, troubleshooting
ms.assetid: 89123eae-0fef-46d5-bd36-3d2a166b14e3
caps.latest.revision: 24
manager: douge
ms.openlocfilehash: e18667adb48f565f73acc14f5012f9c96283efe9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195024"
---
# <a name="visual-studio-interop-assembly-parameter-marshaling"></a>Serialización de parámetros de ensamblado de interoperabilidad de Visual Studio
Los VSPackages que están escritos en código administrado que tenga que llamar o llamar a código COM no administrado. Normalmente, argumentos de método se transforman o serializar automáticamente por el serializador de interoperabilidad. Sin embargo, en ocasiones, no se puede transformar los argumentos de una manera sencilla. En esos casos, se usan los parámetros del prototipo de método de ensamblado de interoperabilidad para que coincida con los parámetros de función COM lo máximo posible. Para obtener más información, consulte [interoperativo](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).  
  
## <a name="general-suggestions"></a>Sugerencias generales  
  
##### <a name="read-the-reference-documentation"></a>Lea la documentación de referencia  
 Es una forma eficaz para detectar problemas de interoperabilidad leer la documentación de referencia para cada método.  
  
 La documentación de referencia para cada método contiene tres secciones pertinentes:  
  
-   El [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] prototipo de función COM.  
  
-   El prototipo de método del ensamblado de interoperabilidad.  
  
-   Una lista de los parámetros de COM y una breve descripción de cada uno.  
  
##### <a name="look-for-differences-between-the-two-prototypes"></a>Ver las diferencias entre los dos prototipos  
 La mayoría de los problemas de interoperabilidad se derivan de las diferencias entre la definición de un tipo determinado en una interfaz COM y la definición del mismo tipo en el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ensamblados de interoperabilidad. Por ejemplo, considere la diferencia en la capacidad para pasar un `null` valor en un parámetro [out]. Debe ver las diferencias entre los dos prototipos y tenga en cuenta sus consecuencias para los datos que se pasa.  
  
##### <a name="read-the-parameter-definitions"></a>Leer las definiciones de parámetro  
 Leer las definiciones de parámetro. COM es menos estricta que common language runtime (CLR) sobre la combinación de distintos tipos de datos en un único parámetro. El [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfaces COM aprovechan al máximo esta flexibilidad. Cualquier parámetro que se puede pasar o requieren un valor no estándar o el tipo de datos, como un valor constante en un parámetro de puntero, debería describirse como tal en la documentación.  
  
### <a name="iunknown-objects-passed-as-type-void"></a>Los objetos pasan a IUnknown como tipo void **  
 Buscar [los parámetros que se definen como tipo out] `void **` en COM, interfaz, pero que se definen como `[``iid_is``]` en el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototipo de método del ensamblado de interoperabilidad.  
  
 A veces, una interfaz COM genera una `IUnknown` objeto y la interfaz COM, a continuación, se pasa como tipo `void **`. Estas interfaces son especialmente importantes porque si la variable se define como [out] en el archivo IDL, el `IUnknown` objeto es el recuento de referencias con el `AddRef` método. Si el objeto no se controla correctamente, se produce una pérdida de memoria.  
  
> [!NOTE]
>  Un `IUnknown` objeto creado por la interfaz COM y devuelto en una variable [out] provoca una pérdida de memoria si no se libera explícitamente.  
  
 Deben tratar los métodos administrados que administran dichos objetos <xref:System.IntPtr> como un puntero a un `IUnknown` de objetos y llamar a la <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> método para obtener el objeto. El llamador, a continuación, debe convertir el valor devuelto para el tipo es adecuado. Cuando el objeto ya no es necesario, llame a <xref:System.Runtime.InteropServices.Marshal.Release%2A> para liberarlo.  
  
 La siguiente es un ejemplo de llamada la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> método y el control de la `IUnknown` objeto correctamente:  
  
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
>  Se conocen los siguientes métodos para pasar `IUnknown` punteros de objeto como tipo <xref:System.IntPtr>. Como se describe en esta sección, controlarlos.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
### <a name="optional-out-parameters"></a>Parámetros [out] opcional  
 Buscar los parámetros que se definen como un [out] tipo de datos (`int`, `object`, etc.) en el COM interfaz, pero que se definen como matrices del mismo tipo de datos en el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototipo de método del ensamblado de interoperabilidad.  
  
 Algunos COM las interfaces, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, tratar [out] parámetros como opcionales. Si no se requiere un objeto, estas interfaces COM devuelven un `null` puntero como el valor de ese parámetro en lugar de crear el objeto [out]. Esto es intencionado. Para estas interfaces, `null` punteros se consideran como parte del comportamiento correcto del VSPackage y se devuelve ningún error.  
  
 Dado que el CLR no admite el valor de un parámetro [out] se `null`, parte del comportamiento de estas interfaces diseñado no está disponible directamente en código administrado. El [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] métodos del ensamblado de interoperabilidad para las interfaces afectados solución el problema mediante la definición de los parámetros relevantes como matrices porque CLR permite el paso de `null` matrices.  
  
 Implementaciones administradas de estos métodos se deben colocar un `null` matriz en el parámetro cuando no hay nada que se va a devolver. En caso contrario, cree una matriz de un elemento del tipo correcto y coloque el valor devuelto de la matriz.  
  
 Administra los métodos que reciben información de las interfaces con opcional [out] el parámetro como una matriz de parámetros de recepción. Sólo tiene que examinar el valor del primer elemento de la matriz. Si no es `null`, trate el primer elemento como si fuese el parámetro original.  
  
### <a name="passing-constants-in-pointer-parameters"></a>Constantes de pasar parámetros de puntero  
 Buscar los parámetros que se definen como [in] punteros en la interfaz COM, pero que se definen como un <xref:System.IntPtr> escriba en el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototipo de método del ensamblado de interoperabilidad.  
  
 Un problema similar se produce cuando una interfaz COM pasa un valor especial, como 0, -1 o – 2, en lugar de un puntero de objeto. A diferencia de [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], CLR no admite las constantes para convertirse en objetos. En su lugar, el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ensamblado de interoperabilidad define el parámetro como un <xref:System.IntPtr> tipo.  
  
 Implementaciones administradas de estos métodos deben sacar partido del hecho de que el <xref:System.IntPtr> clase tiene ambos `int` y `void *` constructores para crear un <xref:System.IntPtr> en un objeto o una constante entera, según corresponda.  
  
 Administra los métodos que reciben <xref:System.IntPtr> parámetros de este tipo se deben usar el <xref:System.IntPtr> escribir operadores de conversión para controlar los resultados. Debe convertir primero el <xref:System.IntPtr> a `int` y prueba frente a constantes de tipo entero correspondiente. Si no hay valores coinciden, convertirlo en un objeto del tipo necesario y continuar.  
  
 Para obtener ejemplos de esto, consulte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.  
  
### <a name="ole-return-values-passed-as-out-parameters"></a>OLE devuelven los valores pasados como [parámetros out]  
 Busque los métodos que tienen un `retval` valor devuelto en la interfaz COM, pero que tienen un `int` valor devuelto y adicional [out] el parámetro de matriz en la [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototipo de método del ensamblado de interoperabilidad. Debe quedar claro que estos métodos requieren un tratamiento especial porque la [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototipos de método del ensamblado de interoperabilidad tienen un parámetro más que los métodos de interfaz COM.  
  
 Muchas interfaces COM que se encargan de actividad OLE enviar información sobre el estado OLE al programa que realiza la llamada almacena en el `retval` devolver el valor de la interfaz. En lugar de usar un valor devuelto, los correspondientes [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] métodos del ensamblado de interoperabilidad envían la información al programa que realiza la llamada almacenado en una [out] un parámetro de matriz.  
  
 Implementaciones administradas de estos métodos deben crear una matriz de solo elemento del mismo tipo que el parámetro [out] y colóquela en el parámetro. El valor del elemento de matriz debe ser el mismo que el COM adecuado `retval`.  
  
 Métodos administrados que llaman a las interfaces de este tipo deben extraer el primer elemento de la matriz [out]. Este elemento se puede tratar como si fuese un `retval` devolver valor de la interfaz COM correspondiente.  
  
## <a name="see-also"></a>Vea también  
 [Serialización de interoperabilidad](http://msdn.microsoft.com/en-us/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Serialización de interoperabilidad](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [Solucionar problemas de interoperabilidad](http://msdn.microsoft.com/library/b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37)   
 [VSPackages administrado](../misc/managed-vspackages.md)