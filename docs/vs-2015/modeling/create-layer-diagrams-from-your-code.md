---
title: Cree diagramas de capas a partir del código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 58c3ea71-2dbc-4963-bf82-40f1924cf973
caps.latest.revision: 64
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 138f818eab34b0b1860c7daa85f1b6814888fc9b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652845"
---
# <a name="create-layer-diagrams-from-your-code"></a>Crear diagramas de capas a partir del código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para visualizar la arquitectura lógica de alto nivel del sistema de software, cree un *Diagrama de capas* en Visual Studio. Para asegurarse de que el código mantiene la coherencia con este diseño, valide el código con un diagrama de capas. Se pueden crear diagramas de capas para proyectos de Visual C# .NET y Visual Basic .NET. Para ver qué versiones de Visual Studio admiten esta característica, vea [compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport) .

 ![Crear un diagrama de capas](../modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")

 Un diagrama de capas permite organizar los elementos de la solución de Visual Studio en grupos lógicos abstractos denominados *capas*. Las capas se pueden usar para describir las tareas principales que realizan estos artefactos o los componentes principales del sistema. Cada capa puede contener otras capas que describen tareas más detalladas. También puede especificar las *dependencias* planeadas o existentes entre las capas. Estas dependencias, que se representan como flechas, muestran qué capas pueden usar o usan actualmente la funcionalidad representada por otras capas. Para mantener el control de la arquitectura del código, muestre las dependencias previstas en el diagrama y, a continuación, valide el código con el diagrama.

## <a name="CreateDiagram"></a>Crear un diagrama de capas
 Antes de poder crear un diagrama de capas, asegúrese de que la solución tenga un proyecto de modelado. Vea [crear proyectos y diagramas de modelado UML](../modeling/create-uml-modeling-projects-and-diagrams.md).

> [!IMPORTANT]
> No agregue, arrastre ni copie un diagrama de capas de un proyecto de modelado a otro, ni a otro lugar de la solución. Esto conserva las referencias del diagrama original, aunque se cambie el diagrama. Esto también impide que la validación de capas se haga correctamente y es posible que cause otros problemas, como la pérdida de elementos u otros errores al intentar abrir el diagrama.
>
> En su lugar, agregue un nuevo diagrama de capas al proyecto de modelado. Copie los elementos del diagrama de origen en el nuevo diagrama. Guarde el proyecto de modelado y el nuevo diagrama de capas.

#### <a name="to-add-a-new-layer-diagram-to-a-modeling-project"></a>Para agregar un nuevo diagrama de capas a un proyecto de modelado

1. En el menú **arquitectura** , elija **nuevo diagrama de UML o de capas**.

2. En **plantillas**, elija **Diagrama de capas**.

3. Especifique un nombre para el diagrama.

4. En **Agregar a proyecto de modelado**, busque y seleccione un proyecto de modelado existente en la solución.

     o bien

     Elija **crear un nuevo proyecto de modelado** para agregar un nuevo proyecto de modelado a la solución.

    > [!NOTE]
    > Los diagramas de capas solo pueden existir dentro de un proyecto de modelado. Sin embargo, puede vincularlos a elementos en cualquier parte de la solución.

5. Asegúrese de guardar tanto el proyecto de modelado como el diagrama de capas.

## <a name="CreateLayers"></a>Crear capas a partir de artefactos
 Puede crear capas a partir de elementos de una solución de Visual Studio, como proyectos, archivos de código, espacios de nombres, clases y métodos. Esto crea automáticamente vínculos entre las capas y los elementos, que se incluyen en el proceso de validación de capas.

 También puede vincular capas a los elementos que no admiten validación, como documentos de Word o presentaciones de PowerPoint, para poder asociar una capa con especificaciones o planes. También puede vincular capas a archivos en proyectos que se comparten entre varias aplicaciones, pero el proceso de validación no incluirá esas capas, que aparecen con nombres genéricos como “Layer1" y “Layer2".

 Para ver si un elemento vinculado admite la validación, abra el **Explorador de capas** y examine la propiedad **Supports Validation** del elemento. Consulte [Administración de vínculos a artefactos](#Managing).

|**En**|**Siga estos pasos**|
|------------|----------------------------|
|Crear una capa para un único artefacto|<ol><li>Arrastre el elemento hasta el diagrama de capas desde estos orígenes:<br /><br /> <ul><li>**Explorador de soluciones**<br /><br />         Por ejemplo, puede arrastrar archivos o proyectos.</li><li>Mapas de código<br /><br />         Consulte [asignación de dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md) y [uso de mapas de código para depurar las aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Vista de clases** o **Examinador de objetos**</li></ul><br />     Aparecerá una capa en el diagrama que estará vinculada al artefacto.</li><li>Cambie el nombre de la capa para que refleje las responsabilidades del código asociado u otros artefactos.</li></ol> **Importante:**  Al arrastrar archivos binarios al diagrama de capas, no se agregan automáticamente sus referencias al proyecto de modelado. Debe agregar manualmente los archivos binarios que desee validar al proyecto de modelado. **Para agregar archivos binarios al proyecto de modelado** <ol><li>En **Explorador de soluciones**, abra el menú contextual del proyecto de modelado y, a continuación, elija **Agregar elemento existente**.</li><li>En el cuadro de diálogo **Agregar elemento existente** , vaya a los archivos binarios, selecciónelos y, a continuación, elija **Aceptar**.     Los archivos binarios aparecen en el proyecto de modelado.</li><li>En **Explorador de soluciones**, elija un archivo binario que haya agregado y, a continuación, presione **F4** para abrir la ventana **propiedades** .</li><li>En cada archivo binario, establezca la propiedad **acción de compilación** en **validar**.</li></ol>|
|Crear una única capa para todos los artefactos seleccionados|Arrastre todos los artefactos hasta el diagrama de capas al mismo tiempo.<br /><br /> Aparecerá una capa en el diagrama que estará vinculada a todos los artefactos.|
|Crear una capa para cada artefacto seleccionado|Mantenga presionada la tecla **MAYÚS** mientras arrastra todos los artefactos al diagrama de capas al mismo tiempo. **Nota:**  Si usa la tecla **MAYÚS** para seleccionar un intervalo de elementos, suelte la tecla después de seleccionar los artefactos. Cuando arrastre los artefactos al diagrama, vuelva a mantener la tecla presionada. <br /><br /> Aparecerá una capa para cada artefacto y cada capa estará vinculada a cada uno de los artefactos.|
|Agregar un artefacto a una capa|Arrastre el artefacto hasta la capa.|
|Crear una nueva capa que no tenga vínculos|En el **cuadro de herramientas**, expanda la sección **Diagrama de capas** y, a continuación, arrastre una **capa** al diagrama de capas.<br /><br /> Para agregar varias capas, haga doble clic en la herramienta. Cuando haya terminado, elija la herramienta **puntero** o presione la tecla **ESC** .<br /><br /> O bien<br /><br /> Abra el menú contextual del diagrama de capas, elija **Agregar**y, a continuación, elija **capa**.|
|Crear capas anidadas|Arrastre una capa existente a otro nivel.<br /><br /> O bien<br /><br /> Abra el menú contextual de una capa, elija **Agregar**y, a continuación, elija **capa**.|
|Crear una nueva capa que contenga dos o más capas existentes|Seleccione las capas, abra el menú contextual de la selección y, a continuación, elija **Grupo**.|
|Cambiar el color de una capa|Establezca su propiedad **color** en el color que desee.|
|Especificar qué artefactos asociados a una capa no deben pertenecer a los espacios de nombres especificados|Escriba los espacios de nombres en la propiedad **Forbidden namespaces** de la capa. Use un punto y coma ( **;** ) para separar los espacios de nombres.|
|Especificar qué artefactos asociados a una capa no pueden depender de los espacios de nombres especificados|Escriba los espacios de nombres en la propiedad **Forbidden namespace dependencies** de la capa. Use un punto y coma ( **;** ) para separar los espacios de nombres.|
|Especificar qué artefactos asociados a una capa no deben pertenecer a uno de los espacios de nombres especificados|Escriba el espacio de nombres en la propiedad **espacios de nombres necesarios** de la capa. Use un punto y coma ( **;** ) para separar los espacios de nombres.|

 El número de una capa indica el número de artefactos vinculados a ella. Sin embargo, cuando lea este número, recuerde lo siguiente:

- Si una capa se vincula a un artefacto que contiene otros artefactos, pero no se vincula directamente a estos otros artefactos, el número incluye únicamente el artefacto vinculado. Sin embargo, los demás artefactos se incluyen para el análisis durante la validación de capas.

     Por ejemplo, si una capa está vinculada a un solo espacio de nombres, el número de artefactos vinculados es 1, aunque el espacio de nombres contenga clases. Si la capa tiene también vínculos a cada clase del espacio de nombres, el número incluirá las clases vinculadas.

- Si una capa contiene otras que están vinculadas a artefactos, la capa contenedora también está vinculada a esos artefactos, incluso aunque el número de la capa contenedora no los incluya.

## <a name="Managing"></a>Administrar vínculos entre capas y artefactos

1. En el diagrama de capas, abra el menú contextual de la capa y, a continuación, elija **ver vínculos**.

     En el **Explorador de capas** se muestran los vínculos de artefacto para la capa seleccionada.

2. Use las tareas siguientes para administrar estos vínculos:

|**En**|**En el explorador de capas**|
|------------|---------------------------|
|Eliminar el vínculo entre la capa y un artefacto|Abra el menú contextual del vínculo del artefacto y, a continuación, elija **eliminar**.|
|Mover el vínculo de una capa a otra|Arrastre el vínculo del artefacto a una capa del diagrama.<br /><br /> O bien<br /><br /> 1. Abra el menú contextual del vínculo del artefacto y, a continuación, elija **cortar**.<br />2. en el diagrama de capas, abra el menú contextual de la capa y, a continuación, elija **pegar**.|
|Copiar el vínculo de una capa a otra|1. Abra el menú contextual del vínculo del artefacto y, a continuación, elija **copiar**.<br />2. en el diagrama de capas, abra el menú contextual de la capa y, a continuación, elija **pegar**.|
|Crear una nueva capa a partir del vínculo de un artefacto existente|Arrastre el vínculo del artefacto a un espacio en blanco del diagrama.|
|Compruebe que el artefacto vinculado admite la validación con el diagrama de capas.|Fíjese en la columna **admite validación** para el vínculo del artefacto.|

## <a name="Discovering"></a>Ingeniería inversa de las dependencias existentes
 Una dependencia existe cuando un artefacto que está asociado a una capa tiene una referencia a un artefacto que está asociado a otra capa. Por ejemplo, una clase de una capa declara una variable que tiene una clase en otra capa. Puede realizar ingeniería inversa de las dependencias existentes en los artefactos vinculados a las capas del diagrama.

> [!NOTE]
> No se puede realizar ingeniería inversa en las dependencias de ciertos tipos de artefactos. Por ejemplo, no se va a realizar ingeniería inversa en ninguna dependencia que tenga como origen o destino una capa vinculada a un archivo de texto. Para ver qué artefactos tienen dependencias a las que puede aplicar ingeniería inversa, abra el menú contextual de una o varias capas y, a continuación, elija **ver vínculos**. En el **Explorador de capas**, examine la columna **admite validación** . No se aplicará ingeniería inversa a las dependencias para los artefactos para los que esta columna muestra **false**.

- Seleccione una o varias capas, abra el menú contextual de una capa seleccionada y, a continuación, elija **generar dependencias**.

  Normalmente, verá algunas dependencias que no deberían existir. Puede editar estas dependencias para alinearlas con el diseño buscado.

## <a name="EditDependencies"></a>Editar capas y dependencias para mostrar el diseño previsto
 Para describir los cambios que piensa realizar en el sistema o la arquitectura deseada, edite el diagrama de capas:

|**En**|**Siga estos pasos**|
|------------|-----------------------------|
|Cambiar o restringir la dirección de una dependencia|Establezca su propiedad **Direction** .|
|Crear nuevas dependencias|Use las herramientas **de dependencia de dependencia y** **bidireccional** .<br /><br /> Para dibujar varias dependencias, haga doble clic en la herramienta. Cuando haya terminado, elija la herramienta **puntero** o presione la tecla **ESC** .|
|Especificar qué artefactos asociados a una capa no pueden depender de los espacios de nombres especificados|Escriba los espacios de nombres en la propiedad **Forbidden namespace dependencies** de la capa. Use un punto y coma ( **;** ) para separar los espacios de nombres.|
|Especificar qué artefactos asociados a una capa no deben pertenecer a los espacios de nombres especificados|Escriba los espacios de nombres en la propiedad **Forbidden namespaces** de la capa. Use un punto y coma ( **;** ) para separar los espacios de nombres.|
|Especificar qué artefactos asociados a una capa no deben pertenecer a uno de los espacios de nombres especificados|Escriba el espacio de nombres en la propiedad **espacios de nombres necesarios** de la capa. Use un punto y coma ( **;** ) para separar los espacios de nombres.|

## <a name="EditLayout"></a>Cambiar el modo en que aparecen los elementos en el diagrama
 Puede cambiar el tamaño, la forma, el color y la posición de las capas o el color de las dependencias mediante la edición de sus propiedades.

## <a name="Codemaps"></a>Detectar patrones y dependencias en un mapa de código
 Al crear diagramas de capas, también puede crear **mapas de código**. Estos diagramas pueden ayudarle a detectar patrones y dependencias mientras explora el código. Use el Explorador de soluciones, la Vista de clases o el Examinador de objetos para explorar los ensamblados, los espacios de nombres y las clases, que a menudo corresponden a las capas existentes. Para obtener más información sobre mapas de código, vea:

- [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)

- [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)

- [Buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="see-also"></a>Vea también
 [Vídeo de Channel 9: diseñar y validar la arquitectura mediante diagramas de](http://go.microsoft.com/fwlink/?LinkID=252073) capas [diagramas de capas: referencia](../modeling/layer-diagrams-reference.md) [diagramas de capas: instrucciones](../modeling/layer-diagrams-guidelines.md) [validar código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md) [visualizar código](../modeling/visualize-code.md)