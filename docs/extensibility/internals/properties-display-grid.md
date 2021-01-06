---
title: Cuadrícula de visualización de propiedades | Microsoft Docs
description: Obtenga información sobre dónde se encuentran los campos nombres de propiedad y valores de propiedad en la cuadrícula del ventana Propiedades y cómo trabajar con la cuadrícula en la extensión de propiedades.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 418501ada340614d084e9796a59a46f8612aa743
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97878032"
---
# <a name="properties-display-grid"></a>Cuadrícula de visualización de propiedades

La ventana **propiedades** muestra los campos de una cuadrícula. La columna izquierda contiene los nombres de propiedad. la columna de la derecha contiene los valores de propiedad.

## <a name="work-with-the-grid"></a>Trabajar con la cuadrícula

La lista de dos columnas muestra las propiedades independientes de la configuración que se pueden cambiar en tiempo de diseño y su configuración actual. Tenga en cuenta que es posible que no se muestren todas las propiedades. Una propiedad se puede establecer como oculta, por ejemplo, implementando el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> método. En concreto, para ocultar las propiedades que tienen propiedades secundarias:

1. Establezca el `pfDisplay` parámetro de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> en `FALSE` .

2. Establezca el `pfHide` parámetro de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> en `TRUE` .

Para enviar información a la ventana **propiedades** , el IDE usa <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> se llama mediante VSPackages para cada ventana que contiene objetos seleccionables con propiedades relacionadas que se mostrarán en la ventana **propiedades** . **Explorador de soluciones** la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> llamadas `GetProperty` mediante [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) en la jerarquía del proyecto para adquirir los objetos que se van a examinar en la jerarquía.

Si el VSPackage no admite [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>), el IDE intenta usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> con el valor de [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) que el elemento o elementos de la jerarquía suministran.

No es necesario crear el VSPackage del proyecto <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> porque el paquete de ventana proporcionado por el IDE que lo implementa (por ejemplo, **Explorador de soluciones**) se construye <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> en su nombre.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> consta de tres métodos a los que llama el IDE:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> contiene el número de objetos seleccionados que se mostrarán en la ventana **propiedades** .

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> Devuelve los `IDispatch` objetos seleccionados que se mostrarán en la ventana **propiedades** .

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> permite que el usuario seleccione cualquiera de los objetos devueltos por <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> . Esto permite que el VSPackage actualice visualmente la selección que se muestra al usuario en la interfaz de usuario.

La ventana **propiedades** extrae información de los `IDispatch` objetos para recuperar las propiedades que se van a examinar. El explorador de propiedades utiliza `IDispatch` para solicitar al objeto las propiedades que admite consultando `ITypeInfo` , que se obtiene de `IDispatch::GetTypeInfo` . Después, el explorador usa estos valores para rellenar la ventana **propiedades** y cambiar los valores de las propiedades individuales que se muestran en la cuadrícula. La información de las propiedades se mantiene dentro del propio objeto.

Dado que los objetos devueltos admiten `IDispatch` , el llamador puede obtener información como el nombre del objeto llamando a `IDispatch::Invoke` o `ITypeInfo::Invoke` con un identificador de envío (DISPID) predefinido que representa la información deseada. Los DISPID declarados son negativos para asegurarse de que no entran en conflicto con los identificadores definidos por el usuario.

La ventana **propiedades** muestra distintos tipos de campos en función de los atributos de las propiedades específicas de un objeto seleccionado. Estos campos incluyen cuadros de edición, listas desplegables y vínculos a cuadros de diálogo del editor personalizado.

- Los valores contenidos en una lista enumerada se recuperan mediante una <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> consulta en `IDispatch` . Los valores obtenidos de una lista enumerada se pueden cambiar en la cuadrícula de propiedades haciendo doble clic en el nombre del campo o haciendo clic en el valor y seleccionando el nuevo valor en la lista desplegable. En el caso de las propiedades que tienen valores predefinidos de listas enumeradas, al hacer doble clic en el nombre de la propiedad en la lista de propiedades, se recorren las opciones disponibles. En el caso de las propiedades predefinidas con solo dos opciones, como true/false, haga doble clic en el nombre de la propiedad para cambiar entre las opciones.

- Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> es `false` , lo que indica que se ha cambiado el valor, el valor se muestra en negrita. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> se utiliza para determinar si el valor se puede restablecer al valor original. Si es así, puede volver a cambiar al valor predeterminado haciendo clic con el botón secundario en el valor y eligiendo **restablecer** en el menú que se muestra. De lo contrario, tendrá que volver a cambiar el valor de forma predeterminada. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> también permite localizar y ocultar los nombres de las propiedades que se muestran durante el tiempo de diseño, pero no afecta a los nombres de propiedad que se muestran durante el tiempo de ejecución.

- Al hacer clic en el botón de puntos suspensivos (...), se muestra una lista de valores de propiedad entre los que el usuario puede seleccionar (por ejemplo, un selector de colores o una lista de fuentes). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> proporciona estos valores.

## <a name="see-also"></a>Consulte también

- [Propiedades de extensión](../../extensibility/internals/extending-properties.md)
