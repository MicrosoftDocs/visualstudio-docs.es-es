---
title: 'Cómo: Compilar y ejecutar el ejemplo LinqToXmlDataBinding | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3943deaf-80e2-4968-ac04-d3ef56cfad6c
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9e299000cd8477ccc36829e806072cb25e115f8f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237918"
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>Cómo: Compilar y ejecutar el ejemplo LinqToXmlDataBinding
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se muestra cómo crear y compilar el proyecto LinqToXmlDataBinding de Visual Studio  y cómo ejecutar el programa de ejemplo LinqToXmlDataBinding de Windows Presentation Foundation (WPF) resultante.  
  
 Para más información sobre el uso de Visual Studio para crear proyectos, vea [Desarrollo de aplicaciones en Visual Studio](http://msdn.microsoft.com/en-us/97490c1b-a247-41fb-8f2c-bc4c201eff68).  
  
## <a name="creating-and-populating-the-project"></a>Crear y rellenar el proyecto  
  
#### <a name="to-create-the-starting-project"></a>Para crear el proyecto inicial  
  
1.  Inicie Visual Studio y cree una aplicación WPF de C# con el nombre LinqToXmlDataBinding. El proyecto debe usar .NET Framework 3.5 (o posterior).  
  
2.  Si aún no están presentes, agregue referencias al proyecto para los siguientes ensamblados de .NET:  
  
    -   System.Data  
  
    -   System.Data.DataSetExtensions  
  
    -   System.Xml  
  
    -   System.Xml.Linq  
  
3.  Compile la solución presionando **Ctrl+Mayús+B** y después presione **F5** para ejecutarla. El proyecto debería compilarse sin errores y ejecutarse como una aplicación WPF genérica.  
  
#### <a name="to-add-custom-code-to-the-project"></a>Para agregar código personalizado al proyecto  
  
1.  En el Explorador de soluciones, cambie el nombre del archivo de origen Window1.xaml a L2XDBForm.xaml. El archivo de origen Window1.xaml.cs dependiente debería cambiar automáticamente de nombre a L2XDBForm.xaml.cs.  
  
2.  Sustituya el código fuente del archivo L2XDBForm.xaml con la sección de código del tema [Código fuente de L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md). (Use la vista de origen de XAML para trabajar con este archivo).  
  
3.  De igual modo, sustituya el código fuente de L2XDBForm.xaml.cs con el código de [Código fuente de L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md).  
  
4.  En el archivo App.xaml, sustituya todas las apariciones de la cadena "Window1.xaml" con "L2XDBForm.xaml".  
  
5.  Compile la solución presionando **Ctrl+Mayús+B**.  
  
## <a name="running-the-program"></a>Ejecutar el programa  
 El programa LinqToXmlDataBinding permite al usuario ver y manipular una lista de libros que está almacenada como un elemento XML incrustado.  
  
#### <a name="to-run-the-program-and-view-the-book-list"></a>Para ejecutar el programa y ver la lista de libros  
  
1.  Ejecute LinqToXmlDataBinding presionando **F5** (**Iniciar depuración**) o **Ctrl+F5** (**Iniciar sin depurar**). Debería mostrarse una ventana de programa con el título **Enlace de datos de WPF con LINQ to XML**.  
  
2.  Observe la sección superior de la interfaz de usuario, en la que se muestra el código **XML** sin formato que representa la lista de libros. Se muestra mediante un control <xref:System.Windows.Controls.TextBlock> de WPF, que no permite la interacción a través del mouse o del teclado.  
  
3.  En la segunda sección vertical, con la etiqueta **Lista de libros**, se muestran los libros como una lista ordenada de texto sin formato. Utiliza un control <xref:System.Windows.Controls.ListBox> que permite la selección a través del mouse o del teclado.  
  
#### <a name="to-add-and-delete-books-from-the-list"></a>Para agregar y eliminar libros de la lista  
  
1.  Para eliminar un libro existente de la lista, selecciónelo en la sección **Lista de libros** y haga clic en el botón **Quitar el libro seleccionado**. Observe que la entrada del libro se ha quitado del libro y de los listados de origen XML sin formato.  
  
2.  Para agregar un nuevo libro a la lista, escriba los valores en los controles **Id.** y **Valor**<xref:System.Windows.Controls.TextBox> de la última sección, haga clic en **Agregar nuevo libro** y, después, haga clic en el botón **Agregar libro**. Observe que el libro se adjunta a la lista en los listados de libros y XML. Este programa no valida los valores de entrada.  
  
#### <a name="to-edit-an-existing-book-entry"></a>Para editar una entrada de libro existente  
  
1.  Seleccione la entrada del libro en la segunda sección **Lista de libros**. Sus valores actuales se deben mostrar en la tercera sección, **Editar el libro seleccionado**.  
  
2.  Edite los valores usando el teclado. En cuanto el control <xref:System.Windows.Controls.TextBox> pierda el enfoque los cambios se propagarán automáticamente al origen de XML y a los listados de libros.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de enlace de datos WPF mediante LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)   
 [Tutorial: LinqToXmlDataBinding Example](../designers/walkthrough-linqtoxmldatabinding-example.md)   
 [Desarrollo de aplicaciones en Visual Studio](http://msdn.microsoft.com/en-us/97490c1b-a247-41fb-8f2c-bc4c201eff68)



