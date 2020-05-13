---
title: Propiedades Campos e Interfaces de la ventana ? Microsoft Docs
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
ms.openlocfilehash: 9529708c781e7fdb04c3b4c5ee143b7605857e84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706157"
---
# <a name="properties-window-fields-and-interfaces"></a>Interfaces y campos de la ventana Propiedades
El modelo de selección para determinar qué información se muestra en la ventana **Propiedades** se basa en la ventana que tiene el foco en el IDE. Cada ventana y objeto dentro de la ventana seleccionada pueden tener su objeto de contexto de selección insertado en el contexto de selección global. El entorno actualiza el contexto de selección global con valores de un marco de ventana cuando esa ventana tiene el foco. Cuando el foco cambia, también lo hace el contexto de selección.

## <a name="tracking-selection-in-the-ide"></a>Seguimiento de la selección en el IDE
 El marco o sitio de ventana, propiedad del <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>IDE, tiene un servicio llamado . Los pasos siguientes muestran cómo se implementa un cambio en una selección, causado por el usuario cambiando el foco a otra ventana abierta o seleccionando un elemento de proyecto diferente en el **Explorador**de soluciones, para cambiar el contenido que se muestra en la ventana **Propiedades.**

1. El objeto creado por el VSPackage que se <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> encuentra <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>en la ventana seleccionada llama para tener invoke .

2. El contenedor de selección, proporcionado por <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> la ventana seleccionada, crea su propio objeto. Cuando cambia la selección, <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> el VSPackage llama para notificar a los agentes de escucha en el entorno, incluida la **propiedades** ventana, del cambio. También proporciona acceso a la jerarquía y a la información de elementos relacionada con la nueva selección.

3. Al <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> llamarlo y pasarle `VSHPROPID_BrowseObject` los elementos <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> de jerarquía seleccionados en el parámetro, se rellena el objeto.

4. Un objeto derivado de la [interfaz IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) se devuelve para [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) para el elemento solicitado y el <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> entorno lo envuelve en un (consulte el paso siguiente). Si se produce un error en `IVsHierarchy::GetProperty`la llamada, el entorno realiza una segunda llamada a , pasándole el contenedor de selección [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) que el artículo de jerarquía o los artículos proporcionan.

    El proyecto VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> no crea porque la ventana proporcionada por el entorno VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> que lo implementa (por ejemplo, El **Explorador**de soluciones ) construye en su nombre.

