---
title: Las propiedades para mostrar cuadrícula | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62430d70b86402876bc94c1051a710ea3c074c5a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960690"
---
# <a name="properties-display-grid"></a>Cuadrícula para mostrar de Propiedades
El **propiedades** ventana muestra los campos dentro de una cuadrícula. La columna izquierda contiene los nombres de propiedad; la columna derecha contiene los valores de propiedad.  
  
## <a name="working-with-the-grid"></a>Trabajar con la cuadrícula  
 La lista de dos columnas muestra las propiedades independientes de la configuración que se pueden cambiar en tiempo de diseño y su configuración actual. Tenga en cuenta que no se pueden mostrar todas las propiedades. Se puede establecer una propiedad como ocultas, por ejemplo, implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> método. En concreto, para ocultar las propiedades que tienen propiedades secundarias:  
  
1. Establecer el `pfDisplay` parámetro <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> a `FALSE`.  
  
2. Establecer el `pfHide` parámetro <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> a `TRUE`.  
  
   Para obtener información de inserción a la **propiedades** ventana, el IDE usa <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> se llama a los VSPackages para cada ventana que contiene objetos seleccionables con las propiedades relacionadas que se mostrará en el **propiedades** ventana. **El Explorador de soluciones**de implementación de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> llamadas `GetProperty` mediante <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> en la jerarquía de proyecto para adquirir los pueda examinar objetos en la jerarquía.  
  
   Si no es compatible con el paquete de VS <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>, intente utilizar el IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> con el valor de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> que proporcionen el elemento de la jerarquía o elementos.  
  
   El proyecto de VSPackage no es necesario crear <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> porque el paquete de ventana proporcionado por el IDE que lo implementa (por ejemplo, **el Explorador de soluciones**) construye <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> en su nombre.  
  
   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> consta de tres métodos que son llamados por el IDE:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> contiene el número de objetos seleccionados que se mostrará en el **propiedades** ventana.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> Devuelve el `IDispatch` objetos que se van a mostrarse en el **propiedades** ventana.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> permite que cualquiera de los objetos devueltos por <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> seleccionarse por el usuario. Esto permite que el VSPackage actualizar visualmente la selección que se muestra al usuario en la interfaz de usuario.  
  
  El **propiedades** ventana extrae información de la `IDispatch` objetos que se va a recuperar las propiedades que se va a examinar. Usa el Explorador de propiedades `IDispatch` para pedir el objeto de las propiedades que admite consultando `ITypeInfo`, que se obtiene del `IDispatch::GetTypeInfo`. El explorador, a continuación, utiliza estos valores para rellenar el **propiedades** ventana y cambiar los valores de propiedades individuales se muestran en la cuadrícula. La información de las propiedades se mantiene en el propio objeto.  
  
  Dado que los objetos devueltos admiten `IDispatch`, el llamador puede obtener información como el nombre del objeto llamando `IDispatch::Invoke` o `ITypeInfo::Invoke` con un identificador predefinido de envío (DISPID) que representa la información deseada. Envío (DISPID) declarados es negativos para asegurarse de que no entren en conflicto con los identificadores definidos por el usuario.  
  
  El **propiedades** ventana muestra distintos tipos de campos dependiendo de los atributos de las propiedades específicas de un objeto seleccionado. Estos campos incluyen cuadros de edición, listas desplegables y vínculos a cuadros de diálogo del editor personalizado.  
  
- Valores contenidos en una lista enumerada se recuperan mediante un <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> consultar a `IDispatch`. Los valores obtenidos de una lista enumerada pueden cambiarse en la cuadrícula de propiedades, haciendo doble clic en el nombre del campo o haciendo clic en el valor y seleccione el nuevo valor de la lista desplegable. Para las propiedades que han predefinido la configuración de listas enumeradas, haga doble clic en el nombre de propiedad en la lista de propiedades recorre las opciones disponibles. Las propiedades predefinidas con solo dos opciones, como verdadero/falso, haga doble clic en el nombre de propiedad para cambiar entre las opciones.  
  
- Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> es `false`, que indica que el valor ha cambiado, el valor se muestra en negrita. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> se usa para determinar si el valor se puede restablecer al valor original. Si por lo tanto, puede cambiar en el valor predeterminado haciendo clic en el valor y elegir **restablecer** desde el menú que aparece. De lo contrario, deberá cambiar manualmente el valor en el valor predeterminado. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> También le permite localizar y ocultar los nombres de propiedades que se muestran durante el tiempo de diseño, pero no afecta a los nombres de propiedad que se muestran durante el tiempo de ejecución.  
  
- Al hacer clic en el botón de puntos suspensivos (...), se muestra una lista de valores de propiedad desde la que puede seleccionar el usuario (por ejemplo, un selector de colores o una lista de fuente). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> proporciona estos valores.  
  
## <a name="see-also"></a>Vea también  
 [Extensión de propiedades](../../extensibility/internals/extending-properties.md)