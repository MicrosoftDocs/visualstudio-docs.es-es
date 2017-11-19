---
title: Mediante ensamblados de interoperabilidad de Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
caps.latest.revision: "33"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 298caf0b1c65ecb3612b927859b4d7d01720fc27
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="using-visual-studio-interop-assemblies"></a>Mediante ensamblados de interoperabilidad de Visual Studio
Ensamblados de interoperabilidad de Visual Studio permiten a las aplicaciones administradas tener acceso a las interfaces COM que proporcionan extensibilidad de Visual Studio. Hay algunas diferencias entre las interfaces COM rectas y sus versiones de interoperabilidad. Por ejemplo, HRESULT generalmente se representa como valores de tipo int y debe tratarse de la misma manera que las excepciones y parámetros (especialmente los parámetros out) se tratan de manera diferente.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Control de valores HRESULT devueltos al código administrado desde COM  
 Cuando se llama a una interfaz COM desde código administrado, se examina el valor HRESULT y se genera una excepción si es necesario. El <xref:Microsoft.VisualStudio.ErrorHandler> clase contiene la <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> método, que produce una excepción de COM, dependiendo del valor de HRESULT se pasa a él.  
  
 De forma predeterminada, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> produce una excepción cuando se pasa un valor HRESULT que tiene un valor menor que cero. En casos donde HRESULT sean los valores aceptables y no se debe producir ninguna excepción, los valores HRESULT adicionales deben pasarse a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> después de que se comprueban los valores. Si el valor HRESULT que se está probando coincide con los valores HRESULT pasados explícitamente a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, se inicia ninguna excepción.  
  
> [!NOTE]
>  El <xref:Microsoft.VisualStudio.VSConstants> clase contiene constantes para valores HRESULT comunes, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.S_OK> y <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, y [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULT, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> y <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants>También proporciona la <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> y <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> métodos, que corresponden a las macros SUCCEEDED y FAILED en COM.  
  
 Por ejemplo, considere la siguiente llamada de función, en el que <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> es un valor devuelto aceptable, pero cualquier otro valor HRESULT menor que cero representa un error.  
  
 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]  
  
 Si hay de más de un aceptables valores devueltos, los valores HRESULT adicionales solo se pueden anexar a la lista en la llamada a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.  
  
 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Devolución de valores HRESULT a COM desde el código administrado  
 Si se produce ninguna excepción, el código administrado devuelve <xref:Microsoft.VisualStudio.VSConstants.S_OK> a la función COM que lo llamó. La interoperabilidad COM admite excepciones comunes que están fuertemente tipadas en el código administrado. Por ejemplo, un método que recibe un inaceptable `null` argumento produce un <xref:System.ArgumentNullException>.  
  
 Si no está seguro de qué excepción que se inicia, pero conoce el valor HRESULT que desea devolver a COM, puede usar el <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> método produzca una excepción adecuada. Esto funciona incluso con un error no estándar, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>intenta asignar el valor HRESULT pasado a una excepción fuertemente tipada. Si no es posible, genera una excepción COM genérica. El resultado final es que el valor HRESULT que se pasa a <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> desde el código administrado se devuelve a la función COM que lo llamó.  
  
> [!NOTE]
>  Las excepciones afectan al rendimiento y están destinadas para indicar condiciones del programa anormales. Las condiciones que se producen con frecuencia deben controlarse en línea, en lugar de generar una excepción.  
  
## <a name="iunknown-parameters-passed-as-type-void"></a>Parámetros de IUnknown pasan como tipo void **  
 Buscar [los parámetros que se definen como tipo out] `void **` en el modelo COM, interfaz, pero que se definen como `[``iid_is``]` en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo de método del ensamblado de interoperabilidad.  
  
 A veces, una interfaz COM genera una `IUnknown` objeto y la interfaz COM, a continuación, lo pasa como tipo `void **`. Estas interfaces son especialmente importantes porque si la variable se define como [out] en el archivo IDL, la `IUnknown` objeto es el recuento de referencias con el `AddRef` método. Si el objeto no se controla correctamente, se produce una pérdida de memoria.  
  
