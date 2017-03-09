---
title: "Establecer colores, degradados y opacidad | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Diseño de elemento de interfaz de usuario [SDK de Visual Studio]"
ms.assetid: 1734bdc7-5e16-46c7-8507-eef5cea75cb9
caps.latest.revision: 31
caps.handback.revision: 31
manager: "douge"
---
# Establecer colores, degradados y opacidad
Todos los elementos de la interfaz de usuario \(UI\) en Visual Studio se crean en Windows Presentation Foundation \(WPF\). Por lo tanto, al crear ventanas de herramientas u otros elementos de interfaz de usuario, puede aplicar colores, degradados y opacidad estableciendo los atributos adecuados en esos elementos. Puede establecer estos valores específicos mediante la ventana **Propiedades**, o bien puede consultar los valores del sistema en el entorno de desarrollo integrado \(IDE\). Se recomienda usar los valores del sistema en caso de querer que las extensiones sean similares al resto del IDE.  
  
 La interfaz de usuario de Windows Forms y la interfaz de usuario de código nativo siguen siendo compatibles con versiones anteriores. Para obtener información sobre cómo establecer colores y degradados en extensiones que no son de WPF, vea la documentación de [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].  
  
## Establecer colores, degradados y opacidad  
 Puede cambiar la apariencia de la mayoría de los elementos XAML mediante la configuración de `Background`, `Foreground`, `Opacity` u otros atributos visuales. Estos atributos corresponden a las propiedades que toman <xref:System.Windows.Media.Brush?displayProperty=fullName> como un valor.  
  
#### Para establecer la opacidad, los degradados y los colores de fondo en una ventana de herramientas  
  
1.  Abra MyControl.xaml.  
  
2.  En el panel **XAML**, en el elemento <xref:System.Windows.Controls.UserControl> de nivel superior, escriba `background=`.  
  
     IntelliSense muestra una lista de colores para el atributo BackGround.  
  
     Seleccione un color de la lista.  
  
3.  En la ventana **Propiedades**, expanda el nodo **Pinceles** y, después, haga clic en **Fondo**.  
  
     La ventana **Propiedades** muestra un selector de colores. Sobre el selector de colores existe una fila de iconos que representan los pinceles.  
  
4.  Use los controles deslizantes para elegir un color.  
  
     El XAML se actualiza inmediatamente para mostrar el nuevo color de fondo.  
  
5.  Haga clic en el icono de pincel de degradado.  
  
     El selector de color cambia a un selector de degradado.  
  
6.  Use los controles deslizantes para elegir un degradado.  
  
     El XAML se actualiza inmediatamente para mostrar el nuevo degradado de fondo.  
  
7.  Haga clic en el icono de pincel de imagen.  
  
     El selector de degradado cambia a una herramienta de selección de imagen.  
  
8.  Seleccione una imagen y establezca sus parámetros de ajuste e icono.  
  
     El XAML se actualiza inmediatamente para mostrar la nueva imagen de fondo.  
  
9. Haga clic en el icono de pincel nulo.  
  
     El fondo del diseñador devuelve un valor neutro y el atributo `BackGround` está establecido en `"{x:Null}"`.  
  
## Consulta de valores del sistema  
 Puede consultar los valores del sistema mediante las propiedades de clase <xref:Microsoft.VisualStudio.Shell.VsBrushes?displayProperty=fullName>, que hacen referencia a los pinceles establecidos en otras partes de Visual Studio.  
  
#### Para establecer colores, degradados y opacidad consultando los valores del sistema  
  
1.  Seleccione un elemento XAML.  
  
2.  En la definición del elemento, establezca uno de los atributos visuales del elemento en una propiedad de la clase `VsBrushes`, como se muestra en el ejemplo siguiente.  
  
     [!code-xml[TWShortcutMenu#32](../misc/codesnippet/Xaml/setting-colors-gradients-and-opacity_1.xaml)]  
  
     El uso de la extensión [DynamicResource](../Topic/DynamicResource%20Markup%20Extension.md) permite cambiar el valor según sea necesario como, por ejemplo, cuando un usuario cambia la configuración. Debe usar la extensión [x:Static](../Topic/x:Static%20Markup%20Extension.md) porque la clase `VsBrushes` no forma parte del espacio de nombres WPF predeterminado.  
  
## Vea también  
 [Extender ventanas de herramientas](../misc/extending-tool-windows.md)