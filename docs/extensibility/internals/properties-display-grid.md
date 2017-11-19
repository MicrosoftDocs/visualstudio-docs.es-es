---
title: "Propiedades Mostrar cuadrícula | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 35b36c357c9b98d81627eea0d511b0b4fd49f693
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="properties-display-grid"></a>Mostrar cuadrícula de propiedades
El **propiedades** ventana muestra los campos dentro de una cuadrícula. La columna izquierda contiene los nombres de propiedad; la columna derecha contiene los valores de propiedad.  
  
## <a name="working-with-the-grid"></a>Trabajar con la cuadrícula  
 La lista de dos columnas muestra propiedades independientes de la configuración que se pueden cambiar en tiempo de diseño y su configuración actual. Tenga en cuenta que todas las propiedades podrían no mostrarse. Una propiedad puede establecerse como ocultos, por ejemplo, mediante la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> método. En concreto, para ocultar propiedades que tienen propiedades secundarias:  
  
1.  Establecer el `pfDisplay` parámetro en <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> a `FALSE`.  
  
2.  Establecer el `pfHide` parámetro en <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> a `TRUE`.  
  
 Para obtener información de inserción a la **propiedades** ventana, el IDE usa <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>llama a VSPackages para cada ventana que contiene objetos que pueden seleccionarse con propiedades relacionadas que se mostrará en el **propiedades** ventana. **El Explorador de soluciones**de implementación de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> llamadas `GetProperty` con <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> en la jerarquía del proyecto para adquirir los objetos explorable en la jerarquía.  
  
 Si no es compatible con el paquete de VS <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>, el IDE intenta usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> con el valor de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> que proporcionan el elemento de la jerarquía o elementos.  
  
 El proyecto no es necesario crear VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> porque el paquete de ventana proporcionado por el IDE que lo implementa (por ejemplo, **el Explorador de soluciones**) construye <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> en su nombre.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>consta de tres métodos llamados por el IDE:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>contiene el número de objetos seleccionados que se mostrarán en el **propiedades** ventana.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>Devuelve el `IDispatch` objetos que se van a mostrar en el **propiedades** ventana.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>permite que cualquiera de los objetos devueltos por <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> seleccionarse por el usuario. Esto permite que el VSPackage visualmente actualizar la selección que se muestra al usuario en la interfaz de usuario.  
  
 El **propiedades** ventana extrae información de la `IDispatch` objetos que se va a recuperar las propiedades que se va a examinar. Utiliza el Explorador de propiedades `IDispatch` para solicitar al objeto qué propiedades admite consultando `ITypeInfo`, que se obtiene desde `IDispatch::GetTypeInfo`. El explorador, a continuación, utiliza estos valores para rellenar el **propiedades** ventana y cambiar los valores de las propiedades individuales se muestran en la cuadrícula. La información de propiedades se mantiene en el propio objeto.  
  
 Dado que los objetos devueltos admiten `IDispatch`, el llamador puede obtener información como el nombre del objeto mediante una llamada a `IDispatch::Invoke` o `ITypeInfo::Invoke` con un identificador de predefinidos de envío (DISPID) que representa la información deseada. Los identificadores DispId declarados son negativos para asegurarse de que no entren en conflicto con identificadores definidos por el usuario.  
  
 El **propiedades** ventana muestra distintos tipos de campos dependiendo de los atributos de propiedades específicas de un objeto seleccionado. Estos campos incluyen cuadros de edición, listas desplegables y vínculos a cuadros de diálogo de editor personalizado.  
  
-   Se recuperan los valores contenidos en una lista enumerada por un <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> una consulta para `IDispatch`. Valores obtenidos de una lista enumerada pueden cambiarse en la cuadrícula de propiedades haciendo doble clic en el nombre del campo o haciendo clic en el valor y seleccione el nuevo valor de la lista desplegable. Para las propiedades que tienen predefinidos de configuración de las listas enumeradas, haga doble clic en el nombre de propiedad en la lista de propiedades recorre las opciones disponibles. Para las propiedades predefinidas con solo dos opciones, como verdadero/falso, haga doble clic en el nombre de propiedad para cambiar entre las opciones.  
  
-   Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> es `false`, que indica que se ha cambiado el valor, el valor se muestra en negrita. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A>se usa para determinar si el valor se puede restablecer el valor original. Si es así, puede cambiar a la predeterminada haciendo clic en el valor y elegir **restablecer** desde el menú que se muestra. De lo contrario, tendrá que cambiar manualmente el valor a la predeterminada. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>También le permite localizar y ocultar los nombres de propiedades que se muestran en tiempo de diseño, pero no afecta a los nombres de propiedad que se muestra en tiempo de ejecución.  
  
-   Haga clic en el botón de puntos suspensivos (...), se muestra una lista de valores de propiedad desde el que el usuario puede seleccionar (por ejemplo, un selector de colores o una lista de fuentes). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>proporciona estos valores.  
  
## <a name="see-also"></a>Vea también  
 [Extensión de propiedades](../../extensibility/internals/extending-properties.md)