---
title: Cuadrícula de visualización de propiedades ( Properties Display Grid) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d094c32ba8a64fc636f3fb6dfb2944dc3955628a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706189"
---
# <a name="properties-display-grid"></a>Cuadrícula de visualización de propiedades

La ventana **Propiedades** muestra campos dentro de una cuadrícula. La columna izquierda contiene los nombres de propiedad; la columna derecha contiene los valores de propiedad.

## <a name="work-with-the-grid"></a>Trabajar con la cuadrícula

La lista de dos columnas muestra las propiedades independientes de la configuración que se pueden cambiar en tiempo de diseño y su configuración actual. Tenga en cuenta que es posible que no se muestren todas las propiedades. Una propiedad se puede establecer como oculta, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> por ejemplo, mediante la implementación del método. En concreto, para ocultar propiedades que tienen propiedades secundarias:

1. Establezca `pfDisplay` el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> parámetro `FALSE`en .

2. Establezca `pfHide` el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> parámetro `TRUE`en .

Para insertar información en la ventana <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> **Propiedades,** el IDE usa . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>VSPackages llama para cada ventana que contiene objetos seleccionables con propiedades relacionadas que se mostrarán en el **propiedades** ventana. **Implementación**del Explorador <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> `GetProperty` de soluciones de llamadas mediante [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) en la jerarquía del proyecto para adquirir los objetos que se pueden examinar en la jerarquía.

Si el VSPackage no admite [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>), el IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> intenta usar el valor de [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) que el artículo de jerarquía o los artículos proporcionan.

El proyecto VSPackage no <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> necesita crear porque el paquete de ventana proporcionado por IDE <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> que lo implementa (por ejemplo, El **Explorador**de soluciones ) se construye en su nombre.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>consta de tres métodos a los que llama el IDE:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>contiene el número de objetos seleccionados para mostrarse en la ventana **Propiedades.**

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>devuelve `IDispatch` los objetos seleccionados para mostrarse en la ventana **Propiedades.**

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>hace posible que cualquiera de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> los objetos devueltos por sea seleccionado por el usuario. Esto permite que el VSPackage para actualizar visualmente la selección que se muestra al usuario en la interfaz de usuario.

La ventana **Propiedades** extrae `IDispatch` información de los objetos para recuperar las propiedades que se están examinando. El explorador `IDispatch` de propiedades utiliza para preguntar al `ITypeInfo`objeto qué propiedades `IDispatch::GetTypeInfo`admite mediante la consulta, que se obtiene de . A continuación, el explorador utiliza estos valores para rellenar la ventana **Propiedades** y cambiar los valores de las propiedades individuales que se muestran en la cuadrícula. La información de propiedades se mantiene dentro del propio objeto.

Dado que los `IDispatch`objetos devueltos admiten , el llamador `IDispatch::Invoke` `ITypeInfo::Invoke` puede obtener información como el nombre del objeto llamando a o con un identificador de envío predefinido (DISPID) que representa la información deseada. Los DISPID declarados son negativos para asegurarse de que no entren en conflicto con los identificadores definidos por el usuario.

La ventana **Propiedades** muestra diferentes tipos de campos en función de los atributos de propiedades específicas de un objeto seleccionado. Estos campos incluyen cuadros de edición, listas desplegables y vínculos a cuadros de diálogo de editor personalizados.

- Los valores contenidos en una lista <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> enumerada `IDispatch`se recuperan mediante una consulta en . Los valores obtenidos de una lista enumerada se pueden cambiar en la cuadrícula de propiedades haciendo doble clic en el nombre del campo o haciendo clic en el valor y seleccionando el nuevo valor de la lista desplegable. Para las propiedades que tienen la configuración predefinida de las listas enumeradas, haga doble clic en el nombre de la propiedad en la lista Propiedades recorre las opciones disponibles. Para las propiedades predefinidas con solo dos opciones, como true/false, haga doble clic en el nombre de propiedad para cambiar entre las opciones.

- Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> `false`es , lo que indica que se ha cambiado el valor, el valor se muestra en negrita. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A>se utiliza para determinar si el valor se puede restablecer al valor original. Si es así, puede volver al valor predeterminado haciendo clic con el botón derecho en el valor y seleccionando **Restablecer** en el menú que se muestra. De lo contrario, debe volver a cambiar el valor al valor predeterminado manualmente. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>También permite localizar y ocultar los nombres de las propiedades que se muestran durante el tiempo de diseño, pero no afecta a los nombres de propiedad que se muestran durante el tiempo de ejecución.

- Al hacer clic en el botón de puntos suspensivos (...) se muestra una lista de valores de propiedad que el usuario puede seleccionar (por ejemplo, un selector de color o una lista de fuentes). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>proporciona estos valores.

## <a name="see-also"></a>Vea también

- [Extender propiedades](../../extensibility/internals/extending-properties.md)
