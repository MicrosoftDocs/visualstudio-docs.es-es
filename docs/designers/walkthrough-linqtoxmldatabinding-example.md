---
title: 'Tutorial: Ejemplo de LinqToXmlDataBinding | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bc78fd4331839ce1a55253a719c40f8b19dea491
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>Tutorial: Ejemplo de LinqToXmlDataBinding
Este tutorial describe el ejemplo de LinqToXmlDataBinding y explica algunos de los contenidos más interesantes de sus dos archivos de origen principales (L2DBForm.xaml y L2DBForm.xaml.cs).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Antes de leer este tutorial, recomendamos crear y ejecutar el programa LinqToXmlDataBinding, tal y como se describe en [Cómo compilar y ejecutar el ejemplo LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md).  
  
## <a name="remarks"></a>Comentarios  
 El programa LinqToXmlDataBinding es una aplicación de Windows Presentation Foundation (WPF) que consta de archivos de origen C# y XAML. Contiene un documento XML incrustado que define una lista de libros, y permite que el usuario vea, agregue, elimine y edite estas entradas. Consta de los dos archivos de origen principales siguientes:  
  
-   L2DBForm.xaml contiene el código de declaración XAML para la interfaz de usuario (IU) de la ventana principal. También contiene una sección de recursos de la ventana que define un proveedor de datos y un documento XML incrustado para la lista de libros.  
  
-   L2DBForm.xaml.cs contiene los métodos de control de eventos y de inicialización asociados a la IU.  
  
 La ventana principal se divide en las cuatro secciones de IU verticales siguientes:  
  
-   **XML** muestra el origen XML sin procesar de la lista de libros insertada.  
  
-   **Lista de libros** muestra las entradas de libro como texto estándar y permite que el usuario seleccione y elimine entradas individuales.  
  
-   **Edit Selected Book** (Editar libro seleccionado) permite que el usuario edite los valores asociados a la entrada de libro seleccionada actualmente.  
  
-   **Add New Book** (Agregar nuevo libro) permite la creación de una entrada de libro según los valores especificados por el usuario.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Tema|Description|  
|-----------|-----------------|  
|[Código fuente de L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md)|Incluye el contenido y la descripción del código XAML en el archivo L2DBForm.xaml.|  
|[Código fuente de L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)|Incluye el contenido y la descripción del código fuente C# del archivo L2DBForm.xaml.cs.|  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de enlace de datos WPF mediante LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)   
 [Cómo: Compilar y ejecutar el ejemplo LinqToXmlDataBinding](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)