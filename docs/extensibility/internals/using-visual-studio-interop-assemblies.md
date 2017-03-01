---
title: Utilizar ensamblados de interoperabilidad de Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 9762ba0404e739c167cadc3e9d3106c7f3ee14e8
ms.lasthandoff: 02/22/2017

---
# <a name="using-visual-studio-interop-assemblies"></a>Utilizar ensamblados de interoperabilidad de Visual Studio
Ensamblados de interoperabilidad de Visual Studio permiten a las aplicaciones administradas obtener acceso a las interfaces COM que proporcionan extensibilidad de Visual Studio. Existen algunas diferencias entre las interfaces de COM rectas y sus versiones de interoperabilidad. Por ejemplo, HRESULT generalmente se representa como valores int y debe tratarse de la misma manera como excepciones y parámetros (especialmente los parámetros de salida) se tratan de manera diferente.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Control de valores HRESULT devueltos al código administrado desde COM  
 Cuando se llama a una interfaz COM desde código administrado, se examina el valor HRESULT y se genera una excepción si es necesario. La <xref:Microsoft.VisualStudio.ErrorHandler>clase contiene el <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>método, que produce una excepción de COM, dependiendo del valor de HRESULT pasado a lo</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> </xref:Microsoft.VisualStudio.ErrorHandler>  
  
 De forma predeterminada, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>producirá una excepción cuando se pasa un valor HRESULT que tiene un valor menor que cero.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> En casos donde tal valores HRESULT es valores aceptables y no se debe producir ninguna excepción, se deben pasar los valores de HRESULT adicional al <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>después de que los valores se prueban.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> Si el valor de HRESULT que se está probando coincide con los valores HRESULT se pasa explícitamente a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, se inicia ninguna excepción.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>  
  
