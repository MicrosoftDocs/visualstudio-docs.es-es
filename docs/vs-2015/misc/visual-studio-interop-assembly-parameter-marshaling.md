---
title: Serialización de parámetros de ensamblado de interoperabilidad de Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting Visual Studio SDK interop assemblies
- interop assemblies, parameter marshaling
- interop assemblies, troubleshooting
ms.assetid: 89123eae-0fef-46d5-bd36-3d2a166b14e3
caps.latest.revision: 24
manager: jillfra
ms.openlocfilehash: ac95c40b356c542da323a3ea3744827087f2d840
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686923"
---
# <a name="visual-studio-interop-assembly-parameter-marshaling"></a>Serialización de parámetros de ensamblado de interoperabilidad de Visual Studio
Los paquetes VSPackage que se escriben en código administrado podrían tener que llamar a o ser llamados por código COM no administrado. Normalmente, el serializador de interoperabilidad transforma o calcula automáticamente los argumentos de método. Sin embargo, a veces los argumentos no se pueden transformar de manera sencilla. En esos casos, se usan los parámetros de prototipo de método de ensamblado de interoperabilidad para que coincidan lo más posible con los parámetros de la función COM. Para obtener más información, consulte [serialización de interoperabilidad](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).  
  
## <a name="general-suggestions"></a>Sugerencias generales  
  
##### <a name="read-the-reference-documentation"></a>Lea la documentación de referencia  
 Una manera eficaz de detectar problemas de interoperabilidad es leer la documentación de referencia de cada método.  
  
 La documentación de referencia de cada método contiene tres secciones relevantes:  
  
- Prototipo de la [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] función com.  
  
- Prototipo de método de ensamblado de interoperabilidad.  
  
- Una lista de los parámetros COM y una breve descripción de cada uno.  
  
