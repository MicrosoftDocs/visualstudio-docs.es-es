---
title: Crear diagramas de dependencia a partir del código
description: Aprenda a crear un diagrama de dependencias en Visual Studio visualizar la arquitectura lógica de alto nivel del sistema de software.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b07af93386d5062f28f19f01ce150fba8ec45dd2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389662"
---
# <a name="create-dependency-diagrams-from-your-code"></a>Crear diagramas de dependencia a partir del código

Para visualizar la arquitectura lógica de alto nivel del sistema de software, cree un diagrama *de dependencias* en Visual Studio. Para asegurarse de que el código sigue siendo coherente con este diseño, valide el código con un diagrama de dependencias. Puede crear diagramas de dependencias para Visual C# y Visual Basic proyecto. Para ver qué ediciones de Visual Studio admiten esta característica, consulte [Compatibilidad de ediciones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#edition-support-for-architecture-and-modeling-tools).

![Creación de un diagrama de dependencias](../modeling/media/layerdiagramvisualizecode.png)

Un diagrama de dependencias le permite organizar los Visual Studio de la solución en grupos lógicos y abstractos *denominados capas*. Las capas se pueden usar para describir las tareas principales que realizan estos artefactos o los componentes principales del sistema. Cada capa puede contener otras capas que describen tareas más detalladas. También puede especificar las dependencias previstas o *existentes entre* capas. Estas dependencias, que se representan como flechas, muestran qué capas pueden usar o usan actualmente la funcionalidad representada por otras capas. Para mantener el control de la arquitectura del código, muestre las dependencias previstas en el diagrama y, a continuación, valide el código con el diagrama.

[Vídeo: Validación de las dependencias de la arquitectura en tiempo real](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)

## <a name="create-a-dependency-diagram"></a><a name="CreateDiagram"></a> Creación de un diagrama de dependencias

Antes de crear un diagrama de dependencias, asegúrese de que la solución tiene un proyecto de modelado.

> [!IMPORTANT]
> No agregue, arrastre ni copie un diagrama de dependencias existente de un proyecto de modelado a otro proyecto de modelado ni a otro lugar de la solución. Esto conserva las referencias del diagrama original, aunque se cambie el diagrama. Esto también impide que la validación de capas se haga correctamente y es posible que cause otros problemas, como la pérdida de elementos u otros errores al intentar abrir el diagrama.
>
> En su lugar, agregue un nuevo diagrama de dependencias al proyecto de modelado. Copie los elementos del diagrama de origen en el nuevo diagrama. Guarde el proyecto de modelado y el nuevo diagrama de dependencias.

### <a name="add-a-new-dependency-diagram-to-a-modeling-project"></a>Agregar un nuevo diagrama de dependencias a un proyecto de modelado

> [!NOTE]
> Los diagramas de dependencias para proyectos de .NET Core se admiten a partir Visual Studio versión 16.2 de 2019.

1. En el **menú Arquitectura,** elija **Nuevo diagrama de dependencias.**

2. En **Plantillas,** elija diagrama **de dependencias.**

3. Especifique un nombre para el diagrama.

4. En **Agregar al proyecto de modelado**, busque y seleccione un proyecto de modelado existente en la solución.

     O bien

     Elija **Crear un nuevo proyecto de modelado** para agregar un nuevo proyecto de modelado a la solución.

    > [!NOTE]
    > El diagrama de dependencias debe existir dentro de un proyecto de modelado. Sin embargo, puede vincularlos a elementos en cualquier parte de la solución.

5. Asegúrese de guardar el proyecto de modelado y el diagrama de dependencias.

## <a name="drag-and-drop-or-copy-and-paste-from-a-code-map"></a>Arrastrar y colocar, o copiar y pegar, desde un mapa de código

1. Genere un mapa de código para la solución mediante el **menú** Arquitectura.

2. Considere la posibilidad de aplicar un filtro de mapa de código para quitar carpetas de soluciones y "Recursos de prueba" si solo desea aplicar dependencias en el código de producto.

3. En el mapa de código generado, quite el nodo "Externo" o expándalo para mostrar ensamblados externos, en función de si desea aplicar dependencias de espacio de nombres y eliminar los ensamblados no necesarios del mapa de código.