5. El entorno invoca los <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> métodos de obtener `IDispatch` los objetos basados en la interfaz para rellenar la ventana **Propiedades.**

   Cuando se cambia un valor en el `IVsTrackSelectionEx::OnElementValueChangeEx` `IVsTrackSelectionEx::OnSelectionChangeEx` **propiedades** ventana, VSPackages implementan y para notificar el cambio al valor del elemento. A continuación, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> el <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> entorno invoca o para mantener la información mostrada en la ventana **Propiedades** sincronizada con los valores de propiedad. Para obtener más información, vea Actualización de valores de [propiedad en la ventana Propiedades](#updating-property-values-in-the-properties-window).

   Además de seleccionar un elemento de proyecto diferente en el **Explorador** de soluciones para mostrar las propiedades relacionadas con ese elemento, también puede elegir un objeto diferente dentro de un formulario o ventana de documento mediante la lista desplegable disponible en la ventana **Propiedades.** Para obtener más información, consulte Lista de [objetos](../../extensibility/internals/properties-window-object-list.md)de ventana de propiedades .

   Puede cambiar la forma en que se muestra la información en la cuadrícula de la ventana **Propiedades** de alfabética a categórica y, si está disponible, también puede abrir una página de propiedades para un objeto seleccionado haciendo clic en los botones adecuados de la ventana **Propiedades.** Para obtener más información, vea [Botones](../../extensibility/internals/properties-window-buttons.md) de ventana de propiedades y [páginas](../../extensibility/internals/property-pages.md)de propiedades .

   Por último, la parte inferior de la ventana **Propiedades** también contiene una descripción del campo seleccionado en la cuadrícula de la ventana **Propiedades.** Para obtener más información, consulte [Obtención de descripciones de campos desde la ventana Propiedades](#getting-field-descriptions-from-the-properties-window).

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a>Actualización de los valores de propiedad en la ventana Propiedades
Existen dos maneras de mantener la ventana **Propiedades** sincronizada con los cambios de valores de propiedad. La primera es llamar a la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>, que proporciona acceso a la funcionalidad básica basada en ventanas, incluidos el acceso y la creación de ventanas de documentos y herramientas proporcionadas por el entorno. Los pasos siguientes describen este proceso de sincronización.

### <a name="updating-property-values-using-ivsuishell"></a>Actualización de los valores de propiedad mediante IVsUIShell

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Para actualizar los valores de propiedad mediante la interfaz IVsUIShell

1. Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (a través del servicio <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>) cada vez que paquetes VSPackage, proyectos, o editores necesiten crear o enumerar las ventanas de documentos o herramientas.

2. Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> para mantener la ventana **Propiedades** sincronizada con los cambios de propiedad de un proyecto <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> (o cualquier otro objeto seleccionado que esté examinando la ventana **Propiedades)** sin implementar <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> ni desencadenar eventos.

3. Implemente los métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy><xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> para establecer y deshabilitar, respectivamente, la notificación de cliente de los eventos de jerarquía sin requerir que la jerarquía implemente <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.

### <a name="updating-property-values-using-iconnection"></a>Actualización de los valores de propiedad mediante IConnection
 La segunda manera de mantener la ventana **Propiedades** sincronizada con los cambios de valores de propiedad consiste en implementar `IConnection` en el objeto conectable para indicar la existencia de las interfaces de salida. Si desea localizar el nombre de propiedad, derive su objeto de <xref:System.ComponentModel.ICustomTypeDescriptor>. La implementación de <xref:System.ComponentModel.ICustomTypeDescriptor> puede modificar los descriptores de propiedad que devuelve y cambiar el nombre de una propiedad. Para localizar la descripción, cree un atributo que se derive de <xref:System.ComponentModel.DescriptionAttribute> e invalide la propiedad Description.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Consideraciones de la implementación de la interfaz IConnection

1. `IConnection` proporciona acceso a un subobjeto enumerador con la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. También proporciona acceso a todos los subobjetos del punto de conexión, cada uno de los cuales implementa la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>.

2. Cualquier objeto de búsqueda es responsable de implementar un evento <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>. La ventana **Propiedades** aconsejará sobre el evento establecido a través de `IConnection`.

3. Un punto de conexión controla cuántas conexiones (una o más) permite en su implementación de <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Un punto de conexión que permita solo una interfaz puede devolver <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> desde el método <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>.

4. Un cliente puede llamar a la interfaz `IConnection` para obtener acceso a un subobjeto enumerador con la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. A continuación, se puede llamar a la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> para enumerar los puntos de conexión de cada identificador de interfaz (IID) de salida.

5. `IConnection` también se puede llamar para obtener acceso a los subobjetos del punto de conexión con la interfaz l <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> para cada IID saliente. A <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> través de la interfaz, un cliente inicia o termina un bucle de aviso con el objeto conectable y la propia sincronización del cliente. El cliente también <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> puede llamar a la <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> interfaz para obtener un objeto enumerador con la interfaz para enumerar las conexiones que conoce.

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a>Obtención de descripciones de campo desde la ventana Propiedades
En la parte inferior de la ventana **Propiedades** , un área de descripción muestra información relacionada con el campo de la propiedad seleccionada. Esta característica está activada de forma predeterminada. Si quiere ocultar el campo de descripción, haga clic con el botón derecho en la ventana **Propiedades** y haga clic en **Descripción**. Al hacerlo, también se quita la marca de verificación junto al título **Descripción** de la ventana de menú. Puede volver a mostrar el campo siguiendo los mismos pasos para volver a activar **Descripción** .

 La información del campo descripción proviene de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Cada método, interfaz, coclase, etc. puede tener un atributo `helpstring` sin localizar en la biblioteca de tipos. La ventana **Propiedades** recupera <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>la cadena de .

### <a name="to-specify-localized-help-strings"></a>Para especificar cadenas de ayuda localizadas

1. Agregue el atributo `helpstringdll` a la instrucción de la biblioteca en la biblioteca de tipos (`typelib`).

   > [!NOTE]
   > Este paso es opcional si la biblioteca de tipos está en un archivo de biblioteca de objetos (.olb).

2. Especifique atributos `helpstringcontext` para las cadenas. También puede especificar atributos `helpstring` .

    Estos atributos son distintos de los atributos `helpfile` y `helpcontext` , que se encuentran en los temas de Ayuda del archivo .chm real.

   Para recuperar la información de descripción que se mostrará para <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> el nombre de propiedad resaltado, `lcid` la ventana **Propiedades** llama a la propiedad seleccionada, especificando el atributo deseado para la cadena de salida. Internamente, <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> busca el archivo .dll especificado en el atributo `helpstringdll` y llama a la función `DLLGetDocumentation` en dicho archivo .dll con el contexto especificado y el atributo `lcid`.

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
