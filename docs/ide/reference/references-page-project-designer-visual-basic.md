---
title: "P&#225;gina Referencias, Dise&#241;ador de proyectos (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesReference"
  - "vb.ProjectPropertiesUnusedReference"
  - "vb.ProjectPropertiesReferencePaths"
helpviewer_keywords: 
  - "Página de referencias en el Diseñador de proyectos"
  - "Diseñador de proyectos, página Referencias"
  - "Cuadro de diálogo Referencias sin utilizar"
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
caps.latest.revision: 34
caps.handback.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# P&#225;gina Referencias, Dise&#241;ador de proyectos (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilice la página **Referencias** del **Diseñador de proyectos** para administrar referencias, referencias Web y espacios de nombres importados en el proyecto.  Los proyectos pueden contener referencias a componentes COM, servicios Web XML, bibliotecas de clases o ensamblados de .NET Framework u otras bibliotecas de clases.  Para obtener más información sobre cómo utilizar referencias, vea [Administrar referencias en un proyecto](../../ide/managing-references-in-a-project.md).  
  
 Para tener acceso a la página **References**, elija un nodo del proyecto \(no el nodo **Solución** \) en **Explorador de soluciones**.  A continuación **proyecto**, **propiedades** en la barra de menús.  Cuando aparezca el Diseñador de proyectos, haga clic en la ficha **References**.  
  
## Lista de UIElement  
 Las opciones siguientes le permiten seleccionar o quitar referencias y espacios de nombres importados en el proyecto.  
  
 **Referencias sin utilizar**  
 Haga clic en este botón para tener acceso al cuadro de diálogo **Referencias sin utilizar**.  
  
 El cuadro de diálogo **Referencias sin utilizar** permite quitar referencias incluidas en su proyecto pero que el código no utiliza realmente.  Contiene una cuadrícula que muestra **Nombre de la referencia**, **Ruta de acceso**, y otra información sobre el espacio de nombres no hace referencia en el proyecto.  En la cuadrícula, seleccione las referencias de espacio de nombres que quiere quitar del proyecto y haga clic en **Quitar**.  
  
 **Rutas de acceso de referencia**  
 Haga clic en este botón para tener acceso al cuadro de diálogo **Rutas de acceso de referencia**.  
  
> [!NOTE]
>  Cuando el sistema de proyectos encuentra una referencia de ensamblado, el sistema resuelve la referencia buscando en las ubicaciones siguientes, en el orden siguiente:  
>   
>  1.  La carpeta de proyecto.  Los archivos de la carpeta de proyecto aparecen en **Explorador de soluciones** cuando **mostrar todos los archivos** no está activada.  
> 2.  Carpetas que se especifican en el cuadro de diálogo **Rutas de acceso de referencia**.  
> 3.  Carpetas que generan archivos en el cuadro de diálogo **Agregar referencia**.  
> 4.  La carpeta obj del proyecto.  \(Cuando se agrega una referencia COM al proyecto, uno o más ensamblados se pueden agregar a la carpeta obj del proyecto\).  
  
 **Referencias**  
 Esta lista muestra todas las referencias del proyecto, utilizadas o sin utilizar.  
  
 **Agregar**  
 Haga clic en este botón para agregar una referencia o una referencia Web a la lista **Referencias**.  
  
 Elija **Referencia** para agregar una referencia al proyecto a través del cuadro de diálogo Agregar referencia.  
  
 Elija **Referencia web** para agregar una referencia web al proyecto utilizando el cuadro de diálogo Agregar referencia web.  
  
 **Remove**  
 Seleccione una o más referencias en la lista **Referencias**, a continuación, haga clic en este botón para eliminarlas.  
  
 **Actualizar referencia Web**  
 Seleccione una referencia Web en la lista **Referencias** y haga clic en este botón para actualizarla.  
  
 **Espacios de nombres importados**  
 Puede escribir su propio espacio de nombres en este cuadro y hacer clic en **Agregar importación del usuario** para agregarlo a la lista de espacios de nombres.  
  
 Puede crear los alias para los espacios de nombres importados por el usuario.  Para ello, escriba el alias y el espacio de nombres con el formato *alias*\=*espacio de nombres*.  Esto resulta útil si utiliza espacios de nombres largos, por ejemplo: `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`.  
  
 **Agregar importación del usuario**  
 Haga clic en este botón para agregar el espacio de nombres especificado en el cuadro **Espacios de nombres importados** a la lista de espacios de nombres importados.  El botón sólo está activo si el espacio de nombres especificado aún no está en la lista.  
  
 **Lista de espacios de nombres**  
 Esta lista muestra todos los espacios de nombres disponibles.  Las casillas de los espacios de nombres incluidos en el proyecto están activadas.  
  
 **Actualizar importación del usuario**  
 Seleccione un espacio de nombres especificado por el usuario en la lista de espacios de nombres, escriba el nombre con el que desea reemplazarlo en el cuadro **Espacios de nombres importados** y, a continuación, haga clic en este botón para cambiar al nuevo espacio de nombres.  El botón sólo está activo si el espacio de nombres seleccionado es uno de los agregados a la lista con el botón **Agregar importación del usuario**.  Puede agregar:  
  
-   Clases o espacios de nombres, como <xref:System.Math?displayProperty=fullName>.  
  
-   Importaciones con alias, como `VB=Microsoft.VisualBasic`.  
  
-   Espacios de nombres XML, como `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`.  
  
## Vea también  
 [Cómo: Agregar o quitar referencias utilizando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Cómo: Agregar o quitar espacios de nombres importados \(Visual Basic\)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)   
 [Agregar referencia Web \(Cuadro de diálogo\)](http://msdn.microsoft.com/es-es/bdf05776-c591-40af-bfd7-e1e2aa1e87b5)   
 [Imports \(Instrucción, Espacio de nombres XML\)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)