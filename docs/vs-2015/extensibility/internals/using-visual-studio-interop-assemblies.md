---
title: Mediante ensamblados de interoperabilidad | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
caps.latest.revision: 34
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 80d5a3dc3bfd3c0751596c3a7ba5969e4339f0f7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987707"
---
# <a name="using-visual-studio-interop-assemblies"></a>Uso de ensamblados de interoperabilidad de Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ensamblados de interoperabilidad de Visual Studio permiten a las aplicaciones administradas tener acceso a las interfaces COM que proporcionan extensibilidad de Visual Studio. Hay algunas diferencias entre las interfaces de COM rectas y sus versiones de interoperabilidad. Por ejemplo, los valores HRESULT generalmente se representan como valores int y deben tratarse de la misma manera que las excepciones, y parámetros (especialmente los parámetros out) se tratan de manera diferente.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Control de valores HRESULT devueltos al código administrado desde COM
 Cuando se llama a una interfaz COM desde código administrado, se examina el valor HRESULT y se genera una excepción si es necesario. La clase <xref:Microsoft.VisualStudio.ErrorHandler> contiene el método <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, que produce una excepción de COM, dependiendo del valor HRESULT que se pasa.

 De forma predeterminada, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> generará una excepción siempre que se pase un valor HRESULT menor que cero. En los casos en los que los valores HRESULT sean aceptables y no se generen excepciones, los valores HRESULT adicionales deben pasarse a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> después de probarlos. Si el valor HRESULT que se está probando coincide con los valores HRESULT pasados explícitamente a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, no se generará ninguna excepción.

