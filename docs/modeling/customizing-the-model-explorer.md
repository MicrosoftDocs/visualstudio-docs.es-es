---
title: Personalizar el Explorador de modelos
description: Obtenga información acerca de cómo cambiar la apariencia y el comportamiento del explorador para el diseñador de lenguajes específicos de dominio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b3ae5ea3c24ea72c911f686c7a0a92191785d9d5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935383"
---
# <a name="customizing-the-model-explorer"></a>Personalizar el Explorador de modelos
Puede cambiar la apariencia y el comportamiento del explorador para el diseñador de lenguaje específico de dominio como se indica a continuación:

- Cambiar el título de la ventana.

- Cambiar el icono de la pestaña.

- Cambiar los iconos de los nodos.

- Ocultar nodos.

## <a name="changing-the-window-title"></a>Cambiar el título de la ventana
 Para cambiar el título de la ventana del explorador generado, seleccione **comportamiento del explorador** en **DSL Explorer** y, a continuación, en la ventana **propiedades** , establezca la propiedad **title** en el título que desee.

## <a name="changing-the-tab-icon"></a>Cambiar el icono de la pestaña
 Para cambiar el icono de la pestaña del explorador, use un icono de 16x16 píxeles en un archivo. bmp. Coloque el archivo de icono en la carpeta \DslPackage\Resources\ y, a continuación, cambie el nombre de archivo a **ModelExplorerToolWindowBitmaps.bmp**. Por ejemplo, puede cambiar el archivo de icono Setup. ico de Visual Studio al formato. bmp y cambiarle el nombre a **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**. El diseñador generado mostrará este icono en la pestaña del explorador cuando esté acoplado junto con **Explorador de soluciones**.

## <a name="setting-custom-icons-on-explorer-nodes"></a>Establecer iconos personalizados en nodos del explorador
 Puede personalizar los nodos del explorador mediante la configuración de nodo del explorador. En el procedimiento siguiente se muestra cómo agregar un icono a un nodo.

#### <a name="to-add-an-icon-to-an-explorer-node"></a>Para agregar un icono a un nodo del explorador

1. Cree una [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] solución mediante la plantilla de solución flujo de tareas.

2. Coloque un archivo. bmp que contenga un icono de 16x16 píxeles en la carpeta **Dsl\Resources** de la solución.

3. En el **Explorador de DSL**, haga clic con el botón secundario en **comportamiento del explorador** y haga clic en **Agregar nueva configuración de nodo del explorador**.

    Aparece un nodo **ExplorerNodeSettings** en el nodo **configuración de nodo personalizado** .

4. Seleccione **ExplorerNodeSettings** y, a continuación, en la ventana **propiedades** , establezca **clase** en **actor**.

5. Establezca el **icono para** que se muestre en la ruta de acceso del archivo de icono.

6. Transformar todas las plantillas y, a continuación, compilar y ejecutar la solución.

7. En el diseñador generado, abra el diagrama de ejemplo.

    El explorador debe mostrar tres nodos de **actor** que tengan el icono.

> [!NOTE]
> Si ha establecido un icono de nodo para cualquier elemento que se muestre en el explorador generado, todos los nodos del explorador mostrarán el icono. Si no se ha establecido ningún icono, los nodos mostrarán el icono predeterminado.

## <a name="changing-the-name-displayed-on-an-explorer-node"></a>Cambiar el nombre mostrado en un nodo del explorador
 Puede cambiar el modo en que se muestran los nombres de los elementos del modelo en el explorador. En el procedimiento siguiente se muestra cómo mostrar el nombre de la **tarea** a la que hace referencia un **Comentario** en el nodo de comentario.

#### <a name="to-display-a-property"></a>Para mostrar una propiedad

1. Abra la solución que creó en el procedimiento anterior.

2. Asegúrese de que el **Comentario** hace referencia a una sola clase de dominio estableciendo la multiplicidad del rol con el nombre de la propiedad **asuntos** en 0.. 1. El nombre de la propiedad debe ser **sujeto** y el nombre de la relación debe ser **CommentReferencesSubject**.

3. En el **Explorador de DSL**, haga clic con el botón secundario en **comportamiento del explorador** y haga clic en **Agregar nueva configuración de nodo del explorador**.

     Aparece un nodo **ExplorerNodeSettings** en el nodo **configuración de nodo personalizado** .

4. Seleccione **ExplorerNodeSettings** y, a continuación, en la ventana **propiedades** , establezca **clase** en **Comentario**.

5. Haga clic con el botón secundario en el nodo **Comentario** y, a continuación, haga clic en **Agregar nueva ruta de acceso de propiedad**.

     Aparece un nuevo nodo que se muestra con el nombre **propiedad**.

6. Seleccione la propiedad que se **muestra** y, a continuación, en la ventana **propiedades** , haga clic en el campo valor de **ruta de acceso a propiedad**. Seleccione **Comentario**, **CommentReferencesSubject** y **FlowElement**. La ruta de acceso resultante debe ser similar a **CommentReferencesSubject. Subject/! Asunto**.

7. En el campo valor de la **propiedad**, seleccione **nombre**.

8. Transformar todas las plantillas y, a continuación, compilar y ejecutar la solución.

9. En el diseñador generado, abra el diagrama de ejemplo.

10. Dibuje un **conector de comentario** entre el elemento comment y el elemento **Task1** en el diagrama.

     El nodo explorador debe mostrar el comentario como **Task1**.

## <a name="hiding-nodes"></a>Ocultar nodos
 Puede ocultar un nodo en el explorador agregando su ruta de acceso al nodo **nodos ocultos** del **Explorador de DSL**. En el procedimiento siguiente se muestra cómo ocultar los nodos de **Comentario** .

#### <a name="to-hide-an-explorer-node"></a>Para ocultar un nodo del explorador

1. Abra la solución que creó en el procedimiento anterior.

2. En el **Explorador de DSL**, haga clic con el botón secundario en **comportamiento del explorador** y haga clic en **Agregar nueva ruta de acceso de dominio**.

     Aparece un nodo de **ruta de acceso de dominio** bajo **nodos ocultos**.

3. Seleccione **ruta de acceso del dominio** y, a continuación, en la ventana **propiedades** , haga clic en el campo valor de la definición de la **ruta de acceso**. Seleccione **FlowGraph** y, después, **FlowGraphHasComments**. La ruta de acceso resultante debe ser similar a **FlowGraphHasComments. comments**

4. Transformar todas las plantillas y, a continuación, compilar y ejecutar la solución.

5. En el diseñador generado, abra el diagrama de ejemplo.

     El explorador debe mostrar solo un nodo **actores** y no debe mostrar el nodo **comentarios** .

## <a name="see-also"></a>Vea también

- [Glosario de las Herramientas del lenguaje específico de dominio](/previous-versions/bb126564(v=vs.100))