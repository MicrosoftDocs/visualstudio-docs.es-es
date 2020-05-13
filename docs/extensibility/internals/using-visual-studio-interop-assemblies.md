---
title: Uso de ensamblados de interoperabilidad de Visual Studio ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704132"
---
# <a name="using-visual-studio-interop-assemblies"></a>Uso de ensamblados de interoperabilidad de Visual Studio
Los ensamblados de interoperabilidad de Visual Studio permiten que las aplicaciones administradas tienen acceso a las interfaces COM que proporcionan extensibilidad de Visual Studio. Hay algunas diferencias entre las interfaces COM rectas y sus versiones de interoperabilidad. Por ejemplo, los HRESULT se representan generalmente como valores int y deben controlarse de la misma manera que las excepciones, y los parámetros (especialmente los parámetros out) se tratan de forma diferente.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Control de valores HRESULT devueltos al código administrado desde COM
 Cuando se llama a una interfaz COM desde código administrado, se examina el valor HRESULT y se genera una excepción si es necesario. La clase <xref:Microsoft.VisualStudio.ErrorHandler> contiene el método <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, que produce una excepción de COM, dependiendo del valor HRESULT que se pasa.

 De forma predeterminada, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> generará una excepción siempre que se pase un valor HRESULT menor que cero. En los casos en los que los valores HRESULT sean aceptables y no se generen excepciones, los valores HRESULT adicionales deben pasarse a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> después de probarlos. Si el valor HRESULT que se está probando coincide con los valores HRESULT pasados explícitamente a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, no se generará ninguna excepción.

> [!NOTE]
> La <xref:Microsoft.VisualStudio.VSConstants> clase contiene constantes para HRESULTS <xref:Microsoft.VisualStudio.VSConstants.S_OK> <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>comunes, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> y <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>, y HRESULTS, por ejemplo, y . <xref:Microsoft.VisualStudio.VSConstants> también proporciona los métodos <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> y <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>, que corresponden a las macros SUCCEEDED y FAILED en COM.

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

## <a name="iunknown-parameters-passed-as-type-void"></a>Parámetros IUnknown pasados como Type void**
 Busque parámetros [out] que `void **` se definen como tipo en `[``iid_is``]` la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaz COM, pero que se definen como en el prototipo del método de ensamblado de interoperabilidad.

 A veces, una `IUnknown` interfaz COM genera un objeto `void **`y, a continuación, la interfaz COM lo pasa como tipo . Estas interfaces son especialmente importantes porque si la variable se define `IUnknown` como [out] en `AddRef` el IDL, el objeto se cuenta como referencia con el método. Se produce una pérdida de memoria si el objeto no se controla correctamente.

> [!NOTE]
> Un `IUnknown` objeto creado por la interfaz COM y devuelto en una variable [out] provoca una pérdida de memoria si no se libera explícitamente.

 Los métodos administrados <xref:System.IntPtr> que controlan `IUnknown` estos objetos <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> deben tratar como un puntero a un objeto y llamar al método para obtener el objeto. A continuación, el autor de la llamada debe convertir el valor devuelto al tipo que sea adecuado. Cuando el objeto ya <xref:System.Runtime.InteropServices.Marshal.Release%2A> no sea necesario, llame para liberarlo.

 A continuación se muestra <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> un ejemplo `IUnknown` de llamada al método y controlar el objeto correctamente:

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
> Se sabe que los `IUnknown` métodos siguientes <xref:System.IntPtr>pasan punteros de objeto como tipo . Manéjalos como se describe en esta sección.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>Parámetros [out] opcionales
 Busque parámetros que se definen como`int`un `object`tipo de datos [out] ( , , etc.) en la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfaz COM, pero que se definen como matrices del mismo tipo de datos en el prototipo del método de ensamblado de interoperabilidad.

 Algunas interfaces COM, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, tratan los parámetros [out] como opcionales. Si no se requiere un objeto, `null` estas interfaces COM devuelven un puntero como el valor de ese parámetro en lugar de crear el objeto [out]. es así por diseño. Para estas interfaces, `null` los punteros se asumen como parte del comportamiento correcto del VSPackage y no se devuelve ningún error.

 Dado que CLR no permite que el valor `null`de un parámetro [out] sea , parte del comportamiento diseñado de estas interfaces no está disponible directamente en el código administrado. Los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] métodos de ensamblado de interoperabilidad para las interfaces afectadas solucionan el `null` problema definiendo los parámetros relevantes como matrices porque CLR permite el paso de matrices.

 Las implementaciones administradas de `null` estos métodos deben colocar una matriz en el parámetro cuando no hay nada que devolver. De lo contrario, cree una matriz de un elemento del tipo correcto y coloque el valor devuelto en la matriz.

 Los métodos administrados que reciben información de interfaces con parámetros [out] opcionales reciben el parámetro como una matriz. Simplemente examine el valor del primer elemento de la matriz. Si no `null`es así, trate el primer elemento como si fuera el parámetro original.

## <a name="passing-constants-in-pointer-parameters"></a>Pasar constantes en parámetros de puntero
 Busque parámetros que se definen como punteros [in] en <xref:System.IntPtr> la interfaz COM, pero que se definen como un tipo en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo del método de ensamblado de interoperabilidad.

 Un problema similar se produce cuando una interfaz COM pasa un valor especial, como 0, -1 o -2, en lugar de un puntero de objeto. A [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]diferencia de , CLR no permite que las constantes se conviertan como objetos. En su [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lugar, el ensamblado <xref:System.IntPtr> de interoperabilidad define el parámetro como un tipo.

 Las implementaciones administradas de estos métodos <xref:System.IntPtr> deben `int` aprovechar `void *` el hecho <xref:System.IntPtr> de que la clase tiene ambos y constructores para crear un a partir de un objeto o una constante entera, según corresponda.

 Los métodos <xref:System.IntPtr> administrados que reciben parámetros de este tipo deben usar los <xref:System.IntPtr> operadores de conversión de tipos para controlar los resultados. Primero convierta <xref:System.IntPtr> `int` el a y pruébelo con constantes enteras relevantes. Si no coincide ningún valor, conviértalo en un objeto del tipo requerido y continúe.

 Para ver ejemplos <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>esto, vea y .

## <a name="ole-return-values-passed-as-out-parameters"></a>Valores de valor devuelto OLE pasados como parámetros [out]
 Busque métodos que `retval` tengan un valor devuelto en `int` la interfaz COM, pero que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tengan un valor devuelto y un parámetro de matriz [out] adicional en el prototipo del método de ensamblado de interoperabilidad. Debe quedar claro que estos métodos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] requieren un control especial porque los prototipos del método de ensamblado de interoperabilidad tienen un parámetro más que los métodos de interfaz COM.

 Muchas interfaces COM que tratan con la actividad OLE envían información `retval` sobre el estado OLE al programa de llamada almacenado en el valor devuelto de la interfaz. En lugar de usar un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] valor devuelto, los métodos de ensamblado de interoperabilidad correspondientes devuelven la información al programa que realiza la llamada almacenado en un parámetro de matriz [out].

 Las implementaciones administradas de estos métodos deben crear una matriz de un solo elemento del mismo tipo que el parámetro [out] y colocarla en el parámetro. El valor del elemento de matriz debe `retval`ser el mismo que el COM adecuado.

 Los métodos administrados que llaman a interfaces de este tipo deben extraer el primer elemento de la matriz [out]. Este elemento se puede tratar `retval` como si fuera un valor devuelto de la interfaz COM correspondiente.

## <a name="see-also"></a>Vea también
- [Interoperar con código no administrado](/dotnet/framework/interop/index)
