---
title: "C&#243;mo compilar y ejecutar el ejemplo LinqToXmlDataBinding | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3943deaf-80e2-4968-ac04-d3ef56cfad6c
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# C&#243;mo compilar y ejecutar el ejemplo LinqToXmlDataBinding
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tema se muestra cómo crear y compilar el proyecto LinqToXmlDataBinding de Visual Studio  y cómo ejecutar el programa de ejemplo LinqToXmlDataBinding de Windows Presentation Foundation \(WPF\) resultante.  
  
 Para obtener más información sobre el uso de Visual Studio para crear proyectos, vea [Desarrollo de aplicaciones en Visual Studio](http://msdn.microsoft.com/es-es/97490c1b-a247-41fb-8f2c-bc4c201eff68).  
  
## Crear y rellenar el proyecto  
  
#### Para crear el proyecto inicial  
  
1.  Inicie Visual Studio y cree una aplicación WPF de C\# con el nombre LinqToXmlDataBinding.El proyecto debe usar .NET Framework 3.5 \(o posterior\).  
  
2.  Si aún no están presentes, agregue referencias al proyecto para los siguientes ensamblados de .NET:  
  
    -   System.Data  
  
    -   System.Data.DataSetExtensions  
  
    -   System.Xml  
  
    -   System.Xml.Linq  
  
3.  Compile la solución presionando **Ctrl\+Mayús\+B** y ejecútela presionando **F5**.El proyecto debería compilarse sin errores y ejecutarse como una aplicación WPF genérica.  
  
#### Para agregar código personalizado al proyecto  
  
1.  En el Explorador de soluciones, cambie el nombre del archivo de origen Window1.xaml a L2XDBForm.xaml.El archivo de origen Window1.xaml.cs dependiente debería cambiar automáticamente de nombre a L2XDBForm.xaml.cs.  
  
2.  Sustituya el código de origen hallado en el archivo L2XDBForm.xaml con la sección de código del tema [Código fuente de L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md).\(Use la vista de origen de XAML para trabajar con este archivo\).  
  
3.  De igual modo, sustituya el código fuente de L2XDBForm.xaml.cs con el código hallado en [Código de origen de L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md).  
  
4.  En el archivo App.xaml, sustituya todas las apariciones de la cadena "Window1.xaml" con "L2XDBForm.xaml".  
  
5.  Compile la solución presionando **Ctrl\+Mayús\+B**.  
  
## Ejecutar el programa  
 El programa LinqToXmlDataBinding permite al usuario ver y manipular una lista de libros que está almacenada como un elemento XML incrustado.  
  
#### Para ejecutar el programa y ver la lista de libros  
  
1.  Ejecute LinqToXmlDataBinding presionando **F5** \(**Iniciar depuración**\) o **Ctrl\+F5** \(**Iniciar sin depurar**\).Debería mostrarse una ventana de programa con el título **Enlace de datos de WPF utilizando LINQ to XML**.  
  
2.  Observe la sección superior de la IU, que muestra **XML** sin formato que representa la lista de libros.Se muestra mediante un control <xref:System.Windows.Controls.TextBlock> de WPF, que no permite la interacción a través del mouse o del teclado.  
  
3.  La segunda sección vertical, con la etiqueta **Lista de libros**, muestra los libros como una lista ordenada de texto sin formato.Utiliza un control <xref:System.Windows.Controls.ListBox> que permite la selección a través del mouse o del teclado.  
  
#### Para agregar y eliminar libros de la lista  
  
1.  Para eliminar un libro existente de la lista, selecciónelo en la sección **Lista de libros** y haga clic en el botón **Quitar el libro seleccionado**.Observe que la entrada del libro se ha quitado del libro y de los listados de origen XML sin formato.  
  
2.  Para agregar un nuevo libro a la lista, especifique los valores en los controles **Id.** y **Valor**<xref:System.Windows.Controls.TextBox> de la última sección, haga clic en **Agregar nuevo libro** y, a continuación, haga clic en  el botón **Agregar libro**.Observe que el libro se adjunta a la lista en los listados de libros y XML.Este programa no valida los valores de entrada.  
  
#### Para editar una entrada de libro existente  
  
1.  Seleccione la entrada del libro en la segunda sección **Lista de libros**.Sus valores actuales se deben mostrar en la tercera sección, **Editar el libro seleccionado**.  
  
2.  Edite los valores usando el teclado.En cuanto el control <xref:System.Windows.Controls.TextBox> pierda el enfoque los cambios se propagarán automáticamente al origen de XML y a los listados de libros.  
  
## Vea también  
 [Ejemplo de enlace de datos de WPF con LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)   
 [Tutorial: Ejemplo de LinqToXmlDataBinding](../designers/walkthrough-linqtoxmldatabinding-example.md)   
 [Desarrollo de aplicaciones en Visual Studio](http://msdn.microsoft.com/es-es/97490c1b-a247-41fb-8f2c-bc4c201eff68)