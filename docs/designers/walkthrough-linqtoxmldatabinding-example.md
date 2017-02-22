---
title: "Tutorial: Ejemplo de LinqToXmlDataBinding | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tutorial: Ejemplo de LinqToXmlDataBinding
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tutorial describe el ejemplo de LinqToXmlDataBinding y explica algunos de los contenidos más interesantes de sus dos archivos de origen principales \(L2DBForm.xaml y L2DBForm.xaml.cs\).  
  
## Requisitos previos  
 Antes de leer este tutorial, es recomendable que cree y ejecute el programa LinqToXmlDataBinding, tal como se describe en [Cómo compilar y ejecutar el ejemplo LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md).  
  
## Notas  
 El programa LinqToXmlDataBinding es una aplicación de Windows Presentation Foundation \(WPF\) que consta de archivos de origen C\# y XAML.Contiene un documento XML incrustado que define una lista de libros, y permite que el usuario vea, agregue, elimine y edite estas entradas.Consta de los dos archivos de origen principales siguientes:  
  
-   L2DBForm.xaml contiene el código de declaración XAML para la interfaz de usuario \(IU\) de la ventana principal.También contiene una sección de recursos de la ventana que define un proveedor de datos y un documento XML incrustado para la lista de libros.  
  
-   L2DBForm.xaml.cs contiene los métodos de control de eventos y de inicialización asociados a la IU.  
  
 La ventana principal se divide en las cuatro secciones de IU verticales siguientes:  
  
-   **XML** muestra el origen XML sin formato de la lista de libros incrustada.  
  
-   **Lista de libros** muestra las entradas de libro como texto estándar y permite que el usuario seleccione y elimine entradas individuales.  
  
-   **Editar libro seleccionado** permite que el usuario edite los valores asociados a la entrada de libro seleccionada actualmente.  
  
-   **Agregar nuevo libro** permite la creación de una entrada de libro nueva según los valores especificados por el usuario.  
  
## En esta sección  
  
|Tema|Descripción|  
|----------|-----------------|  
|[Código fuente de L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md)|Incluye el contenido y la descripción del código XAML en el archivo L2DBForm.xaml.|  
|[Código de origen de L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)|Incluye el contenido y la descripción del código fuente C\# del archivo L2DBForm.xaml.cs.|  
  
## Vea también  
 [Ejemplo de enlace de datos de WPF con LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)   
 [Cómo compilar y ejecutar el ejemplo LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)