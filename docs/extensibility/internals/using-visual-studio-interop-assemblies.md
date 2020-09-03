---
title: Usar ensamblados de interoperabilidad de Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5926b2cce217565c889c7ef2eeef877691101ed6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704132"
---
# <a name="using-visual-studio-interop-assemblies"></a>Uso de ensamblados de interoperabilidad de Visual Studio
Los ensamblados de interoperabilidad de Visual Studio permiten a las aplicaciones administradas tener acceso a las interfaces COM que proporcionan extensibilidad de Visual Studio. Hay algunas diferencias entre las interfaces COM directas y sus versiones de interoperabilidad. Por ejemplo, los HRESULTs se representan generalmente como valores int y deben administrarse de la misma manera que las excepciones, y los parámetros (especialmente los parámetros out) se tratan de forma diferente.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Control de valores HRESULT devueltos al código administrado desde COM
 Cuando se llama a una interfaz COM desde código administrado, se examina el valor HRESULT y se genera una excepción si es necesario. La clase <xref:Microsoft.VisualStudio.ErrorHandler> contiene el método <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, que produce una excepción de COM, dependiendo del valor HRESULT que se pasa.

 De forma predeterminada, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> generará una excepción siempre que se pase un valor HRESULT menor que cero. En los casos en los que los valores HRESULT sean aceptables y no se generen excepciones, los valores HRESULT adicionales deben pasarse a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> después de probarlos. Si el valor HRESULT que se está probando coincide con los valores HRESULT pasados explícitamente a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, no se generará ninguna excepción.

> [!NOTE]
> La <xref:Microsoft.VisualStudio.VSConstants> clase contiene constantes para los valores HRESULT comunes, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.S_OK> y <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> , y [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULTS, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> y <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> . <xref:Microsoft.VisualStudio.VSConstants> también proporciona los métodos <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> y <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>, que corresponden a las macros SUCCEEDED y FAILED en COM.

 Por ejemplo, considere la siguiente llamada de función, en el que <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> es un valor devuelto aceptable, pero cualquier otro valor HRESULT menor que cero representa un error.

 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]

 Si hay más de un valor devuelto aceptable, los valores HRESULT adicionales solo se pueden anexar a la lista en la llamada a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.

 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]

## <a name="returning-hresults-to-com-from-managed-code"></a>Devolución de valores HRESULT a COM desde el código administrado
 Si no se produce ninguna excepción, el código administrado devuelve <xref:Microsoft.VisualStudio.VSConstants.S_OK> a la función COM que lo llamó. La interoperabilidad COM admite excepciones comunes que están fuertemente tipadas en el código administrado. Por ejemplo, un método que recibe un argumento `null` inaceptable produce <xref:System.ArgumentNullException>.

 Si no está seguro de la excepción que se debe generar pero conoce el valor HRESULT que desea devolver a COM, puede usar el método <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> para generar la excepción adecuada. Esto funciona incluso con errores no estándar como, por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> intenta asignar el valor HRESULT pasado a una excepción fuertemente tipada. Si no es posible, genera una excepción COM genérica. El resultado final es que el valor HRESULT que se pasa a <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> desde el código administrado se devuelve a la función COM que lo llamó.

> [!NOTE]
> Las excepciones afectan al rendimiento y están destinadas para indicar condiciones del programa anormales. Las condiciones que se producen con frecuencia deben controlarse en línea, en lugar de generar una excepción.

## <a name="iunknown-parameters-passed-as-type-void"></a>Parámetros IUnknown pasados como tipo void * *
 Busque los parámetros [out] definidos como tipo `void **` en la interfaz com, pero que se definen como `[``iid_is``]` en el prototipo de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] método de ensamblado de interoperabilidad.

 A veces, una interfaz COM genera un `IUnknown` objeto y la interfaz com lo pasa como tipo `void **` . Estas interfaces son especialmente importantes porque si la variable se define como [out] en el IDL, el `IUnknown` objeto se cuenta con el `AddRef` método. Si el objeto no se controla correctamente, se produce una fuga de memoria.