##### <a name="look-for-differences-between-the-two-prototypes"></a>Buscar diferencias entre los dos prototipos  
 La mayoría de los problemas de interoperabilidad derivan de las discrepancias entre la definición de un tipo determinado en una interfaz COM y la definición del mismo tipo en los [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ensamblados de interoperabilidad. Por ejemplo, considere la diferencia en la capacidad de pasar un `null` valor en un parámetro [out]. Debe buscar diferencias entre los dos prototipos y tener en cuenta sus ramificaciones para los datos que se pasan.  
  
##### <a name="read-the-parameter-definitions"></a>Leer las definiciones de parámetros  
 Lea las definiciones de parámetros. COM es menos estricto que el Common Language Runtime (CLR) sobre la combinación de distintos tipos de datos en un único parámetro. Las [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfaces com sacan el máximo partido de esta flexibilidad. Cualquier parámetro que pueda pasar o requerir un valor o un tipo de datos no estándar, como un valor constante en un parámetro de puntero, debe describirse como tal en la documentación de.  
  
### <a name="iunknown-objects-passed-as-type-void"></a>Objetos IUnknown pasados como tipo void * *  
 Busque los parámetros [out] definidos como tipo `void **` en la interfaz com, pero que se definen como `[``iid_is``]` en el prototipo de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] método de ensamblado de interoperabilidad.  
  
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
  
### <a name="optional-out-parameters"></a>Parámetros opcionales [out]  
 Busque los parámetros que se definen como un tipo de datos [out] ( `int` , `object` , etc.) en la interfaz com, pero que se definen como matrices del mismo tipo de datos en el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototipo de método de ensamblado de interoperabilidad.  
  
 Algunas interfaces COM, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> , tratan los parámetros [out] como opcionales. Si un objeto no es necesario, estas interfaces COM devuelven un `null` puntero como el valor de ese parámetro en lugar de crear el objeto [out]. es así por diseño. Para estas interfaces, `null` se supone que los punteros forman parte del comportamiento correcto del VSPackage y no se devuelve ningún error.  
  
 Dado que CLR no permite que el valor de un parámetro [out] sea `null` , parte del comportamiento diseñado de estas interfaces no está disponible directamente en el código administrado. Los [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] métodos de ensamblado de interoperabilidad para interfaces afectadas solucionan el problema definiendo los parámetros pertinentes como matrices porque CLR permite el paso de `null` matrices.  
  
 Las implementaciones administradas de estos métodos deben colocar una `null` matriz en el parámetro cuando no hay nada que devolver. De lo contrario, cree una matriz de un solo elemento del tipo correcto y coloque el valor devuelto en la matriz.  
  
 Los métodos administrados que reciben información de interfaces con parámetros [out] opcionales reciben el parámetro como una matriz. Simplemente examine el valor del primer elemento de la matriz. Si no es así `null` , trate el primer elemento como si fuera el parámetro original.  
  
### <a name="passing-constants-in-pointer-parameters"></a>Pasar constantes en parámetros de puntero  
 Busque los parámetros que se definen como [in] punteros en la interfaz COM, pero que se definen como un <xref:System.IntPtr> tipo en el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototipo de método de ensamblado de interoperabilidad.  
  
 Un problema similar se produce cuando una interfaz COM pasa un valor especial, como 0,-1 o – 2, en lugar de un puntero de objeto. A diferencia de [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , CLR no permite convertir constantes como objetos. En su lugar, el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ensamblado de interoperabilidad define el parámetro como un <xref:System.IntPtr> tipo.  
  
 Las implementaciones administradas de estos métodos deben aprovechar el hecho de que la <xref:System.IntPtr> clase tiene `int` `void *` constructores y para crear un a <xref:System.IntPtr> partir de un objeto o una constante de tipo entero, según corresponda.  
  
 Los métodos administrados que reciben <xref:System.IntPtr> parámetros de este tipo deben usar los <xref:System.IntPtr> operadores de conversión de tipos para controlar los resultados. En primer lugar, convierta <xref:System.IntPtr> en `int` y pruébelo con constantes de tipo entero relevantes. Si no hay valores coincidentes, conviértalo en un objeto del tipo necesario y continúe.  
  
 Para obtener ejemplos de esto, vea <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .  
  
### <a name="ole-return-values-passed-as-out-parameters"></a>Valores devueltos por OLE que se pasan como parámetros [out]  
 Busque los métodos que tienen un `retval` valor devuelto en la interfaz com, pero que tienen un `int` valor devuelto y un parámetro de matriz adicional [out] en el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototipo de método de ensamblado de interoperabilidad. Debe estar claro que estos métodos requieren un tratamiento especial, ya que los [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototipos de método de ensamblado de interoperabilidad tienen un parámetro más que los métodos de interfaz com.  
  
 Muchas interfaces COM que se ocupan de la actividad OLE envían información sobre el estado de OLE al programa que realiza la llamada almacenado en el `retval` valor devuelto de la interfaz. En lugar de usar un valor devuelto, los [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] métodos de ensamblado de interoperabilidad correspondientes envían la información al programa que realiza la llamada almacenado en un parámetro de matriz [out].  
  
 Las implementaciones administradas de estos métodos deben crear una matriz de un solo elemento del mismo tipo que el parámetro [out] y colocarlo en el parámetro. El valor del elemento de la matriz debe ser el mismo que el COM adecuado `retval` .  
  
 Los métodos administrados que llaman a interfaces de este tipo deben extraer el primer elemento de la matriz [out]. Este elemento se puede tratar como si fuera un `retval` valor devuelto de la interfaz com correspondiente.  
  
## <a name="see-also"></a>Consulte también  
 [Serialización de interoperabilidad](https://msdn.microsoft.com/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Serialización de interoperabilidad](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [Solución de problemas de interoperabilidad](https://msdn.microsoft.com/library/b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37)   
 [VSPackages administrado](../misc/managed-vspackages.md)