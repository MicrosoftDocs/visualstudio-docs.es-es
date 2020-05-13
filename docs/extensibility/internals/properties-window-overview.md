---
title: Descripción general de la ventana de propiedades ( Propiedades) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 445a43cec976f363873c89dfe9b8e05429aebaf2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706030"
---
# <a name="properties-window-overview"></a>Información general sobre la ventana Propiedades
La ventana **Propiedades** se utiliza para mostrar las propiedades de los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] objetos seleccionados en los dos tipos principales de ventanas disponibles en el entorno de desarrollo integrado (IDE). Estos dos tipos de ventanas son:

- Ventanas de herramientas como el Explorador de soluciones, la vista de clases y el explorador de objetos

- Ventanas de documentos que contienen editores y diseñadores como diseñador de formularios, editor XML y editor HTML

## <a name="using-the-properties-window"></a>Uso de la ventana Propiedades
 La ventana **Propiedades** muestra las propiedades de uno o varios elementos seleccionados. Si se seleccionan varios elementos, se muestra la intersección de todas las propiedades de todos los objetos seleccionados.

 Los eventos relacionados con un objeto seleccionado dentro de una ventana de diseño de formulario o un editor HTML mediante metadatos COM+ se muestran en la ventana **Propiedades.** Por ejemplo, puede seleccionar un botón y mostrar `OnClick` sus eventos asociados, como un evento, que se puede vincular a ese botón.

 Los eventos que se muestran en la ventana **Propiedades** se utilizan principalmente con objetos enlazados al código. Si está editando un formato de archivo que no tiene nada que ver con el código, no va a tener ningún evento. Los eventos solo se muestran en la ventana **Propiedades** cuando hay un enlace entre el código en ejecución y determinados eventos asociados a objetos específicos. Un ejemplo de esto sería el código detrás de un objeto seleccionado que se ejecuta cuando se activa ese objeto.

 En la tabla siguiente se enumeran las interfaces principales utilizadas por la ventana **Propiedades.**

|Nombre de la interfaz|Descripción|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Proporciona una lista de categorías a la ventana **Propiedades** y asigna cada propiedad a una categoría.|
|[Interfaz IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|Expone los métodos y propiedades de un objeto a herramientas de programación y otras aplicaciones que admiten la automatización.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Proporciona los botones de puntos suspensivos (...) *denominados generadores* que abren ventanas de cuadro de diálogo modal implementadas por el propio objeto. Se utiliza cuando el usuario no escribe fácilmente un valor en un campo de texto. Por ejemplo, se puede utilizar para abrir un selector de color que determina el valor RGB por usted.|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Proporciona acceso a los objetos utilizados para actualizar la información que se muestra en la ventana **Propiedades.** <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>VSPackages implementa para cada ventana que contiene objetos seleccionables con propiedades relacionadas que se mostrarán.|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Proporciona información sobre el tipo de un objeto, como métodos de una interfaz y campos de una estructura.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Permite VSPackages para recibir notificación de eventos de selección y para recuperar información sobre la jerarquía de proyecto actual, elemento, valor de elemento y contexto de interfaz de usuario de comandos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Proporciona el entorno con acceso a varias selecciones.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Se utiliza para proporcionar nombres localizados en algunas propiedades que se muestran en la ventana **Propiedades.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Notifica a los paquetes VSPackage registrados que se han producido cambios en la selección, el valor de elemento o el contexto de la interfaz de usuario de comandos actuales.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Notifica al entorno de un cambio en la selección actual y proporciona acceso a la información de jerarquía y de elemento relacionada con la nueva selección.|

 Para obtener `IDispatch`más información sobre , consulte la biblioteca MSDN.

## <a name="see-also"></a>Vea también
- [Extensión de propiedades](../../extensibility/internals/extending-properties.md)
- [Interfaces y campos de la ventana Propiedades](../../extensibility/internals/properties-window-fields-and-interfaces.md)
