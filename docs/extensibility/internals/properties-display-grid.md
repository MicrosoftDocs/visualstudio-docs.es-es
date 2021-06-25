---
title: Propiedades Mostrar cuadrícula | Microsoft Docs
description: Obtenga información sobre dónde se encuentran los nombres de propiedad y los campos de valores de propiedad en la cuadrícula del ventana Propiedades y cómo trabajar con la cuadrícula para extender las propiedades.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ee3d7d8d6277f9cfa0352cb4961644e4860b46bb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899659"
---
# <a name="properties-display-grid"></a>Cuadrícula de visualización de propiedades

La **ventana** Propiedades muestra los campos dentro de una cuadrícula. La columna izquierda contiene los nombres de propiedad; la columna derecha contiene los valores de propiedad.

## <a name="work-with-the-grid"></a>Trabajar con la cuadrícula

La lista de dos columnas muestra las propiedades independientes de la configuración que se pueden cambiar en tiempo de diseño y su configuración actual. Tenga en cuenta que es posible que no se muestran todas las propiedades. Una propiedad se puede establecer como oculta, por ejemplo, implementando el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> método . En concreto, para ocultar las propiedades que tienen propiedades secundarias:

1. Establezca el `pfDisplay` parámetro en <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> en `FALSE` .

2. Establezca el `pfHide` parámetro en <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> en `TRUE` .

Para insertar información en la **ventana Propiedades,** el IDE usa <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> VSPackages llama a para cada ventana que contiene objetos seleccionables con propiedades relacionadas que se mostrarán en la **ventana** Propiedades. **Explorador de soluciones** implementación de llamadas <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> mediante `GetProperty` [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) en la jerarquía de proyectos para adquirir los objetos que se pueden examinar en la jerarquía.

Si el VSPackage no admite [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>), el IDE intenta usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> utilizando el valor para [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) que el elemento de jerarquía o los elementos suministran.

No es necesario crear el VSPackage del proyecto porque el paquete de ventana proporcionado por ide que lo implementa <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (por ejemplo, **Explorador de soluciones**) construye <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> en su nombre.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> consta de tres métodos a los que llama el IDE:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> contiene el número de objetos seleccionados para mostrarse en la **ventana** Propiedades.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> devuelve los `IDispatch` objetos seleccionados que se van a mostrar en la **ventana** Propiedades.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> hace posible que cualquiera de los objetos devueltos por <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> sea seleccionado por el usuario. Esto permite al VSPackage actualizar visualmente la selección que se muestra al usuario en la interfaz de usuario.

La **ventana** Propiedades extrae información de los `IDispatch` objetos para recuperar las propiedades que se examinan. El explorador Propiedades usa para preguntar al objeto qué propiedades admite consultando `IDispatch` , que se obtiene de `ITypeInfo` `IDispatch::GetTypeInfo` . A continuación, el explorador usa estos valores para rellenar la **ventana Propiedades** y cambiar los valores de las propiedades individuales que se muestran en la cuadrícula. La información de propiedades se mantiene dentro del propio objeto.

Dado que los objetos devueltos admiten , el autor de la llamada puede obtener información como el nombre del objeto llamando a o con un identificador de distribución `IDispatch` `IDispatch::Invoke` predefinido (DISPID) que representa la `ITypeInfo::Invoke` información deseada. Los DISPID declarados son negativos para asegurarse de que no entren en conflicto con los identificadores definidos por el usuario.

La **ventana** Propiedades muestra diferentes tipos de campos en función de los atributos de propiedades específicas de un objeto seleccionado. Estos campos incluyen cuadros de edición, listas desplegables y vínculos a cuadros de diálogo del editor personalizado.

- Los valores contenidos en una lista enumerada se recuperan mediante una <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> consulta a `IDispatch` . Los valores obtenidos de una lista enumerada se pueden cambiar en la cuadrícula de propiedades haciendo doble clic en el nombre del campo o haciendo clic en el valor y seleccionando el nuevo valor en la lista desplegable. En el caso de las propiedades que tienen valores predefinidos de listas enumeradas, al hacer doble clic en el nombre de la propiedad en la lista Propiedades se recorrerán las opciones disponibles. Para las propiedades predefinidas con solo dos opciones, como true/false, haga doble clic en el nombre de propiedad para cambiar entre las opciones.

- Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> es , lo que indica que se ha cambiado el `false` valor, el valor se muestra en negrita. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> se usa para determinar si el valor se puede restablecer al valor original. Si es así, puede volver al valor predeterminado haciendo clic con el botón derecho en el valor y eligiendo **Restablecer** en el menú que se muestra. De lo contrario, tendrá que volver a cambiar el valor al valor predeterminado manualmente. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> también permite localización y ocultación de los nombres de las propiedades que se muestran durante el tiempo de diseño, pero no afecta a los nombres de propiedad mostrados durante el tiempo de ejecución.

- Al hacer clic en el botón de puntos suspensivos (...) se muestra una lista de valores de propiedad entre los que el usuario puede seleccionar (por ejemplo, un selector de colores o una lista de fuentes). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> proporciona estos valores.

## <a name="see-also"></a>Consulta también

- [Extensión de propiedades](../../extensibility/internals/extending-properties.md)