> [!NOTE]
>  El <xref:Microsoft.VisualStudio.VSConstants> clase contiene constantes para valores HRESULT comunes, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.S_OK> y <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, y [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] valores HRESULT, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> y <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> también proporciona los métodos <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> y <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>, que corresponden a las macros SUCCEEDED y FAILED en COM.

 Por ejemplo, considere la siguiente llamada de función, en el que <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> es un valor devuelto aceptable, pero cualquier otro valor HRESULT menor que cero representa un error.

 [!code-csharp[VSSDKHRESULTInformation#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]

 Si hay más de un valor devuelto aceptable, los valores HRESULT adicionales solo se pueden anexar a la lista en la llamada a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.

 [!code-csharp[VSSDKHRESULTInformation#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]

## <a name="returning-hresults-to-com-from-managed-code"></a>Devolución de valores HRESULT a COM desde el código administrado
 Si no se produce ninguna excepción, el código administrado devuelve <xref:Microsoft.VisualStudio.VSConstants.S_OK> a la función COM que lo llamó. La interoperabilidad COM admite excepciones comunes que están fuertemente tipadas en el código administrado. Por ejemplo, un método que recibe un argumento `null` inaceptable produce <xref:System.ArgumentNullException>.

 Si no está seguro de la excepción que se debe generar pero conoce el valor HRESULT que desea devolver a COM, puede usar el método <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> para generar la excepción adecuada. Esto funciona incluso con errores no estándar como, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> intenta asignar el valor HRESULT pasado a una excepción fuertemente tipada. Si no es posible, genera una excepción COM genérica. El resultado final es que el valor HRESULT que se pasa a <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> desde el código administrado se devuelve a la función COM que lo llamó.

> [!NOTE]
>  Las excepciones afectan al rendimiento y están destinadas para indicar condiciones del programa anormales. Las condiciones que se producen con frecuencia deben controlarse en línea, en lugar de generar una excepción.

## <a name="iunknown-parameters-passed-as-type-void"></a>Los parámetros de IUnknown pasan como tipo void **
 Buscar [los parámetros que se definen como tipo out] `void **` en COM, interfaz, pero que se definen como `[``iid_is``]` en el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prototipo de método del ensamblado de interoperabilidad.

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

## <a name="optional-out-parameters"></a>Parámetros [out] opcional
 Buscar los parámetros que se definen como un [out] tipo de datos (`int`, `object`, etc.) en el COM interfaz, pero que se definen como matrices del mismo tipo de datos en el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prototipo de método del ensamblado de interoperabilidad.

 Algunos COM las interfaces, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, tratar [out] parámetros como opcionales. Si no se requiere un objeto, estas interfaces COM devuelven un `null` puntero como el valor de ese parámetro en lugar de crear el objeto [out]. Esto es intencionado. Para estas interfaces, `null` punteros se consideran como parte del comportamiento correcto del VSPackage y se devuelve ningún error.

 Dado que el CLR no admite el valor de un parámetro [out] se `null`, parte del comportamiento de estas interfaces diseñado no está disponible directamente en código administrado. El [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] métodos del ensamblado de interoperabilidad para las interfaces afectados solución el problema mediante la definición de los parámetros relevantes como matrices porque CLR permite el paso de `null` matrices.

 Implementaciones administradas de estos métodos se deben colocar un `null` matriz en el parámetro cuando no hay nada que se va a devolver. En caso contrario, cree una matriz de un elemento del tipo correcto y coloque el valor devuelto de la matriz.

 Administra los métodos que reciben información de las interfaces con opcional [out] el parámetro como una matriz de parámetros de recepción. Sólo tiene que examinar el valor del primer elemento de la matriz. Si no es `null`, trate el primer elemento como si fuese el parámetro original.

## <a name="passing-constants-in-pointer-parameters"></a>Constantes de pasar parámetros de puntero
 Buscar los parámetros que se definen como [in] punteros en la interfaz COM, pero que se definen como un <xref:System.IntPtr> escriba en el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prototipo de método del ensamblado de interoperabilidad.

 Un problema similar se produce cuando una interfaz COM pasa un valor especial, como 0, -1 o – 2, en lugar de un puntero de objeto. A diferencia de [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], CLR no admite las constantes para convertirse en objetos. En su lugar, el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ensamblado de interoperabilidad define el parámetro como un <xref:System.IntPtr> tipo.

 Implementaciones administradas de estos métodos deben sacar partido del hecho de que el <xref:System.IntPtr> clase tiene ambos `int` y `void *` constructores para crear un <xref:System.IntPtr> en un objeto o una constante entera, según corresponda.

 Administra los métodos que reciben <xref:System.IntPtr> parámetros de este tipo se deben usar el <xref:System.IntPtr> escribir operadores de conversión para controlar los resultados. Debe convertir primero el <xref:System.IntPtr> a `int` y prueba frente a constantes de tipo entero correspondiente. Si no hay valores coinciden, convertirlo en un objeto del tipo necesario y continuar.

 Para obtener ejemplos de esto, consulte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.

## <a name="ole-return-values-passed-as-out-parameters"></a>OLE devuelven los valores pasados como [parámetros out]
 Busque los métodos que tienen un `retval` valor devuelto en la interfaz COM, pero que tienen un `int` valor devuelto y adicional [out] el parámetro de matriz en la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prototipo de método del ensamblado de interoperabilidad. Debe quedar claro que estos métodos requieren un tratamiento especial porque la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prototipos de método del ensamblado de interoperabilidad tienen un parámetro más que los métodos de interfaz COM.

 Muchas interfaces COM que se encargan de actividad OLE enviar información sobre el estado OLE al programa que realiza la llamada almacena en el `retval` devolver el valor de la interfaz. En lugar de usar un valor devuelto, los correspondientes [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] métodos del ensamblado de interoperabilidad envían la información al programa que realiza la llamada almacenado en una [out] un parámetro de matriz.

 Implementaciones administradas de estos métodos deben crear una matriz de solo elemento del mismo tipo que el parámetro [out] y colóquela en el parámetro. El valor del elemento de matriz debe ser el mismo que el COM adecuado `retval`.

 Métodos administrados que llaman a las interfaces de este tipo deben extraer el primer elemento de la matriz [out]. Este elemento se puede tratar como si fuese un `retval` devolver valor de la interfaz COM correspondiente.

## <a name="see-also"></a>Vea también
 [Interoperating with Unmanaged Code](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) (Interoperar con código no administrado)
