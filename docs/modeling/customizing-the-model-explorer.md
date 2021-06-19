---
title: Personalizar el Explorador de modelos
description: Obtenga información sobre cómo puede cambiar la apariencia y el comportamiento del explorador para el diseñador de lenguaje específico del dominio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c842988f3e5c9f1bbed5a859e73680cb109ecd43
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385908"
---
# <a name="customizing-the-model-explorer"></a>Personalizar el Explorador de modelos
Puede cambiar la apariencia y el comportamiento del explorador para el diseñador de lenguaje específico del dominio como se muestra a continuación:

- Cambie el título de la ventana.

- Cambie el icono de pestaña.

- Cambie los iconos de los nodos.

- Ocultar nodos.

## <a name="changing-the-window-title"></a>Cambiar el título de la ventana
 Para cambiar el título de la  ventana del explorador generado, seleccione  Comportamiento del explorador en el Explorador **DSL** y, a continuación, en la ventana Propiedades, establezca la propiedad **Título** en el título que desee.

## <a name="changing-the-tab-icon"></a>Cambiar el icono de pestaña
 Para cambiar el icono de pestaña del explorador, use un icono de 16 x 16 píxeles en un .bmp explorador. Coloque el archivo de icono en la carpeta \DslPackage\Resources\ y, a continuación, cambie el nombre de archivo **aModelExplorerToolWindowBitmaps.bmp**. Por ejemplo, puede cambiar el archivo de icono Visual Studio setup.ico a .bmp formato y cambiar su nombre a **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. El diseñador generado mostrará este icono en la pestaña del explorador cuando se acopla junto con **Explorador de soluciones**.

## <a name="setting-custom-icons-on-explorer-nodes"></a>Establecer iconos personalizados en nodos del Explorador
 Puede personalizar los nodos en el explorador mediante la configuración del nodo del explorador. El procedimiento siguiente muestra cómo agregar un icono a un nodo.

#### <a name="to-add-an-icon-to-an-explorer-node"></a>Para agregar un icono a un nodo del explorador

1. Cree una [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] solución mediante la plantilla de solución Flujo de tareas.

2. Coloque un .bmp que contenga un icono de 16 x 16 píxeles en la carpeta **Dsl\Resources** de la solución.

3. En el **Explorador de DSL, haga** clic con el botón derecho en Comportamiento del explorador **y,** a continuación, haga clic **en Agregar nueva configuración de nodo del explorador**.

    Aparece **un nodo ExplorerNodeSettings** en el **nodo Configuración de nodo** personalizado.

4. Seleccione **ExplorerNodeSettings** y, en la **ventana Propiedades,** establezca **Clase** en **Actor**.

5. Establezca **Icono para mostrar en** la ruta de acceso del archivo de icono.

6. Transforme todas las plantillas y, a continuación, compile y ejecute la solución.

7. En el diseñador generado, abra el diagrama de ejemplo.

    El Explorador debe mostrar tres **nodos actores** que tengan el icono.

> [!NOTE]
> Si ha establecido un icono de nodo para cualquier elemento que se muestre en el explorador generado, todos los nodos del explorador mostrarán el icono. Si no se ha establecido ningún icono, los nodos mostrarán el icono predeterminado.

## <a name="changing-the-name-displayed-on-an-explorer-node"></a>Cambiar el nombre mostrado en un nodo del explorador
 Puede cambiar cómo se muestran los nombres de los elementos del modelo en el explorador. En el procedimiento siguiente se muestra cómo mostrar el nombre de la **tarea** a la que hace referencia un **comentario** en el nodo de comentario.

#### <a name="to-display-a-property"></a>Para mostrar una propiedad

1. Abra la solución que creó en el procedimiento anterior.

2. Asegúrese de que **comment hace** referencia solo a una sola clase de dominio estableciendo la multiplicidad del rol con el nombre de propiedad **Subjects** en 0..1. El nombre de propiedad debe convertirse **en Asunto** y el nombre de la relación debe convertirse **en CommentReferencesSubject**.

3. En el **Explorador de DSL, haga** clic con el botón derecho en Comportamiento del explorador **y,** a continuación, haga clic **en Agregar nueva configuración de nodo del explorador**.

     Aparece **un nodo ExplorerNodeSettings** en el **nodo Configuración de nodo** personalizado.

4. Seleccione **ExplorerNodeSettings** y, a continuación, en la **ventana Propiedades,** **establezca Clase** en **Comentario**.

5. Haga clic con el botón derecho **en el nodo** Comentario y, a continuación, haga clic en Agregar nueva ruta de acceso de **propiedad**.

     Aparece un nuevo nodo denominado **Propiedad mostrada.**

6. Seleccione **Propiedad mostrada y,** a continuación, en la **ventana Propiedades,** haga clic en el campo de valor **de Ruta de acceso a la propiedad**. Seleccione **Comentario** y, **a continuación, CommentReferencesSubject** y, a **continuación, FlowElement.** La ruta de acceso resultante debe ser **similar a CommentReferencesSubject.Subject/! Asunto**.

7. En el campo de valor de **Propiedad**, seleccione **Nombre.**

8. Transforme todas las plantillas y, a continuación, compile y ejecute la solución.

9. En el diseñador generado, abra el diagrama de ejemplo.

10. Dibuje **un conector de** comentario entre el elemento comment y el elemento **Task1** del diagrama.

     El nodo Explorador debe mostrar el comentario como **Tarea1.**

## <a name="hiding-nodes"></a>Ocultar nodos
 Puede ocultar un nodo en el explorador agregando su ruta de acceso al nodo **Nodos ocultos** del Explorador **de DSL.** En el procedimiento siguiente se muestra cómo ocultar nodos **Comment.**

#### <a name="to-hide-an-explorer-node"></a>Para ocultar un nodo del explorador

1. Abra la solución que creó en el procedimiento anterior.

2. En el Explorador **de DSL, haga** clic con el botón derecho **en Comportamiento del explorador y,** a continuación, haga clic **en Agregar nueva ruta de acceso de dominio.**

     Aparece **un nodo Ruta de** acceso de dominio en Nodos **ocultos.**

3. Seleccione **Ruta de acceso del** dominio y, a continuación, en la ventana **Propiedades,** haga clic en el campo de valor de **Definición de ruta de acceso**. Seleccione **FlowGraph** y, a **continuación, FlowGraphHasComments**. La ruta de acceso resultante debe ser **similar a FlowGraphHasComments.Comments**

4. Transforme todas las plantillas y, a continuación, compile y ejecute la solución.

5. En el diseñador generado, abra el diagrama de ejemplo.

     El explorador solo debe mostrar un **nodo Actores** y no debe mostrar el **nodo Comentarios.**

## <a name="see-also"></a>Vea también

- [Glosario de las Herramientas del lenguaje específico de dominio](/previous-versions/bb126564(v=vs.100))