> [!NOTE]
> Un `IUnknown` objeto creado por la interfaz com y devuelto en una variable [out] produce una fuga de memoria si no se libera explícitamente.

 Los métodos administrados que controlan estos objetos deben tratar <xref:System.IntPtr> como un puntero a un `IUnknown` objeto y llamar al <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> método para obtener el objeto. A continuación, el llamador debe convertir el valor devuelto a cualquier tipo que sea adecuado. Cuando el objeto ya no sea necesario, llame <xref:System.Runtime.InteropServices.Marshal.Release%2A> a para liberarlo.

 A continuación se encuentra un ejemplo de llamada al <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> método y control del `IUnknown` objeto correctamente:

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
> Se sabe que los siguientes métodos pasan `IUnknown` punteros de objeto como tipo <xref:System.IntPtr> . Controlarlas tal y como se describe en esta sección.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>Parámetros opcionales [out]
 Busque los parámetros que se definen como un tipo de datos [out] ( `int` , `object` , etc.) en la interfaz com, pero que se definen como matrices del mismo tipo de datos en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo de método de ensamblado de interoperabilidad.

 Algunas interfaces COM, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> , tratan los parámetros [out] como opcionales. Si un objeto no es necesario, estas interfaces COM devuelven un `null` puntero como el valor de ese parámetro en lugar de crear el objeto [out]. es así por diseño. Para estas interfaces, `null` se supone que los punteros forman parte del comportamiento correcto del VSPackage y no se devuelve ningún error.

 Dado que CLR no permite que el valor de un parámetro [out] sea `null` , parte del comportamiento diseñado de estas interfaces no está disponible directamente en el código administrado. Los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] métodos de ensamblado de interoperabilidad para interfaces afectadas solucionan el problema definiendo los parámetros pertinentes como matrices porque CLR permite el paso de `null` matrices.

 Las implementaciones administradas de estos métodos deben colocar una `null` matriz en el parámetro cuando no hay nada que devolver. De lo contrario, cree una matriz de un solo elemento del tipo correcto y coloque el valor devuelto en la matriz.

 Los métodos administrados que reciben información de interfaces con parámetros [out] opcionales reciben el parámetro como una matriz. Simplemente examine el valor del primer elemento de la matriz. Si no es así `null` , trate el primer elemento como si fuera el parámetro original.

## <a name="passing-constants-in-pointer-parameters"></a>Pasar constantes en parámetros de puntero
 Busque los parámetros que se definen como [in] punteros en la interfaz COM, pero que se definen como un <xref:System.IntPtr> tipo en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo de método de ensamblado de interoperabilidad.

 Un problema similar se produce cuando una interfaz COM pasa un valor especial, como 0,-1 o-2, en lugar de un puntero de objeto. A diferencia de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] , CLR no permite convertir constantes como objetos. En su lugar, el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ensamblado de interoperabilidad define el parámetro como un <xref:System.IntPtr> tipo.

 Las implementaciones administradas de estos métodos deben aprovechar el hecho de que la <xref:System.IntPtr> clase tiene `int` `void *` constructores y para crear un a <xref:System.IntPtr> partir de un objeto o una constante de tipo entero, según corresponda.

 Los métodos administrados que reciben <xref:System.IntPtr> parámetros de este tipo deben usar los <xref:System.IntPtr> operadores de conversión de tipos para controlar los resultados. En primer lugar, convierta <xref:System.IntPtr> en `int` y pruébelo con constantes de tipo entero relevantes. Si no hay valores coincidentes, conviértalo en un objeto del tipo necesario y continúe.

 Para obtener ejemplos de esto, vea <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .

## <a name="ole-return-values-passed-as-out-parameters"></a>Valores devueltos por OLE que se pasan como parámetros [out]
 Busque los métodos que tienen un `retval` valor devuelto en la interfaz com, pero que tienen un `int` valor devuelto y un parámetro de matriz adicional [out] en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo de método de ensamblado de interoperabilidad. Debe estar claro que estos métodos requieren un tratamiento especial, ya que los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipos de método de ensamblado de interoperabilidad tienen un parámetro más que los métodos de interfaz com.

 Muchas interfaces COM que se ocupan de la actividad OLE envían información sobre el estado de OLE al programa que realiza la llamada almacenado en el `retval` valor devuelto de la interfaz. En lugar de usar un valor devuelto, los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] métodos de ensamblado de interoperabilidad correspondientes envían la información al programa que realiza la llamada almacenado en un parámetro de matriz [out].

 Las implementaciones administradas de estos métodos deben crear una matriz de un solo elemento del mismo tipo que el parámetro [out] y colocarlo en el parámetro. El valor del elemento de la matriz debe ser el mismo que el COM adecuado `retval` .

 Los métodos administrados que llaman a interfaces de este tipo deben extraer el primer elemento de la matriz [out]. Este elemento se puede tratar como si fuera un `retval` valor devuelto de la interfaz com correspondiente.

## <a name="see-also"></a>Vea también
- [Interoperar con código no administrado](/dotnet/framework/interop/index)
