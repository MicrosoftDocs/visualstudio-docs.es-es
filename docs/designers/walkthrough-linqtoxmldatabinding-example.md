---
title: 'Tutorial: Ejemplo de LinqToXmlDataBinding'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 567b03f9f0441e7f5eb38f4ca0e0b3a1d64cec91
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081197"
---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>Tutorial: Ejemplo de LinqToXmlDataBinding
En este tutorial se describe el ejemplo LinqToXmlDataBinding y se explica parte del contenido más interesante de sus dos archivos de origen principales, *L2DBForm.xaml* y *L2DBForm.xaml.cs*.

## <a name="prerequisites"></a>Requisitos previos
 Antes de leer este tutorial, se recomienda encarecidamente compilar y ejecutar el programa LinqToXmlDataBinding, como se describe en [Cómo compilar y ejecutar el ejemplo LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md).

## <a name="remarks"></a>Comentarios
 El programa LinqToXmlDataBinding es una aplicación de Windows Presentation Foundation (WPF) que consta de archivos de origen C# y XAML. Contiene un documento XML incrustado que define una lista de libros, y permite que el usuario vea, agregue, elimine y edite estas entradas. Consta de los dos archivos de origen principales siguientes:

-   *L2DBForm.xaml* contiene el código de declaración XAML para la interfaz de usuario (IU) de la ventana principal. También contiene una sección de recursos de la ventana que define un proveedor de datos y un documento XML incrustado para la lista de libros.

-   *L2DBForm.xaml.cs* contiene los métodos de control de eventos y de inicialización asociados a la IU.

 La ventana principal se divide en las cuatro secciones de IU verticales siguientes:

-   **XML** muestra el origen XML sin procesar de la lista de libros insertada.

-   **Lista de libros** muestra las entradas de libro como texto estándar y permite que el usuario seleccione y elimine entradas individuales.

-   **Edit Selected Book** (Editar libro seleccionado) permite que el usuario edite los valores asociados a la entrada de libro seleccionada actualmente.

-   **Add New Book** (Agregar nuevo libro) permite la creación de una entrada de libro según los valores especificados por el usuario.

## <a name="in-this-section"></a>En esta sección

|Tema|Descripción|
|-----------|-----------------|
|[Código fuente de L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md)|Incluye el contenido y la descripción del código XAML en el archivo L2DBForm.xaml.|
|[Código fuente de L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)|Incluye el contenido y la descripción del código fuente C# del archivo L2DBForm.xaml.cs.|

## <a name="see-also"></a>Vea también

- [Ejemplo de enlace de datos de WPF con LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)
- [Cómo: compilar y ejecutar el ejemplo LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)