---
title: Página Referencias, Diseñador de proyectos (Visual Basic) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesReference
- vb.ProjectPropertiesUnusedReference
- vb.ProjectPropertiesReferencePaths
helpviewer_keywords:
- References page in Project Designer
- Project Designer, References page
- Unused References dialog box
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0dabf5b84eb1adde1d6e579b7ec5ad6a6c443723
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859062"
---
# <a name="references-page-project-designer-visual-basic"></a>Página Referencias, Diseñador de proyectos (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Use la página **Referencias** del **Diseñador de proyectos** para administrar las referencias, las referencias web y los espacios de nombres importados en su proyecto. Los proyectos pueden contener referencias a componentes COM, servicios Web XML, bibliotecas de clases o ensamblados de .NET Framework u otras bibliotecas de clases. Para obtener más información sobre el uso de referencias, vea [Administrar referencias en un proyecto](../../ide/managing-references-in-a-project.md).  
  
 Para obtener acceso a la página **Referencias**, seleccione un nodo de proyecto (no el nodo **Solución**) en el **Explorador de soluciones**. Después, pulse **Proyecto**, **Propiedades** en la barra de menús. Cuando se muestre el Diseñador de proyectos, haga clic en la pestaña **Referencias**.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 Las opciones siguientes le permiten seleccionar o quitar referencias y espacios de nombres importados en su proyecto.  
  
 **Referencias sin usar**  
 Haga clic en este botón para tener acceso al cuadro de diálogo **Referencias sin usar**.  
  
 El cuadro de diálogo **Referencias sin usar** le permite quitar referencias que se incluyen en su proyecto pero que el código no usa realmente. Contiene una cuadrícula que muestra el **Nombre de referencia**, la **Ruta de acceso** y otra información sobre las referencias del espacio de nombres sin usar de su proyecto. En la cuadrícula, seleccione las referencias del espacio de nombres que quiere quitar de su proyecto y haga clic en **Quitar**.  
  
 **Rutas de acceso de referencia**  
 Haga clic en este botón para tener acceso al cuadro de diálogo **Rutas de acceso de referencia**.  
  
> [!NOTE]
>  Cuando el sistema del proyecto busca una referencia de ensamblado, el sistema resuelve la referencia buscando en las siguientes ubicaciones, en el orden siguiente:  
> 
> 1. La carpeta del proyecto. Los archivos de la carpeta del proyecto aparecen en el **Explorador de soluciones** cuando **Mostrar todos los archivos** no está en vigor.  
>    2.  Las carpetas que se especifican en el cuadro de diálogo **Rutas de acceso de referencia**.  
>    3.  Las carpetas que muestran archivos en el cuadro de diálogo **Agregar referencia**.  
>    4.  La carpeta de objetos del proyecto. (Cuando agrega una referencia COM a su proyecto, uno o más ensamblados pueden agregarse a la carpeta de objetos del proyecto).  
  
 **Referencias**  
 Esta lista muestra todas las referencias del proyecto, usadas o sin usar.  
  
 **Add**  
 Haga clic en este botón para agregar una referencia o una referencia web a la lista **Referencias**.  
  
 Pulse **Referencia** para agregar una referencia a su proyecto con el cuadro de diálogo Agregar referencia.  
  
 Pulse **Referencia web** para agregar una referencia web a su proyecto con el cuadro de diálogo Agregar referencia web.  
  
 **Remove**  
 Seleccione una o más referencias en la lista **Referencias**, después, haga clic en este botón para eliminarlas.  
  
 **Actualizar referencia web**  
 Seleccione una referencia web en la lista **Referencias** y haga clic en este botón para actualizarla.  
  
 **Espacios de nombres importados**  
 Puede escribir su propio espacio de nombres en este cuadro y hacer clic en **Agregar importación del usuario** para agregarlo a la lista de espacios de nombres.  
  
 Puede crear alias para los espacios de nombres importados por el usuario. Para realizar esto, escriba el alias y el espacio de nombres en el formato *alias*=*espacio de nombres*. Esto es útil si está usando espacios de nombres largos, por ejemplo: `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`.  
  
 **Agregar importación del usuario**  
 Haga clic en este botón para agregar el espacio de nombres especificado en el cuadro **Espacios de nombres importados** a la lista de espacios de nombres importados. El botón solo está activo si el espacio de nombres especificado todavía no está en la lista.  
  
 **Lista de espacios de nombres**  
 Esta lista muestra todos los espacios de nombres disponibles. Las casillas de los espacios de nombres incluidas en el proyecto están seleccionadas.  
  
 **Actualizar importación del usuario**  
 Seleccione un espacio de nombres especificado por el usuario en la lista de espacios de nombres, escriba el nombre por el que quiere reemplazarlo en el cuadro **Espacios de nombres importados** y, después, haga clic en este botón para cambiar al nuevo espacio de nombres. El botón está activo solo si el espacio de nombres seleccionado es uno que ha agregado a la lista con el botón **Agregar importación del usuario**. Puede agregar:  
  
-   Clases o espacios de nombres, como <xref:System.Math?displayProperty=fullName>.  
  
-   Importaciones de alias, como `VB=Microsoft.VisualBasic`.  
  
-   Espacios de nombres XML, como `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`.  
  
## <a name="see-also"></a>Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Cómo: agregar o quitar referencias mediante el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Cómo: Agregar o quitar espacios de nombres importados (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)   
 [Agregar cuadro de diálogo de referencia Web](http://msdn.microsoft.com/en-us/bdf05776-c591-40af-bfd7-e1e2aa1e87b5)   
 [Imports (instrucción), espacio de nombres XML](http://msdn.microsoft.com/library/1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4)



