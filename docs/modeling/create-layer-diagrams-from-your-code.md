---
title: Crear diagramas de dependencia desde el código | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 9acc63c676463743ad598736f1d095f0ced0b388
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="create-dependency-diagrams-from-your-code"></a>Crear diagramas de dependencia desde el código

Para visualizar la arquitectura de alto nivel, lógica de su sistema de software, cree un *diagrama de dependencia* en Visual Studio. Para asegurarse de que el código sigue siendo coherente con este diseño, valide el código con un diagrama de dependencia. Puede crear diagramas de dependencia para los proyectos de Visual C# y Visual Basic. Para ver qué versiones de Visual Studio admiten esta característica, vea [Compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

![Crear un diagrama de dependencia](../modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")

Un diagrama de dependencia le permite organizar los elementos de la solución de Visual Studio en grupos lógicos y abstractos denominados *capas*. Las capas se pueden usar para describir las tareas principales que realizan estos artefactos o los componentes principales del sistema. Cada capa puede contener otras capas que describen tareas más detalladas. También puede especificar planeadas o existentes *dependencias* entre las capas. Estas dependencias, que se representan como flechas, muestran qué capas pueden usar o usan actualmente la funcionalidad representada por otras capas. Para mantener el control de la arquitectura del código, muestre las dependencias previstas en el diagrama y, a continuación, valide el código con el diagrama.

[Vídeo: Validar las dependencias de arquitectura en tiempo real](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4) 

##  <a name="CreateDiagram"></a> Crear un diagrama de dependencia

Antes de crear un diagrama de dependencia, asegúrese de que la solución tiene un proyecto de modelado.

> [!IMPORTANT]
> No agregue, arrastre o copie un diagrama de dependencia existente de un proyecto de modelado a otro proyecto de modelado o en otro lugar de la solución. Esto conserva las referencias del diagrama original, aunque se cambie el diagrama. Esto también impide que la validación de capas se haga correctamente y es posible que cause otros problemas, como la pérdida de elementos u otros errores al intentar abrir el diagrama.
>
> En su lugar, agregue un nuevo diagrama de dependencia para el proyecto de modelado. Copie los elementos del diagrama de origen en el nuevo diagrama. Guarde el proyecto de modelado y el nuevo diagrama de dependencia.

#### <a name="to-add-a-new-dependency-diagram-to-a-modeling-project"></a>Para agregar un nuevo diagrama de dependencia a un proyecto de modelado  
  
1.  En el **arquitectura** menú, elija **nuevo diagrama de dependencia**.  
  
2.  En **plantillas**, elija **diagrama de dependencia**.  
  
3.  Especifique un nombre para el diagrama.  
  
4.  En **agregar a proyecto de modelado**, busque y seleccione un proyecto de modelado existente de la solución.  
  
     -o bien-  
  
     Elija **crear un nuevo proyecto de modelado** para agregar un nuevo proyecto de modelado a la solución.  
  
    > [!NOTE]
    >  El diagrama de dependencia debe existir dentro de un proyecto de modelado. Sin embargo, puede vincularlos a elementos en cualquier parte de la solución.  
  
5.  Asegúrese de que desea guardar el proyecto de modelado y el diagrama de dependencia.  

## <a name="drag-and-drop-or-copy-and-paste-from-a-code-map"></a>Arrastrar y colocar, o copiar y pegar, desde un mapa de código

1. Generar un mapa de código para la solución mediante la **arquitectura** menú. 

2. Considere la posibilidad de aplicar un filtro de mapa de código para quitar las carpetas de soluciones y "Prueba activos" Si desea aplicar las dependencias del código de producto.

3. En el mapa de código generado, quite el nodo "Externo", o expandir para mostrar los ensamblados externos, dependiendo de si desea aplicar las dependencias de espacio de nombres y eliminar ensamblados no sean necesarios desde el mapa de código. 

4. Cree un nuevo diagrama de dependencia para la solución mediante la **arquitectura** menú

5. Seleccionar todos los nodos del mapa de código (usar _Ctrl_ + _A_, o use la herramienta de selección de goma presionando el _MAYÚS_ antes de que haga clic en, arrastre y suelte la clave.

6. Arrastrar y colocar, o un copiar y pegar, los elementos seleccionados en el nuevo diagrama de validación de la dependencia. 

7. Esto muestra la arquitectura de aplicación actual. Decidir la acción que realizará la arquitectura sea y modificar el diagrama de dependencia en consecuencia.

![Diagrama de dependencias generado a partir de un mapa de código](media/dependency-validation-01.png)
  
##  <a name="CreateLayers"></a> Crear capas a partir de artefactos  
 Puede crear capas a partir de elementos de una solución de Visual Studio, como proyectos, archivos de código, espacios de nombres, clases y métodos. Esto crea automáticamente vínculos entre las capas y los elementos, que se incluyen en el proceso de validación de capas.  
  
 También puede vincular capas a los elementos que no admiten validación, como documentos de Word o presentaciones de PowerPoint, para poder asociar una capa con especificaciones o planes. También puede vincular capas a archivos en proyectos que se comparten entre varias aplicaciones, pero el proceso de validación no incluirá esas capas, que aparecen con nombres genéricos como “Layer1" y “Layer2".  
  
 Para ver si un elemento vinculado admite la validación, abra **Explorador de capas** y examine el **Supports Validation** propiedad del elemento. Vea [administrar vínculos a artefactos](#Managing).  
  
|**En**|**Siga estos pasos**|  
|------------|----------------------------|  
|Crear una capa para un único artefacto|<ol><li>Arrastre el elemento al diagrama de dependencia de estos orígenes:<br /><br /> <ul><li>**Explorador de soluciones**<br /><br />         Por ejemplo, puede arrastrar archivos o proyectos.</li><li>Mapas de código<br /><br />         Vea [asignar dependencias en sus soluciones](../modeling/map-dependencies-across-your-solutions.md) y [usar mapas de código para depurar las aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Vista de clases** o **Examinador de objetos**</li></ul><br />     Aparecerá una capa en el diagrama que estará vinculada al artefacto.</li><li>Cambie el nombre de la capa para que refleje las responsabilidades del código asociado u otros artefactos.</li></ol> **Importante:** arrastrar archivos binarios al diagrama de dependencia no agrega automáticamente sus referencias al proyecto de modelado. Debe agregar manualmente los archivos binarios que desee validar al proyecto de modelado. **Para agregar archivos binarios para el proyecto de modelado** <ol><li>En **el Explorador de soluciones**, abra el menú contextual del proyecto de modelado y, a continuación, elija **Agregar elemento existente**.</li><li>En el **Agregar elemento existente** cuadro de diálogo, busque los archivos binarios, selecciónelos y, a continuación, elija **Aceptar**.     Los archivos binarios aparecen en el proyecto de modelado.</li><li>En **el Explorador de soluciones**, elija un archivo binario que ha agregado y, a continuación, presione **F4** para abrir el **propiedades** ventana.</li><li>En cada archivo binario, establezca el **acción de compilación** propiedad **validar**.</li></ol>|  
|Crear una única capa para todos los artefactos seleccionados|Arrastre todos los artefactos al diagrama de dependencia al mismo tiempo.<br /><br /> Aparecerá una capa en el diagrama que estará vinculada a todos los artefactos.|  
|Crear una capa para cada artefacto seleccionado|Presione y mantenga presionado el **MAYÚS** mientras arrastra al mismo tiempo todos los artefactos al diagrama de dependencia de clave. **Nota:** si usas el **MAYÚS** clave para seleccionar un intervalo de elementos, suelte la tecla después de seleccionar los artefactos. Cuando arrastre los artefactos al diagrama, vuelva a mantener la tecla presionada. <br /><br /> Aparecerá una capa para cada artefacto y cada capa estará vinculada a cada uno de los artefactos.|  
|Agregar un artefacto a una capa|Arrastre el artefacto hasta la capa.|  
|Crear una nueva capa que no tenga vínculos|En el **cuadro de herramientas**, expanda la **diagrama de dependencia** sección y, a continuación, arrastre un **capa** hasta el diagrama de dependencia.<br /><br /> Para agregar varias capas, haga doble clic en la herramienta. Cuando haya terminado, elija la **puntero** herramienta o presione la **ESC** clave.<br /><br /> O bien<br /><br /> Abra el menú contextual para el diagrama de dependencia, elija **agregar**y, a continuación, elija **capa**.|  
|Crear capas anidadas|Arrastre una capa existente a otro nivel.<br /><br /> O bien<br /><br /> Abra el menú contextual de una capa, elija **agregar**y, a continuación, elija **capa**.|  
|Crear una nueva capa que contenga dos o más capas existentes|Seleccione las capas, abra el menú contextual para la selección y, a continuación, elija **grupo**.|  
|Cambiar el color de una capa|Establecer su **Color** propiedad para el color que desee.|  
|Especificar qué artefactos asociados a una capa no deben pertenecer a los espacios de nombres especificados|Escriba los espacios de nombres en la capa **Forbidden Namespaces** propiedad. Use un punto y coma (**;**) para separar los espacios de nombres.|  
|Especificar qué artefactos asociados a una capa no pueden depender de los espacios de nombres especificados|Escriba los espacios de nombres en la capa **Forbidden Namespace Dependencies** propiedad. Use un punto y coma (**;**) para separar los espacios de nombres.|  
|Especificar qué artefactos asociados a una capa no deben pertenecer a uno de los espacios de nombres especificados|Escriba el espacio de nombres en la capa **Required Namespaces** propiedad. Use un punto y coma (**;**) para separar los espacios de nombres.|  
  
 El número de una capa indica el número de artefactos vinculados a ella. Sin embargo, cuando lea este número, recuerde lo siguiente:  
  
-   Si una capa se vincula a un artefacto que contiene otros artefactos, pero no se vincula directamente a estos otros artefactos, el número incluye únicamente el artefacto vinculado. Sin embargo, los demás artefactos se incluyen para el análisis durante la validación de capas.  
  
     Por ejemplo, si una capa está vinculada a un solo espacio de nombres, el número de artefactos vinculados es 1, aunque el espacio de nombres contenga clases. Si la capa tiene también vínculos a cada clase del espacio de nombres, el número incluirá las clases vinculadas.  
  
-   Si una capa contiene otras que están vinculadas a artefactos, la capa contenedora también está vinculada a esos artefactos, incluso aunque el número de la capa contenedora no los incluya.  
  
##  <a name="Managing"></a> Administrar vínculos entre capas y artefactos  
  
1.  En el diagrama de dependencia, abra el menú contextual de la capa y, a continuación, elija **ver vínculos**.  
  
     **Explorador de capas** muestra los vínculos de artefacto de la capa seleccionada.  
  
2.  Use las tareas siguientes para administrar estos vínculos:  
  
|**En**|**En el Explorador de capas**|  
|------------|---------------------------|  
|Eliminar el vínculo entre la capa y un artefacto|Abra el menú contextual para el vínculo del artefacto y, a continuación, elija **eliminar**.|  
|Mover el vínculo de una capa a otra|Arrastre el vínculo del artefacto a una capa del diagrama.<br /><br /> O bien<br /><br /> 1.  Abra el menú contextual para el vínculo del artefacto y, a continuación, elija **cortar**.<br />2.  En el diagrama de dependencia, abra el menú contextual de la capa y, a continuación, elija **pegar**.|  
|Copiar el vínculo de una capa a otra|1.  Abra el menú contextual para el vínculo del artefacto y, a continuación, elija **copia**.<br />2.  En el diagrama de dependencia, abra el menú contextual de la capa y, a continuación, elija **pegar**.|  
|Crear una nueva capa a partir del vínculo de un artefacto existente|Arrastre el vínculo del artefacto a un espacio en blanco del diagrama.|  
|Compruebe que el artefacto vinculado admite la validación con el diagrama de dependencia.|Mire el **admite validación** columna para el vínculo del artefacto.|  
  
##  <a name="Discovering"></a> Técnicas de ingeniería inversa de las dependencias existentes  
 Una dependencia existe cuando un artefacto que está asociado a una capa tiene una referencia a un artefacto que está asociado a otra capa. Por ejemplo, una clase de una capa declara una variable que tiene una clase en otra capa. Puede realizar ingeniería inversa de las dependencias existentes en los artefactos vinculados a las capas del diagrama.  
  
> [!NOTE]
>  No se puede realizar ingeniería inversa en las dependencias de ciertos tipos de artefactos. Por ejemplo, no se va a realizar ingeniería inversa en ninguna dependencia que tenga como origen o destino una capa vinculada a un archivo de texto. Para ver qué artefactos tienen dependencias en las que puede realizar ingeniería inversa, abra el menú contextual para una o varias capas y, a continuación, elija **ver vínculos**. En **Explorador de capas**, examine la **admite validación** columna. Dependencias no se pueden realizar ingeniería inversa de artefactos para el que se muestra esta columna **False**.  
  
-   Seleccione una o varias capas, abra el menú contextual de una capa seleccionada y, a continuación, elija **generar dependencias**.  
  
 Normalmente, verá algunas dependencias que no deberían existir. Puede editar estas dependencias para alinearlas con el diseño buscado.  
  
##  <a name="EditDependencies"></a> Editar capas y dependencias para mostrar el diseño previsto  
 Para describir los cambios que va a realizar en el sistema o la arquitectura deseada, edite el diagrama de dependencia:  
  
|**En**|**Siga estos pasos**|  
|------------|-----------------------------|  
|Cambiar o restringir la dirección de una dependencia|Establecer su **dirección** propiedad.|  
|Crear nuevas dependencias|Use la **dependencia** y **dependencia bidireccional** herramientas.<br /><br /> Para dibujar varias dependencias, haga doble clic en la herramienta. Cuando haya terminado, elija la **puntero** herramienta o presione la **ESC** clave.|  
|Especificar qué artefactos asociados a una capa no pueden depender de los espacios de nombres especificados|Escriba los espacios de nombres en la capa **Forbidden Namespace Dependencies** propiedad. Use un punto y coma (**;**) para separar los espacios de nombres.|  
|Especificar qué artefactos asociados a una capa no deben pertenecer a los espacios de nombres especificados|Escriba los espacios de nombres en la capa **Forbidden Namespaces** propiedad. Use un punto y coma (**;**) para separar los espacios de nombres.|  
|Especificar qué artefactos asociados a una capa no deben pertenecer a uno de los espacios de nombres especificados|Escriba el espacio de nombres en la capa **Required Namespaces** propiedad. Use un punto y coma (**;**) para separar los espacios de nombres.|  
  
##  <a name="EditLayout"></a> Cambiar cómo aparecen los elementos en el diagrama  
 Puede cambiar el tamaño, la forma, el color y la posición de las capas o el color de las dependencias mediante la edición de sus propiedades.  
  
##  <a name="Codemaps"></a> Detectar patrones y las dependencias de un mapa de código  
 Durante la creación de diagramas de dependencia, también puede crear **mapas de código**. Estos diagramas pueden ayudarle a detectar patrones y dependencias mientras explora el código. Use el Explorador de soluciones, la Vista de clases o el Examinador de objetos para explorar los ensamblados, los espacios de nombres y las clases, que a menudo corresponden a las capas existentes. Para obtener más información sobre mapas de código, vea:  
  
-   [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)  
  
-   [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Buscar posibles problemas mediante analizadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
## <a name="see-also"></a>Vea también  
 [Vídeo: Validar las dependencias de arquitectura en tiempo real](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)   
 [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)   
 [Diagramas de dependencia: instrucciones](../modeling/layer-diagrams-guidelines.md)   
 [Validar código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)   
 [Visualizar el código](../modeling/visualize-code.md)