4. Crear un nuevo diagrama de dependencias para la solución mediante el **menú Arquitectura**

5. Seleccione todos los nodos del mapa de código (use _Ctrl_ A o use la selección de banda elástica presionando la tecla Mayús antes de hacer clic, arrastrar  +  y liberar). 

6. Arrastre y coloque, o copiar y pegar, los elementos seleccionados en el nuevo diagrama de validación de dependencias.

7. Esto muestra la arquitectura de la aplicación actual. Decida cuál desea que sea la arquitectura y modifique el diagrama de dependencias en consecuencia.

![Diagrama de dependencias generado a partir de un mapa de código](media/dependency-validation-01.png)

## <a name="create-layers-from-artifacts"></a><a name="CreateLayers"></a> Creación de capas a partir de artefactos
 Puede crear capas a partir de elementos de una solución de Visual Studio, como proyectos, archivos de código, espacios de nombres, clases y métodos. Esto crea automáticamente vínculos entre las capas y los elementos, que se incluyen en el proceso de validación de capas.

 También puede vincular capas a los elementos que no admiten validación, como documentos de Word o presentaciones de PowerPoint, para poder asociar una capa con especificaciones o planes. También puede vincular capas a archivos en proyectos que se comparten entre varias aplicaciones, pero el proceso de validación no incluirá esas capas, que aparecen con nombres genéricos como “Layer1" y “Layer2".

 Para ver si un elemento vinculado admite la validación, abra **el Explorador de capas** y examine la propiedad Supports **Validation** del elemento. Consulte [Administración de vínculos a artefactos.](#Managing)

|**To**|**Siga estos pasos**:|
|-|-|
|Crear una capa para un único artefacto|<ol><li>Arrastre el elemento al diagrama de dependencias desde estos orígenes:<br /><br /> <ul><li>**Explorador de soluciones**<br /><br />         Por ejemplo, puede arrastrar archivos o proyectos.</li><li>Mapas de código<br /><br />         Consulte [Asignación de dependencias en las soluciones y](../modeling/map-dependencies-across-your-solutions.md) Uso de mapas de código para depurar las [aplicaciones.](../modeling/use-code-maps-to-debug-your-applications.md)</li><li>**Vista de clases** o explorador **de objetos**</li></ul><br />     Aparecerá una capa en el diagrama que estará vinculada al artefacto.</li><li>Cambie el nombre de la capa para que refleje las responsabilidades del código asociado u otros artefactos.</li></ol> **Importante:**  Arrastrar archivos binarios al diagrama de dependencias no agrega automáticamente sus referencias al proyecto de modelado. Debe agregar manualmente los archivos binarios que desee validar al proyecto de modelado. **Para agregar archivos binarios al proyecto de modelado** <ol><li>En **Explorador de soluciones**, abra el menú contextual del proyecto de modelado y, a continuación, **elija Agregar elemento existente.**</li><li>En el **cuadro de diálogo Agregar** elemento existente , vaya a los archivos binarios, selecciónelos y, a continuación, elija **Aceptar.**     Los archivos binarios aparecen en el proyecto de modelado.</li><li>En **Explorador de soluciones**, elija un archivo binario que agregó y, a continuación, **presione F4** para abrir la **ventana** Propiedades.</li><li>En cada archivo binario, establezca la propiedad **Acción de** compilación en **Validar**.</li></ol>|
|Crear una única capa para todos los artefactos seleccionados|Arrastre todos los artefactos al diagrama de dependencias al mismo tiempo.<br /><br /> Aparecerá una capa en el diagrama que estará vinculada a todos los artefactos.|
|Crear una capa para cada artefacto seleccionado|Mantenga presionada la **tecla MAYÚS** mientras arrastra todos los artefactos al diagrama de dependencias al mismo tiempo. **Nota:**  Si usa la tecla **MAYÚS para** seleccionar un intervalo de elementos, suelte la clave después de seleccionar los artefactos. Cuando arrastre los artefactos al diagrama, vuelva a mantener la tecla presionada. <br /><br /> Aparecerá una capa para cada artefacto y cada capa estará vinculada a cada uno de los artefactos.|
|Agregar un artefacto a una capa|Arrastre el artefacto hasta la capa.|
|Crear una nueva capa que no tenga vínculos|En el **cuadro de herramientas**, expanda la sección Diagrama **de** dependencias y, a continuación, arrastre una **capa** al diagrama de dependencias.<br /><br /> Para agregar varias capas, haga doble clic en la herramienta. Cuando haya terminado, elija la herramienta **Puntero** o presione la **tecla ESC.**<br /><br /> o bien<br /><br /> Abra el menú contextual del diagrama de dependencias, **elija Agregar** y, a continuación, **elija Capa.**|
|Crear capas anidadas|Arrastre una capa existente a otro nivel.<br /><br /> o bien<br /><br /> Abra el menú contextual de una capa, **elija Agregar** y, a continuación, **elija Capa.**|
|Crear una nueva capa que contenga dos o más capas existentes|Seleccione las capas, abra el menú contextual de la selección y, a continuación, elija **Agrupar.**|
|Cambiar el color de una capa|Establezca su **propiedad Color** en el color que desee.|
|Especificar qué artefactos asociados a una capa no deben pertenecer a los espacios de nombres especificados|Escriba los espacios de nombres en la propiedad Espacios de nombres **prohibidos de la** capa. Use un punto y coma (**;**) para separar los espacios de nombres.|
|Especificar qué artefactos asociados a una capa no pueden depender de los espacios de nombres especificados|Escriba los espacios de nombres en la propiedad **Dependencias** de espacio de nombres prohibido de la capa. Use un punto y coma (**;**) para separar los espacios de nombres.|
|Especificar qué artefactos asociados a una capa no deben pertenecer a uno de los espacios de nombres especificados|Escriba el espacio de nombres en la propiedad **Espacios de nombres necesarios de la** capa. Use un punto y coma (**;**) para separar los espacios de nombres.|

 El número de una capa indica el número de artefactos vinculados a ella. Sin embargo, cuando lea este número, recuerde lo siguiente:

- Si una capa se vincula a un artefacto que contiene otros artefactos, pero no se vincula directamente a estos otros artefactos, el número incluye únicamente el artefacto vinculado. Sin embargo, los demás artefactos se incluyen para el análisis durante la validación de capas.

     Por ejemplo, si una capa está vinculada a un solo espacio de nombres, el número de artefactos vinculados es 1, aunque el espacio de nombres contenga clases. Si la capa tiene también vínculos a cada clase del espacio de nombres, el número incluirá las clases vinculadas.

- Si una capa contiene otras que están vinculadas a artefactos, la capa contenedora también está vinculada a esos artefactos, incluso aunque el número de la capa contenedora no los incluya.

## <a name="manage-links-between-layers-and-artifacts"></a><a name="Managing"></a> Administración de vínculos entre capas y artefactos

1. En el diagrama de dependencias, abra el menú contextual de la capa y elija **Ver vínculos.**

     **El Explorador de capas** muestra los vínculos de artefacto para la capa seleccionada.

2. Use las tareas siguientes para administrar estos vínculos:

|**To**|**En el Explorador de capas**|
|-|-|
|Eliminar el vínculo entre la capa y un artefacto|Abra el menú contextual del vínculo del artefacto y, a continuación, elija **Eliminar.**|
|Mover el vínculo de una capa a otra|Arrastre el vínculo del artefacto a una capa del diagrama.<br /><br /> o bien<br /><br /> 1. Abra el menú contextual del vínculo del artefacto y, a continuación, elija **Cortar.**<br />2. En el diagrama de dependencias, abra el menú contextual de la capa y, a continuación, **elija Pegar.**|
|Copiar el vínculo de una capa a otra|1. Abra el menú contextual del vínculo del artefacto y, a continuación, elija **Copiar.**<br />2. En el diagrama de dependencias, abra el menú contextual de la capa y, a continuación, **elija Pegar.**|
|Crear una nueva capa a partir del vínculo de un artefacto existente|Arrastre el vínculo del artefacto a un espacio en blanco del diagrama.|
|Compruebe que un artefacto vinculado admite la validación en el diagrama de dependencias.|Vea la columna **Supports Validation (Admite** validación) para el vínculo del artefacto.|

## <a name="reverse-engineer-existing-dependencies"></a><a name="Discovering"></a> Ingeniería inversa de dependencias existentes
 Una dependencia existe cuando un artefacto que está asociado a una capa tiene una referencia a un artefacto que está asociado a otra capa. Por ejemplo, una clase de una capa declara una variable que tiene una clase en otra capa. Puede realizar ingeniería inversa de las dependencias existentes en los artefactos vinculados a las capas del diagrama.

> [!NOTE]
> No se puede realizar ingeniería inversa en las dependencias de ciertos tipos de artefactos. Por ejemplo, no se va a realizar ingeniería inversa en ninguna dependencia que tenga como origen o destino una capa vinculada a un archivo de texto. Para ver qué artefactos tienen dependencias que se pueden realizar con ingeniería inversa, abra el menú contextual de una o varias capas y, a continuación, elija **Ver vínculos.** En **el Explorador de capas,** examine la columna **Admite** validación. Las dependencias no se diseñarán inversamente para los artefactos para los que esta columna muestra **False**.

- Seleccione una o varias capas, abra el menú contextual de una capa seleccionada y elija **Generar dependencias.**

  Normalmente, verá algunas dependencias que no deberían existir. Puede editar estas dependencias para alinearlas con el diseño buscado.

## <a name="edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditDependencies"></a> Editar capas y dependencias para mostrar el diseño previsto
 Para describir los cambios que planea realizar en el sistema o en la arquitectura prevista, edite el diagrama de dependencias:

|**To**|**Siga estos pasos**|
|-|-|
|Cambiar o restringir la dirección de una dependencia|Establezca su **propiedad Direction.**|
|Crear nuevas dependencias|Use las **herramientas Dependencia** y **Dependencia bidireccional.**<br /><br /> Para dibujar varias dependencias, haga doble clic en la herramienta. Cuando haya terminado, elija la herramienta **Puntero** o presione la **tecla ESC.**|
|Especificar qué artefactos asociados a una capa no pueden depender de los espacios de nombres especificados|Escriba los espacios de nombres en la propiedad **Dependencias** de espacio de nombres prohibido de la capa. Use un punto y coma (**;**) para separar los espacios de nombres.|
|Especificar qué artefactos asociados a una capa no deben pertenecer a los espacios de nombres especificados|Escriba los espacios de nombres en la propiedad Espacios de nombres **prohibidos de la** capa. Use un punto y coma (**;**) para separar los espacios de nombres.|
|Especificar qué artefactos asociados a una capa no deben pertenecer a uno de los espacios de nombres especificados|Escriba el espacio de nombres en la propiedad **Espacios de nombres necesarios de la** capa. Use un punto y coma (**;**) para separar los espacios de nombres.|

## <a name="change-how-elements-appear-on-the-diagram"></a><a name="EditLayout"></a> Cambiar cómo aparecen los elementos en el diagrama
 Puede cambiar el tamaño, la forma, el color y la posición de las capas o el color de las dependencias mediante la edición de sus propiedades.

## <a name="discover-patterns-and-dependencies-on-a-code-map"></a><a name="Codemaps"></a> Detectar patrones y dependencias en un mapa de código
 Al crear diagramas de dependencias, también puede crear mapas **de código**. Estos diagramas pueden ayudarle a detectar patrones y dependencias mientras explora el código. Use el Explorador de soluciones, la Vista de clases o el Examinador de objetos para explorar los ensamblados, los espacios de nombres y las clases, que a menudo corresponden a las capas existentes. Para obtener más información sobre mapas de código, vea:

- [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)

- [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)

- [Buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="see-also"></a>Vea también

- [Compatibilidad de edición con herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#edition-support-for-architecture-and-modeling-tools)
- [Vídeo: Validación de las dependencias de la arquitectura en tiempo real](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
- [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)
- [Diagramas de dependencia: instrucciones](../modeling/layer-diagrams-guidelines.md)
- [Validación código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)
- [Visualizar el código](../modeling/visualize-code.md)
