---
title: Campos e interfaces de la ventana Propiedades | Microsoft Docs
description: Obtenga información sobre la selección que determina qué información se muestra en el ventana Propiedades en función de la ventana que tiene el foco en el IDE de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21bc3a7f1d46a1afe579a67afa09097fd04458ff
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875770"
---
# <a name="properties-window-fields-and-interfaces"></a>Interfaces y campos de la ventana Propiedades
El modelo de selección para determinar qué información se muestra en la ventana **propiedades** se basa en la ventana que tiene el foco en el IDE. Todas las ventanas y objetos de la ventana seleccionada pueden hacer que su objeto de contexto de selección se inserte en el contexto de selección global. El entorno actualiza el contexto de selección global con los valores de un marco de ventana cuando la ventana tiene el foco. Cuando el foco cambia, también lo hace el contexto de selección.

## <a name="tracking-selection-in-the-ide"></a>Seguimiento de la selección en el IDE
 El marco de ventana o el sitio, propiedad del IDE, tiene un servicio denominado <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . En los pasos siguientes se muestra cómo un cambio en una selección, causado por el usuario, ya sea cambiando el foco a otra ventana abierta o seleccionando un elemento de proyecto diferente en **Explorador de soluciones**, se implementa para cambiar el contenido que se muestra en la ventana **propiedades** .

1. El objeto creado por el VSPackage que se encuentra en la ventana seleccionada llama <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> a para que se <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> invoque <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .

2. El contenedor de selección, proporcionado por la ventana seleccionada, crea su propio <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objeto. Cuando la selección cambia, el VSPackage llama <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> a para notificar a cualquier agente de escucha en el entorno, incluida la ventana **propiedades** , del cambio. También proporciona acceso a la información de la jerarquía y los elementos relacionados con la nueva selección.

3. Al llamar a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> y pasarle los elementos de la jerarquía seleccionada en el parámetro, se `VSHPROPID_BrowseObject` rellena el <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objeto.

4. Un objeto derivado de la [interfaz IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) se devuelve para [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) para el elemento solicitado y el entorno lo ajusta en un <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (vea el paso siguiente). Si se produce un error en la llamada, el entorno realiza una segunda llamada a `IVsHierarchy::GetProperty` , pasándole el contenedor de selección [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) que el elemento o elementos de la jerarquía suministran.

    El VSPackage del proyecto no crea <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> porque el VSPackage de ventana proporcionado por el entorno que lo implementa (por ejemplo, **Explorador de soluciones**) se construye <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> en su nombre.

