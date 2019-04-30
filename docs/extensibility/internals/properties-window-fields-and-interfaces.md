---
title: Campos de la ventana de propiedades e Interfaces | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1bf74bb93901cbd1637efd22690b8b1ba52f6b97
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425732"
---
# <a name="properties-window-fields-and-interfaces"></a>Interfaces y campos de la ventana Propiedades
El modelo de selección determinar qué información se muestra en el **propiedades** ventana se basa en la ventana que tiene el foco en el IDE. Cada ventana y el objeto dentro de la ventana seleccionada, pueden tener su objeto de contexto de selección insertado en el contexto de selección global. El entorno actualiza el contexto de selección global con los valores de un marco de ventana cuando esa ventana tiene el foco. Cuando el foco cambia, también lo hace el contexto de selección.

## <a name="tracking-selection-in-the-ide"></a>Selección de seguimiento en el IDE
 El marco de ventana o el sitio, el IDE de la propiedad tiene un servicio denominado <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Los pasos siguientes muestran cómo un cambio en una selección, causada por el usuario cambia el foco a otra ventana abierta o seleccionar un elemento de proyecto diferente en **el Explorador de soluciones**, se implementa para cambiar el contenido mostrado en el  **Propiedades** ventana.

1. El objeto creado por el VSPackage que está situado en las llamadas de la ventana seleccionada <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> tener <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> invocar <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.

2. El contenedor de selección, proporcionado por la ventana seleccionada, se crea su propio <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objeto. Cuando la selección cambia, el VSPackage llama <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> para notificar a los agentes de escucha en el entorno, incluida la **propiedades** ventana del cambio. También proporciona acceso a la jerarquía y elemento de información relacionada con la nueva selección.

3. Una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> y pasándole los elementos de la jerarquía seleccionada en el `VSHPROPID_BrowseObject` parámetro rellena el <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objeto.

4. Un objeto derivado de la [interfaz IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) se devuelve para [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) para el elemento solicitado y el entorno lo encapsula en un <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (consulte el paso siguiente). Si se produce un error en la llamada, el entorno hace que una segunda llamada a `IVsHierarchy::GetProperty`, pasándole el contenedor de selección [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) que proporcionen el elemento de la jerarquía o elementos.

    El proyecto de VSPackage no crea <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> porque la ventana proporcionada por el entorno de VSPackage que implemente (por ejemplo, **el Explorador de soluciones**) construye <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> en su nombre.

