---
title: 'Cómo: Compilar y ejecutar el ejemplo LinqToXmlDataBinding'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1164312d74259ad4f3a56750a487fb2578595cf0
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924166"
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>Cómo: Compilar y ejecutar el ejemplo LinqToXmlDataBinding

En este tema se muestra cómo crear y compilar el proyecto LinqToXmlDataBinding de Visual Studio  y cómo ejecutar el programa de ejemplo LinqToXmlDataBinding de Windows Presentation Foundation (WPF) resultante.

Para obtener más información sobre Visual Studio, vea [Introducción al IDE de Visual Studio](../ide/visual-studio-ide.md).

## <a name="create-and-populate-the-project"></a>Crear y rellenar el proyecto

### <a name="to-create-the-starting-project"></a>Para crear el proyecto inicial

1. Inicie Visual Studio y cree una aplicación WPF de C# con el nombre LinqToXmlDataBinding. El proyecto debe usar .NET Framework 3.5 (o posterior).

1. Si aún no están presentes, agregue referencias al proyecto para los siguientes ensamblados de .NET:

    - System.Data

    - System.Data.DataSetExtensions

    - System.Xml

    - System.Xml.Linq

1. Compile la solución presionando **Ctrl**+**Mayús**+**B** y después presione **F5** para ejecutarla. El proyecto debería compilarse sin errores y ejecutarse como una aplicación WPF genérica.

### <a name="to-add-custom-code-to-the-project"></a>Para agregar código personalizado al proyecto

1. En el Explorador de soluciones, cambie el nombre del archivo de origen **Window1.xaml** a **L2XDBForm.xaml**. El archivo de origen **Window1.xaml.cs** dependiente debería cambiar automáticamente de nombre a **L2XDBForm.xaml.cs**.

1. Sustituya el código fuente del archivo **L2XDBForm.xaml** con la sección de código del tema [Código fuente de L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md). (Use la vista de origen de XAML para trabajar con este archivo).

1. De igual modo, sustituya el código fuente de **L2XDBForm.xaml.cs** con el código de [Código fuente de L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md).

1. En el archivo **App.xaml** sustituya todas las apariciones de la cadena `Window1.xaml` con `L2XDBForm.xaml`.

1. Compile la solución presionando **Ctrl**+**Mayús**+**B**.

## <a name="run-the-program"></a>Ejecutar el programa

El programa LinqToXmlDataBinding permite al usuario ver y manipular una lista de libros que está almacenada como un elemento XML incrustado.

### <a name="to-run-the-program-and-view-the-book-list"></a>Para ejecutar el programa y ver la lista de libros

- Ejecute LinqToXmlDataBinding presionando **F5** (**Iniciar depuración**) o **Ctrl**+**F5** (**Iniciar sin depurar**).

   Se muestra una ventana de programa con el título **Enlace de datos de WPF con LINQ to XML**.

- Observe la sección superior de la interfaz de usuario, en la que se muestra el código **XML** sin formato que representa la lista de libros. Se muestra mediante un control <xref:System.Windows.Controls.TextBlock> de WPF, que no permite la interacción a través del mouse o del teclado.

- En la segunda sección vertical, con la etiqueta **Lista de libros**, se muestran los libros como una lista ordenada de texto sin formato. Utiliza un control <xref:System.Windows.Controls.ListBox> que permite la selección a través del mouse o del teclado.

### <a name="to-add-and-delete-books-from-the-list"></a>Para agregar y eliminar libros de la lista

- Para agregar un nuevo libro a la lista, escriba los valores en los controles **Id.** y **Valor**<xref:System.Windows.Controls.TextBox> de la última sección, haga clic en **Agregar nuevo libro** y, después, haga clic en el botón **Agregar libro**. Observe que el libro se adjunta a la lista en los listados de libros y XML. Este programa no valida los valores de entrada.

- Para eliminar un libro existente de la lista, selecciónelo en la sección **Lista de libros** y haga clic en el botón **Quitar el libro seleccionado**. Observe que la entrada del libro se ha quitado del libro y de los listados de origen XML sin formato.

### <a name="to-edit-an-existing-book-entry"></a>Para editar una entrada de libro existente

1. Seleccione la entrada del libro en la segunda sección **Lista de libros**. Sus valores actuales se deben mostrar en la tercera sección, **Editar el libro seleccionado**.

1. Edite los valores usando el teclado. En cuanto el control <xref:System.Windows.Controls.TextBox> pierda el enfoque los cambios se propagarán automáticamente al origen de XML y a los listados de libros.

## <a name="see-also"></a>Vea también

- [Ejemplo de enlace de datos WPF mediante LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)
- [Tutorial: Ejemplo de LinqToXmlDataBinding](../designers/walkthrough-linqtoxmldatabinding-example.md)
- [Introducción al IDE de Visual Studio](../ide/visual-studio-ide.md)