> [!NOTE]
>  Un `IUnknown` objeto creado por la interfaz COM y se devuelve en una variable [out] provoca una pérdida de memoria si no se libera explícitamente.  
  
 Deben tratar los métodos administrados que administran estos objetos <xref:System.IntPtr> como un puntero a un `IUnknown` objeto y llamar a la <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> método para obtener el objeto. El autor de la llamada, a continuación, debe convertir el valor devuelto para cualquier tipo que es adecuado. Cuando el objeto ya no es necesario, llame a <xref:System.Runtime.InteropServices.Marshal.Release%2A> para liberarlo.  
  
 Aquí te mostramos un ejemplo de llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> método y el control de la `IUnknown` objeto correctamente:  
  
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
>  Se conocen los siguientes métodos para pasar `IUnknown` punteros de objeto como tipo <xref:System.IntPtr>. Controlarlos como se describe en esta sección.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
## <a name="optional-out-parameters"></a>Parámetros [out] opcional  
 Buscar los parámetros que se definen como un [out] tipo de datos (`int`, `object`, y así sucesivamente) en el modelo COM, interfaz, pero que se definen como matrices del mismo tipo de datos en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo de método del ensamblado de interoperabilidad.  
  
 Interfaces de algunos COM, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, tratar [out] parámetros como opcional. Si no se requiere un objeto, las interfaces COM devuelven un `null` puntero como el valor de ese parámetro en lugar de crear el objeto [out]. Esto es intencionado. Para estas interfaces, `null` como parte del comportamiento correcto del VSPackage se asume que los punteros y se devuelve ningún error.  
  
 Dado que el CLR no permite el valor de un parámetro [out] sea `null`, parte del comportamiento de diseño de estas interfaces no está disponible directamente en código administrado. El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] métodos de ensamblado de interoperabilidad para interfaces afectados solución el problema mediante la definición de los parámetros pertinentes como matrices porque CLR permite el paso de `null` matrices.  
  
 Las implementaciones administradas de estos métodos deben colocar un `null` matriz en el parámetro cuando no hay nada que se devuelvan. En caso contrario, cree una matriz de un elemento del tipo correcto y coloca el valor devuelto en la matriz.  
  
 Administra los métodos que reciben información de las interfaces con [out] opcional de parámetros reciben el parámetro como una matriz. Sólo tiene que examinar el valor del primer elemento de la matriz. Si no lo es `null`, trate el primer elemento como si fuera el parámetro original.  
  
## <a name="passing-constants-in-pointer-parameters"></a>Constantes de paso de parámetros de puntero  
 Buscar los parámetros que se definen como [in] punteros en la interfaz COM, pero que se definen como un <xref:System.IntPtr> escriba en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo de método del ensamblado de interoperabilidad.  
  
 Un problema similar se produce cuando una interfaz COM pasa un valor especial, por ejemplo, 0, -1 y -2, en lugar de un puntero de objeto. A diferencia de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], el CLR no permiten constantes convertirse en objetos. En su lugar, el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ensamblado de interoperabilidad define el parámetro como un <xref:System.IntPtr> tipo.  
  
 Las implementaciones administradas de estos métodos deben aprovechar el hecho de que el <xref:System.IntPtr> clase tiene dos `int` y `void *` constructores para crear un <xref:System.IntPtr> desde un objeto o una constante entera, según corresponda.  
  
 Métodos que reciben administrados <xref:System.IntPtr> deben usar los parámetros de este tipo el <xref:System.IntPtr> escriba operadores de conversión para controlar los resultados. Primero hay que convertir la <xref:System.IntPtr> a `int` y prueba frente a constantes de tipo entero correspondiente. Si no hay valores coinciden, convertirlo en un objeto del tipo requerido y continuar.  
  
 Para obtener ejemplos de esto, consulte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.  
  
## <a name="ole-return-values-passed-as-out-parameters"></a>OLE devuelven valores pasados como [parámetros out]  
 Buscar métodos que tienen un `retval` valor devuelto en la interfaz COM, pero que tienen un `int` valor devuelto y un [parámetro de matriz en out] adicional la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo de método del ensamblado de interoperabilidad. Debe quedar claro que estos métodos requieren un tratamiento especial porque la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipos de método de ensamblado de interoperabilidad tienen un parámetro más que los métodos de interfaz COM.  
  
 Las interfaces COM que se encargan de actividad OLE envían información sobre el estado OLE hacia el programa de llamada que se almacenan en la `retval` valor devuelto de la interfaz. En lugar de usar un valor devuelto, los correspondientes [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] métodos de ensamblado de interoperabilidad envían la información al programa que realiza la llamada almacenado en un [out] un parámetro de matriz.  
  
 Las implementaciones administradas de estos métodos deben crear una matriz único elemento del mismo tipo que el parámetro [out] y colóquelo en el parámetro. El valor del elemento de matriz debe ser el mismo que el COM adecuado `retval`.  
  
 Los métodos administrados que llama a las interfaces de este tipo deben extraer el primer elemento de la matriz [out]. Este elemento se puede tratar como si fuera un `retval` devuelve el valor de la interfaz COM correspondiente.  
  
## <a name="see-also"></a>Vea también  
 [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)