5. El entorno invoca los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> para obtener los objetos según el `IDispatch` interfaz para rellenar el **propiedades** ventana.

   Cuando un valor de la **propiedades** ventana se cambia, los paquetes VSPackage implementar `IVsTrackSelectionEx::OnElementValueChangeEx` y `IVsTrackSelectionEx::OnSelectionChangeEx` para notificar el cambio en el valor del elemento. A continuación, invoca el entorno <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> para mantener la información mostrada en el **propiedades** ventana sincronizada con los valores de propiedad. Para obtener más información, consulte [actualizar valores de propiedad en la ventana propiedades](#updating-property-values-in-the-properties-window).

   Además de seleccionar otro elemento de proyecto en **el Explorador de soluciones** para mostrar las propiedades relacionadas con ese elemento, también puede elegir un objeto diferente desde dentro de una ventana de documento o de formulario mediante la lista desplegable disponible en el **Propiedades** ventana. Para obtener más información, consulte [lista de objetos de ventana de propiedades](../../extensibility/internals/properties-window-object-list.md).

   Puede cambiar la manera en que se muestra información en el **propiedades** cuadrícula de la ventana de alfabético en categorías, y, si está disponible, también puede abrir una página de propiedades de un objeto seleccionado, haga clic en los botones apropiados en el  **Propiedades** ventana. Para obtener más información, consulte [botones de la ventana propiedades](../../extensibility/internals/properties-window-buttons.md) y [páginas de propiedades](../../extensibility/internals/property-pages.md).

   Por último, la parte inferior de la **propiedades** ventana también contiene una descripción del campo seleccionado en el **propiedades** cuadrícula de la ventana. Para obtener más información, consulte [obtener descripciones de los campos desde la ventana propiedades](#getting-field-descriptions-from-the-properties-window).

## <a name="updating-property-values-in-the-properties-window"></a> Actualizar valores de propiedad en la ventana Propiedades
Existen dos maneras de mantener la ventana **Propiedades** sincronizada con los cambios de valores de propiedad. La primera es llamar a la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>, que proporciona acceso a la funcionalidad básica basada en ventanas, incluidos el acceso y la creación de ventanas de documentos y herramientas proporcionadas por el entorno. Los pasos siguientes describen este proceso de sincronización.

### <a name="updating-property-values-using-ivsuishell"></a>Actualización de los valores de propiedad mediante IVsUIShell

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Para actualizar los valores de propiedad mediante la interfaz IVsUIShell

1. Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (a través del servicio <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>) cada vez que paquetes VSPackage, proyectos, o editores necesiten crear o enumerar las ventanas de documentos o herramientas.

2. Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> para mantener la **propiedades** ventana sincronizado con los cambios de propiedad para un proyecto (o cualquier otro objeto seleccionado que examina el **propiedades** ventana) sin necesidad de implementar <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> y desencadenando <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> eventos.

3. Implemente los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> para establecer y deshabilitar, respectivamente, la notificación de cliente de los eventos de jerarquía sin requerir que la jerarquía implemente <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.

### <a name="updating-property-values-using-iconnection"></a>Actualización de los valores de propiedad mediante IConnection
 La segunda manera de mantener la ventana **Propiedades** sincronizada con los cambios de valores de propiedad consiste en implementar `IConnection` en el objeto conectable para indicar la existencia de las interfaces de salida. Si desea localizar el nombre de propiedad, derive su objeto de <xref:System.ComponentModel.ICustomTypeDescriptor>. La implementación de <xref:System.ComponentModel.ICustomTypeDescriptor> puede modificar los descriptores de propiedad que devuelve y cambiar el nombre de una propiedad. Para localizar la descripción, cree un atributo que se derive de <xref:System.ComponentModel.DescriptionAttribute> e invalide la propiedad Description.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Consideraciones de la implementación de la interfaz IConnection

1. `IConnection` proporciona acceso a un subobjeto enumerador con la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. También proporciona acceso a todos los subobjetos del punto de conexión, cada uno de los cuales implementa la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>.

2. Cualquier objeto de búsqueda es responsable de implementar un evento <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>. La ventana **Propiedades** aconsejará sobre el evento establecido a través de `IConnection`.

3. Un punto de conexión controla cuántas conexiones (una o más) permite en su implementación de <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Un punto de conexión que permita solo una interfaz puede devolver <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> desde el método <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>.

4. Un cliente puede llamar a la interfaz `IConnection` para obtener acceso a un subobjeto enumerador con la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. A continuación, se puede llamar a la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> para enumerar los puntos de conexión de cada identificador de interfaz (IID) de salida.

5. `IConnection` también se puede llamar para obtener acceso a los subobjetos del punto de conexión con la interfaz l <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> para cada IID saliente. A través de la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>, un cliente inicia o termina un bucle de asesoría con el objeto conectable y la sincronización del cliente. El cliente también puede llamar a la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> para obtener un objeto enumerador con la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> para enumerar las conexiones que conoce.

## <a name="getting-field-descriptions-from-the-properties-window"></a> Obtener descripciones de los campos de la ventana de propiedades
En la parte inferior de la ventana **Propiedades** , un área de descripción muestra información relacionada con el campo de la propiedad seleccionada. Esta característica está activada de forma predeterminada. Si quiere ocultar el campo de descripción, haga clic con el botón derecho en la ventana **Propiedades** y haga clic en **Descripción**. Al hacerlo, también se quita la marca de verificación junto al título **Descripción** de la ventana de menú. Puede volver a mostrar el campo siguiendo los mismos pasos para volver a activar **Descripción** .

 La información del campo descripción proviene de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Cada método, interfaz, coclase, etc. puede tener un atributo `helpstring` sin localizar en la biblioteca de tipos. El **propiedades** ventana recupera la cadena de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.

### <a name="to-specify-localized-help-strings"></a>Para especificar cadenas de ayuda localizadas

1. Agregue el atributo `helpstringdll` a la instrucción de la biblioteca en la biblioteca de tipos (`typelib`).

   > [!NOTE]
   > Este paso es opcional si la biblioteca de tipos está en un archivo de biblioteca de objetos (.olb).

2. Especifique atributos `helpstringcontext` para las cadenas. También puede especificar atributos `helpstring` .

    Estos atributos son distintos de los atributos `helpfile` y `helpcontext` , que se encuentran en los temas de Ayuda del archivo .chm real.

   Para recuperar la información de descripción que se mostrará para el nombre de la propiedad resaltada, la **propiedades** ventana llamadas <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> para la propiedad que está seleccionada, especificando el deseado `lcid` atributo para el cadena de salida. Internamente, <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> busca el archivo .dll especificado en el atributo `helpstringdll` y llama a la función `DLLGetDocumentation` en dicho archivo .dll con el contexto especificado y el atributo `lcid`.

   La signatura y la implementación de `DLLGetDocumentation` son:

```cpp
STDAPI DLLGetDocumentation
(
   ITypeLib * /* ptlib */,
   ITypeInfo * /* ptinfo */,
   LCID /* lcid */,
   DWORD dwCtx,
   BSTR * pbstrHelpString
);
```

 La función `DLLGetDocumentation` debe ser una exportación definida en el archivo .def para la DLL.

 Internamente, se crea un archivo .olb, que en realidad es una DLL. Esta DLL contiene un recurso, el archivo de biblioteca de tipos (.tlb) y una función exportada, `DLLGetDocumentation`.

 En el caso de los archivos .olb, el atributo `helpstringdll` es opcional porque es el mismo archivo que contiene el propio archivo .tlb.

 Para obtener cadenas que aparezcan en el panel **Descripciones** , por tanto, lo mínimo que debe hacer es especificar el atributo `helpstring` en la biblioteca de tipos. Si quiere que estas cadenas se localicen, debe especificar el atributo `helpstringdll` (opcional) y el atributo `helpstringcontext` (obligatorio) e implementar `DLLGetDocumentation`.

 No hay interfaces adicionales que deban implementarse al obtener información localizada a través del atributo `helpstringcontext` y la función `DLLGetDocumentation`del archivo .idl.

 Otra manera de obtener el nombre y la descripción localizados de una propiedad es implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Para obtener más información sobre la implementación de este método, consulte [Properties Window Fields and Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md).

## <a name="see-also"></a>Vea también

- [Extensión de propiedades](../../extensibility/internals/extending-properties.md)