> [!NOTE]
>  La <xref:Microsoft.VisualStudio.VSConstants>clase contiene constantes para HRESULT comunes, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.S_OK>y <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, y [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULT, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>y <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>.</xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> </xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> </xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> </xref:Microsoft.VisualStudio.VSConstants.S_OK> </xref:Microsoft.VisualStudio.VSConstants> <xref:Microsoft.VisualStudio.VSConstants>También proporciona <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A>y los <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>métodos, que corresponden a las macros de éxito y error en COM.</xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> </xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A></xref:Microsoft.VisualStudio.VSConstants>  
  
 Por ejemplo, considere la siguiente llamada de función, en el que <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>es un valor devuelto aceptable, pero cualquier otro HRESULT menor que cero representa un error.</xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>  
  
 [!code-vb[VSSDKHRESULTInformation&#1;](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb) ] 
 [!code-cs [VSSDKHRESULTInformation n.º&1;](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]  
  
 Si hay de dos o más valores devueltos aceptables, sólo se pueden anexar valores HRESULT adicionales a la lista en la llamada a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>  
  
 [!code-vb[VSSDKHRESULTInformation&#2;](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb) ] 
 [!code-cs [VSSDKHRESULTInformation&2;](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Devolución de valores HRESULT a COM desde el código administrado  
 Si se produce ninguna excepción, devuelve código administrado <xref:Microsoft.VisualStudio.VSConstants.S_OK>a la función COM que llama lo</xref:Microsoft.VisualStudio.VSConstants.S_OK> La interoperabilidad COM admite excepciones comunes que están fuertemente tipadas en el código administrado. Por ejemplo, un método que recibe un inaceptable `null` argumento produce un <xref:System.ArgumentNullException>.</xref:System.ArgumentNullException>  
  
 Si no está seguro de qué excepción que se inicia, pero conoce el valor HRESULT que desea volver a COM, puede usar el <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>método produzca una excepción adecuada.</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> Funciona incluso con un error no estándar, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>.</xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>Si se intenta asignar el valor HRESULT pasa a una excepción fuertemente tipada.</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> Si no es posible, genera una excepción COM genérica. El resultado final es que el valor HRESULT pasa a <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>desde el código administrado se devuelve a la función COM que llama lo</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>  
  
> [!NOTE]
>  Las excepciones afectan al rendimiento y están destinadas para indicar condiciones del programa anormales. Las condiciones que se producen con frecuencia deben controlarse en línea, en lugar de generar una excepción.  
  
## <a name="iunknown-parameters-passed-as-type-void"></a>Parámetros de IUnknown se pasan como tipo void **  
 Buscar [los parámetros que se definen como tipo out] `void **` en COM, interfaz, pero que se definen como `[``iid_is``]` en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo de método del ensamblado de interoperabilidad.  
  
 A veces, se genera una interfaz COM una `IUnknown` objeto y la interfaz COM, a continuación, se pasa como tipo `void **`. Estas interfaces son especialmente importantes porque si la variable se define como [out] en el archivo IDL, la `IUnknown` objeto es el recuento de referencias con el `AddRef` método. Si el objeto no se administra correctamente, se produce una pérdida de memoria.  
  
> [!NOTE]
>  Un `IUnknown` objeto creado por la interfaz COM y devuelto en una variable [out] provoca una pérdida de memoria si no se libera explícitamente.  
  
 Deben tratar los métodos administrados que administran dichos objetos <xref:System.IntPtr>como un puntero a un `IUnknown` de objetos y llamar a la <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>método para obtener el objeto.</xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> </xref:System.IntPtr> El llamador debe convertir el valor devuelto para cualquier tipo que es adecuado. Cuando el objeto ya no es necesario, llame <xref:System.Runtime.InteropServices.Marshal.Release%2A>al soltarlo.</xref:System.Runtime.InteropServices.Marshal.Release%2A>  
  
 Siguiente es un ejemplo de cómo llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>(método) y el control de la `IUnknown` objeto correctamente:</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
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
>  Se conocen los siguientes métodos para pasar `IUnknown` punteros de objeto como tipo <xref:System.IntPtr>.</xref:System.IntPtr> Controlarlos como se describe en esta sección.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
## <a name="optional-out-parameters"></a>Parámetros opcionales [out]  
 Buscar los parámetros que se definen como un [out] tipo de datos (`int`, `object`, etc.) en el COM interfaz, pero que se definen como matrices del mismo tipo de datos en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo de método del ensamblado de interoperabilidad.  
  
 Algunos COM las interfaces, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, tratar [out] parámetros como opcional.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> Si no se requiere un objeto, estas interfaces COM devuelven un `null` puntero como el valor de dicho parámetro en lugar de crear el objeto [out]. Esto es intencionado. Para estas interfaces `null` punteros se consideran como parte del comportamiento correcto de VSPackage, y se devuelve ningún error.  
  
 Dado que el CLR no admite el valor de un parámetro [out] que `null`, parte del comportamiento de diseño de estas interfaces no está disponible directamente en código administrado. El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] métodos del ensamblado de interoperabilidad para interfaces afectados solución el problema mediante la definición de los parámetros relevantes como matrices porque CLR permite el paso de `null` matrices.  
  
 Las implementaciones administradas de estos métodos deben colocar un `null` matriz en el parámetro cuando no hay nada que se devuelve. De lo contrario, cree una matriz de un elemento del tipo correcto y coloca el valor devuelto en la matriz.  
  
 Administra los métodos que reciben información de interfaces opcionales [out] el parámetro como una matriz de parámetros de recepción. Sólo tiene que examinar el valor del primer elemento de la matriz. Si no es `null`, trate el primer elemento como si fuese el parámetro original.  
  
## <a name="passing-constants-in-pointer-parameters"></a>Constantes de pasar los parámetros de puntero  
 Buscar los parámetros que se definen como [in] punteros en la interfaz COM, pero que se definen como un <xref:System.IntPtr>Escriba en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo de método del ensamblado de interoperabilidad.</xref:System.IntPtr>  
  
 Un problema similar se produce cuando una interfaz COM pasa un valor especial, como 0, -1 o – 2, en lugar de un puntero de objeto. A diferencia de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], el CLR no admite constantes convertirse como objetos. En su lugar, el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ensamblado define el parámetro como un <xref:System.IntPtr>tipo.</xref:System.IntPtr>  
  
 Las implementaciones administradas de estos métodos deben sacar partido del hecho de que el <xref:System.IntPtr>clase tiene dos `int` y `void *` constructores para crear un <xref:System.IntPtr>desde un objeto o una constante entera, según corresponda.</xref:System.IntPtr> </xref:System.IntPtr>  
  
 Métodos que reciben administrados <xref:System.IntPtr>parámetros de este tipo se deben utilizar el <xref:System.IntPtr>operadores de conversión para controlar los resultados de tipo.</xref:System.IntPtr> </xref:System.IntPtr> Convertir el <xref:System.IntPtr>a `int` y probarla con constantes de tipo entero correspondiente.</xref:System.IntPtr> Si no hay valores coinciden, convertirlo en un objeto del tipo necesario y continuar.  
  
 Para obtener ejemplos de esto, vea <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>  
  
## <a name="ole-return-values-passed-as-out-parameters"></a>OLE devuelven valores pasados como [parámetros out]  
 Buscar métodos que tienen un `retval` valor devuelto en la interfaz COM, pero que tienen una `int` devolver valor y un [parámetro de matriz en out] adicional el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo de método del ensamblado de interoperabilidad. Debe quedar claro que estos métodos requieren un tratamiento especial porque la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipos de método del ensamblado de interoperabilidad tienen un parámetro más que los métodos de interfaz COM.  
  
 Muchas interfaces COM que se encargan de la actividad OLE enviar información acerca del estado OLE al programa que realiza la llamada almacenado en el `retval` devuelve el valor de la interfaz. En lugar de utilizar un valor devuelto correspondiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] métodos del ensamblado de interoperabilidad envían la información al programa que realiza la llamada almacenado en un [out] el parámetro de matriz.  
  
 Implementaciones administradas de estos métodos deben crear una matriz de solo elementos del mismo tipo que el parámetro [out] y colocarlo en el parámetro. El valor del elemento de matriz debe ser el mismo que el COM adecuado `retval`.  
  
 El primer elemento de la matriz [out] deben extraer los métodos administrados que llama a las interfaces de este tipo. Este elemento se puede tratar como si fuese un `retval` valor devuelto de la interfaz COM correspondiente.  
  
## <a name="see-also"></a>Vea también  
 [Interoperación con código no administrado](http://msdn.microsoft.com/Library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
