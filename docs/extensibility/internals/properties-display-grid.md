---
title: "Mostrar cuadr&#237;cula de propiedades | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "cuadrícula de propiedades [Visual Studio SDK],"
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Mostrar cuadr&#237;cula de propiedades
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Los campos de la ventana muestra de **Propiedades** dentro de una cuadrícula.  la columna izquierda contiene los nombres de propiedad; la columna derecha contiene los valores de propiedad.  
  
## Trabajar con la cuadrícula  
 La lista de dos columnas muestran las propiedades de la independientes que se puede cambiar en tiempo de diseño y la configuración actual.  Observe que todas las propiedades no sean mostradas.  Una propiedad puede establecerse como oculto, por ejemplo, implementando el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> .  Específicamente, ocultar las propiedades que tienen propiedades secundarias ver, [Ocultar propiedades que tienen propiedades secundarias](../../misc/hiding-properties-that-have-child-properties.md).  
  
 Para insertar la información en la ventana de **Propiedades** , usa el IDE <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> llama VSPackages para cada ventana que contiene objetos seleccionables con propiedades relacionadas que se mostrarán en la ventana de **Propiedades** .  La implementación del Explorador De Soluciones de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> llama `GetProperty` mediante <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> en la jerarquía del proyecto para adquirir los objetos browseable en la jerarquía.  
  
 Si el Paquete no admite <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>, el IDE intenta utilizar <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> con el valor de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> que el elemento o elementos de la jerarquía proporcione.  
  
 El proyecto VSPackage no necesita crear <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> porque el paquete IDE\-proporcionado de la ventana que lo implementa \(por ejemplo, **Explorador de soluciones**\) crea <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> en su nombre.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> consta de tres métodos a los que llaman el IDE:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> contiene el número de objetos seleccionados se muestre en la ventana de **Propiedades** .  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> devuelve los objetos de `IDispatch` que son seleccionado se muestran en la ventana de **Propiedades** .  
  
-   el<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> permite a los objetos cualquiera de los devueltos por <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> para ser seleccionado por el usuario.  Esto permite que el paquete VSPackage actualice la selección visualmente ante el usuario en la interfaz de usuario.  
  
 la ventana de **Propiedades** extrae la información de los objetos de `IDispatch` para recuperar las propiedades que son examinadas.  El explorador de propiedades utiliza `IDispatch` para preguntar a objeto qué propiedades admite consultando `ITypeInfo`, que se obtiene de `IDispatch::GetTypeInfo`.  El explorador utilice estos valores para rellenar la ventana de **Propiedades** y cambiar los valores para las propiedades individuales mostradas en la cuadrícula.  La información de las propiedades se mantiene dentro del propio objeto.  
  
 Dado que los objetos devueltos `IDispatch`compatible con, el llamador puede obtener información como el nombre de objeto llamando a `IDispatch::Invoke` o `ITypeInfo::Invoke` con un identificador de envío predefinido \(DISPID\) que representa la información deseada.  Identificadores dispid declarado es negativo asegurarse no entra en conflicto con los identificadores definido por el usuario.  
  
 La ventana de **Propiedades** muestra distintos tipos de campos dependiendo de los atributos de propiedades específicas del objeto seleccionado.  Estos campos incluyen cuadros de edición, listas desplegables, e incluye vínculos a cuadros de diálogo de editor personalizado.  
  
-   Los valores contenidos en una lista son recuperados por una consulta de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> a `IDispatch`.  Los valores obtenidos de una lista se pueden cambiar en la cuadrícula de propiedades haciendo doble clic en el nombre de campo, o haciendo clic en el valor y seleccionando el nuevo valor en la lista desplegable.  Para las propiedades que tienen configuraciones predefinidas de listas enumeradas, haciendo doble clic en el nombre de propiedad en los ciclos de lista de propiedades con las opciones disponibles.  Para las propiedades predefinidas con sólo dos opciones, como true o false, haga doble clic en el nombre de propiedad para cambiar las opciones.  
  
-   Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> es `false`, que indica que se ha cambiado el valor, el valor se muestra en negrita.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> se utiliza para determinar si el valor se puede restablecer el valor original.  Si es así puede implementar de nuevo el valor predeterminado haciendo clic con el botón secundario en el valor y eligiendo **Restablecer** de menú mostrado.  Si no, tiene que cambiar el valor al valor predeterminado manualmente.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> también permite busque y oculta los nombres de las propiedades mostradas en tiempo de diseño, pero no afecta a los nombres de propiedad mostrados en tiempo de ejecución.  
  
-   Haga clic en el botón de puntos suspensivos \(...\) muestra una lista de valores de propiedad de los cuales el usuario puede seleccionar \(por ejemplo un selector de colores o una lista de fuentes\).  <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> proporciona estos valores.  
  
## Vea también  
 [Extender propiedades](../../extensibility/internals/extending-properties.md)