5. El entorno invoca los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> para obtener los objetos en función de la `IDispatch` interfaz que se va a rellenar en la ventana **propiedades** .

   Cuando se cambia un valor en la ventana **propiedades** , los VSPackages implementan `IVsTrackSelectionEx::OnElementValueChangeEx` y `IVsTrackSelectionEx::OnSelectionChangeEx` para notificar el cambio en el valor del elemento. A continuación, el entorno invoca <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> para mantener la información mostrada en la ventana **propiedades** sincronizada con los valores de propiedad. Para obtener más información, vea [actualizar valores de propiedad en la ventana Propiedades](#updating-property-values-in-the-properties-window).

   Además de seleccionar un elemento de proyecto diferente en **Explorador de soluciones** para mostrar las propiedades relacionadas con ese elemento, también puede elegir un objeto diferente en un formulario o una ventana de documento mediante la lista desplegable disponible en la ventana **propiedades** . Para obtener más información, vea [propiedades ventana Lista de objetos](../../extensibility/internals/properties-window-object-list.md).

   Puede cambiar la forma en que se muestra la información en la cuadrícula de la ventana **propiedades** de alfabético a categorías y, si está disponible, también puede abrir una página de propiedades para un objeto seleccionado haciendo clic en los botones adecuados en la ventana **propiedades** . Para obtener más información, consulte botones de la [ventana Propiedades](../../extensibility/internals/properties-window-buttons.md) y [páginas de propiedades](../../extensibility/internals/property-pages.md).

   Por último, la parte inferior de la ventana **propiedades** también contiene una descripción del campo seleccionado en la cuadrícula de la ventana **propiedades** . Para obtener más información, vea [obtener descripciones de campo en la ventana Propiedades](#getting-field-descriptions-from-the-properties-window).

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a> Actualizar valores de propiedad en la ventana Propiedades
Existen dos maneras de mantener la ventana **Propiedades** sincronizada con los cambios de valores de propiedad. La primera es llamar a la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>, que proporciona acceso a la funcionalidad básica basada en ventanas, incluidos el acceso y la creación de ventanas de documentos y herramientas proporcionadas por el entorno. Los pasos siguientes describen este proceso de sincronización.

### <a name="updating-property-values-using-ivsuishell"></a>Actualización de los valores de propiedad mediante IVsUIShell

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Para actualizar los valores de propiedad mediante la interfaz IVsUIShell

1. Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (a través del servicio <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>) cada vez que paquetes VSPackage, proyectos, o editores necesiten crear o enumerar las ventanas de documentos o herramientas.

2. Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> para mantener la ventana **propiedades** sincronizada con los cambios de propiedad de un proyecto (o cualquier otro objeto seleccionado que esté examinando la ventana **propiedades** ) sin implementar <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> ni desencadenar <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> eventos.

3. Implemente los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy><xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> para establecer y deshabilitar, respectivamente, la notificación de cliente de los eventos de jerarquía sin requerir que la jerarquía implemente <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.

### <a name="updating-property-values-using-iconnection"></a>Actualización de los valores de propiedad mediante IConnection
 La segunda manera de mantener la ventana **Propiedades** sincronizada con los cambios de valores de propiedad consiste en implementar `IConnection` en el objeto conectable para indicar la existencia de las interfaces de salida. Si desea localizar el nombre de propiedad, derive su objeto de <xref:System.ComponentModel.ICustomTypeDescriptor>. La implementación de <xref:System.ComponentModel.ICustomTypeDescriptor> puede modificar los descriptores de propiedad que devuelve y cambiar el nombre de una propiedad. Para localizar la descripción, cree un atributo que se derive de <xref:System.ComponentModel.DescriptionAttribute> e invalide la propiedad Description.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Consideraciones de la implementación de la interfaz IConnection

1. `IConnection` proporciona acceso a un subobjeto enumerador con la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. También proporciona acceso a todos los subobjetos del punto de conexión, cada uno de los cuales implementa la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>.

2. Cualquier objeto de búsqueda es responsable de implementar un evento <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>. La ventana **Propiedades** aconsejará sobre el evento establecido a través de `IConnection`.

3. Un punto de conexión controla cuántas conexiones (una o más) permite en su implementación de <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Un punto de conexión que permita solo una interfaz puede devolver <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> desde el método <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>.

4. Un cliente puede llamar a la interfaz `IConnection` para obtener acceso a un subobjeto enumerador con la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. A continuación, se puede llamar a la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> para enumerar los puntos de conexión de cada identificador de interfaz (IID) de salida.

5. `IConnection` también se puede llamar para obtener acceso a los subobjetos del punto de conexión con la interfaz l <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> para cada IID saliente. A través de la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaz, un cliente inicia o finaliza un bucle de consulta con el objeto conectable y la propia sincronización del cliente. El cliente también puede llamar a la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaz para obtener un objeto de enumerador con la <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> interfaz para enumerar las conexiones que conoce.

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a> Obtener descripciones de campos en la ventana Propiedades
En la parte inferior de la ventana **Propiedades** , un área de descripción muestra información relacionada con el campo de la propiedad seleccionada. Esta característica está activada de forma predeterminada. Si quiere ocultar el campo de descripción, haga clic con el botón derecho en la ventana **Propiedades** y haga clic en **Descripción**. Al hacerlo, también se quita la marca de verificación junto al título **Descripción** de la ventana de menú. Puede volver a mostrar el campo siguiendo los mismos pasos para volver a activar **Descripción** .

 La información del campo descripción proviene de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Cada método, interfaz, coclase, etc. puede tener un atributo `helpstring` sin localizar en la biblioteca de tipos. La ventana **propiedades** recupera la cadena de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A> .

### <a name="to-specify-localized-help-strings"></a>Para especificar cadenas de ayuda localizadas

1. Agregue el atributo `helpstringdll` a la instrucción de la biblioteca en la biblioteca de tipos (`typelib`).

   > [!NOTE]
   > Este paso es opcional si la biblioteca de tipos está en un archivo de biblioteca de objetos (.olb).

2. Especifique atributos `helpstringcontext` para las cadenas. También puede especificar atributos `helpstring` .

    Estos atributos son distintos de los atributos `helpfile` y `helpcontext` , que se encuentran en los temas de Ayuda del archivo .chm real.

   Para recuperar la información de la descripción que se va a mostrar para el nombre de la propiedad resaltada, la ventana **propiedades** llama a <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> la propiedad que está seleccionada y especifica el `lcid` atributo deseado para la cadena de salida. Internamente, <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> busca el archivo .dll especificado en el atributo `helpstringdll` y llama a la función `DLLGetDocumentation` en dicho archivo .dll con el contexto especificado y el atributo `lcid`.

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

## <a name="see-also"></a>Consulte también

- [Extensión de propiedades](../../extensibility/internals/extending-properties.md)
