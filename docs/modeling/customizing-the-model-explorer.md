---
title: Personalizar el Explorador de modelos
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 781e1cce1d363ade1d236c8e17f9c3feeb4b0f5c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913293"
---
# <a name="customizing-the-model-explorer"></a>Personalizar el Explorador de modelos
Puede cambiar la apariencia y comportamiento del explorador para el Diseñador de lenguaje específico de dominio como sigue:

-   Cambie el título de ventana.

-   Cambiar el icono de pestaña.

-   Cambiar los iconos para los nodos.

-   Ocultar los nodos.

## <a name="changing-the-window-title"></a>Cambiar el título de ventana
 Para cambiar el título de la ventana del explorador generado, seleccione **comportamiento de Explorer** en el **DSL Explorer**y, a continuación, en el **propiedades** ventana, establezca el  **Título** propiedad para el título que desee.

## <a name="changing-the-tab-icon"></a>Cambio del icono de pestaña
 Para cambiar el icono de pestaña en el explorador, use un icono de 16 x 16 píxeles en un archivo. bmp. Coloque el archivo de icono en la carpeta \DslPackage\Resources\ y, a continuación, cambie el nombre de archivo a **ModelExplorerToolWindowBitmaps.bmp**. Por ejemplo, podría cambiar el archivo de icono de Visual Studio setup.ico al formato .bmp y cambie su nombre a **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. El diseñador generado mostrará este icono en la pestaña de su explorador cuando se acopla junto con **el Explorador de soluciones**.

## <a name="setting-custom-icons-on-explorer-nodes"></a>Establecer iconos personalizados en los nodos del explorador
 Puede personalizar los nodos en el explorador mediante la configuración de nodo del explorador. El procedimiento siguiente muestra cómo agregar un icono a un nodo.

#### <a name="to-add-an-icon-to-an-explorer-node"></a>Para agregar un icono a un nodo del explorador

1. Crear un [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] solución mediante la plantilla de solución de flujo de tareas.

2. Coloque un archivo .bmp que contiene un icono de 16 x 16 píxeles en el **Dsl\Resources** carpeta en la solución.

3. En el **DSL Explorer**, haga clic en **comportamiento de Explorer** y, a continuación, haga clic en **agregar nueva configuración de nodo de explorador**.

    Un **ExplorerNodeSettings** nodo aparece en el **configuración personalizada del nodo** nodo.

4. Seleccione **ExplorerNodeSettings**y, a continuación, en el **propiedades** ventana, establezca **clase** a **Actor**.

5. Establecer **icono para mostrar** a la ruta de acceso del archivo del icono.

6. Transformar todas las plantillas y, a continuación, compilar y ejecutar la solución.

7. En el diseñador generado, abra el diagrama de ejemplo.

    El explorador debería mostrar tres **Actor** nodos que tengan su icono.

> [!NOTE]
>  Si ha establecido un icono de nodo para cualquier elemento que se muestra en el explorador generado, todos los nodos del explorador mostrará el icono. Si no se ha establecido ningún icono, los nodos mostrará el icono predeterminado.

## <a name="changing-the-name-displayed-on-an-explorer-node"></a>Cambiar el nombre mostrado en un nodo del explorador
 Puede cambiar cómo se muestran los nombres de los elementos del modelo en el explorador. El siguiente procedimiento muestra cómo mostrar el nombre de la **tarea** que hace referencia un **comentario** en el nodo de comentario.

#### <a name="to-display-a-property"></a>Para mostrar una propiedad

1.  Abra la solución que creó en el procedimiento anterior.

2.  Asegúrese de que el **comentario** hace referencia a solo una clase de dominio único, establezca la multiplicidad del rol con el nombre de la propiedad **asuntos** a 0.. 1. El nombre de propiedad debe convertirse en **asunto**, y debe ser el nombre de la relación **CommentReferencesSubject**.

3.  En el **DSL Explorer**, haga clic en **comportamiento de Explorer** y, a continuación, haga clic en **agregar nueva configuración de nodo de explorador**.

     Un **ExplorerNodeSettings** nodo aparece en el **configuración personalizada del nodo** nodo.

4.  Seleccione **ExplorerNodeSettings**y, a continuación, en el **propiedades** ventana, establezca **clase** a **comentario**.

5.  Haga clic en el **comentario** nodo y, a continuación, haga clic en **agregar nueva ruta de acceso de propiedad**.

     Aparece un nuevo nodo denominado **propiedad muestra**.

6.  Seleccione **propiedad muestra**y, a continuación, en el **propiedades** ventana, haga clic en el campo de valor de **ruta de acceso a la propiedad**. Seleccione **comentario**, a continuación, **CommentReferencesSubject**, a continuación, **FlowElement**. La ruta de acceso resultante debe ser similar a **CommentReferencesSubject.Subject/! Asunto**.

7.  En el campo de valor de **propiedad**, seleccione **nombre**.

8.  Transformar todas las plantillas y, a continuación, compilar y ejecutar la solución.

9. En el diseñador generado, abra el diagrama de ejemplo.

10. Dibujar un **conector comentario** entre el elemento de comentario y el **Task1** elemento del diagrama.

     El nodo del explorador debe mostrar el comentario como **Task1**.

## <a name="hiding-nodes"></a>Al ocultar nodos
 Puede ocultar un nodo en el explorador mediante la adición de su ruta de acceso a la **nodos ocultos** nodo de la **DSL Explorer**. El siguiente procedimiento muestra cómo ocultar **comentario** nodos.

#### <a name="to-hide-an-explorer-node"></a>Para ocultar un nodo del explorador

1.  Abra la solución que creó en el procedimiento anterior.

2.  En el **DSL Explorer**, haga clic en **comportamiento de Explorer** y, a continuación, haga clic en **agregar nueva ruta de acceso de dominio**.

     Un **ruta de acceso de dominio** nodo aparece en **nodos ocultos**.

3.  Seleccione **ruta de acceso de dominio**y, a continuación, en el **propiedades** ventana, haga clic en el campo de valor de **definición de ruta de acceso**. Seleccione **FlowGraph**, a continuación, **FlowGraphHasComments**. La ruta de acceso resultante debe ser similar a **FlowGraphHasComments.Comments**

4.  Transformar todas las plantillas y, a continuación, compilar y ejecutar la solución.

5.  En el diseñador generado, abra el diagrama de ejemplo.

     El explorador debería mostrar sólo una **actores** nodo y no debe mostrar el **comentarios** nodo.

## <a name="see-also"></a>Vea también

- [Glosario de las herramientas de lenguajes específicos de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)