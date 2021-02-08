---
title: Información general sobre la ventana Propiedades | Microsoft Docs
description: Obtenga información sobre las interfaces que se usan para interactuar con el ventana Propiedades en el IDE de Visual Studio en esta información general.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a33d393cfd904bdae890f4ead9a4c25a6451460
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837299"
---
# <a name="properties-window-overview"></a>Información general sobre la ventana Propiedades
La ventana **propiedades** se utiliza para mostrar las propiedades de los objetos seleccionados en los dos tipos principales de ventanas disponibles en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE). Estos dos tipos de ventanas son:

- Ventanas de herramientas, como Explorador de soluciones, Vista de clases y examinador de objetos

- Ventanas de documento que contienen editores y diseñadores como el diseñador de formularios, el editor XML y el editor HTML

## <a name="using-the-properties-window"></a>Usar la ventana Propiedades
 La ventana **propiedades** muestra las propiedades de uno o varios elementos seleccionados. Si se seleccionan varios elementos, se muestra la intersección de todas las propiedades de todos los objetos seleccionados.

 Los eventos relacionados con un objeto seleccionado en una ventana de diseño de formulario o en el editor HTML mediante metadatos de COM+ se muestran en la ventana **propiedades** . Por ejemplo, puede seleccionar un botón y mostrar sus eventos asociados, como un `OnClick` evento, que se puede vincular a ese botón.

 Los eventos mostrados en la ventana **propiedades** se usan principalmente con objetos enlazados al código. Si está editando un formato de archivo que no tiene nada que hacer con el código, no va a tener ningún evento. Los eventos solo se muestran en la ventana **propiedades** cuando hay un enlace entre el código en ejecución y ciertos eventos asociados a objetos específicos. Un ejemplo de esto sería código detrás de un objeto seleccionado que se ejecuta cuando se activa ese objeto.

 En la tabla siguiente se enumeran las interfaces principales utilizadas por la ventana **propiedades** .

|Nombre de la interfaz|Descripción|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Proporciona una lista de categorías a la ventana **propiedades** y asigna cada propiedad a una categoría.|
|[Interfaz IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|Expone los métodos y propiedades de un objeto a las herramientas de programación y otras aplicaciones que admiten la automatización.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Proporciona botones de puntos suspensivos (...) denominados *generadores* que abren ventanas de cuadro de diálogo modales implementadas por el propio objeto. Se usa cuando el usuario no tiene fácil de escribir un valor en un campo de texto. Por ejemplo, podría usarse para abrir un selector de colores que determine el valor RGB.|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Proporciona acceso a los objetos usados para actualizar la información que se muestra en la ventana **propiedades** . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> se implementa mediante VSPackages para cada ventana que contiene objetos seleccionables con propiedades relacionadas que se van a mostrar.|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Proporciona información sobre el tipo de un objeto, como los métodos de una interfaz y los campos de una estructura.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Permite a los VSPackages recibir la notificación de eventos de selección y recuperar información sobre la jerarquía del proyecto actual, el elemento, el valor del elemento y el contexto de la interfaz de usuario de comandos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Proporciona el entorno con acceso a varias selecciones.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Se usa para proporcionar nombres localizados en algunas propiedades que se muestran en la ventana **propiedades** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Notifica a los paquetes VSPackage registrados que se han producido cambios en la selección, el valor de elemento o el contexto de la interfaz de usuario de comandos actuales.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Notifica al entorno de un cambio en la selección actual y proporciona acceso a la información de jerarquía y de elemento relacionada con la nueva selección.|

 Para obtener más información sobre `IDispatch` , vea MSDN Library.

## <a name="see-also"></a>Vea también
- [Extensión de propiedades](../../extensibility/internals/extending-properties.md)
- [Interfaces y campos de la ventana Propiedades](../../extensibility/internals/properties-window-fields-and-interfaces.md)
