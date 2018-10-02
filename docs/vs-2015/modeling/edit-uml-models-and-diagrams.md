---
title: Editar modelos y diagramas UML | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.modelingproject
- vs.teamarch.UMLModelExplorer
- vs.teamarch.UMLModelExplorer.rootnode
helpviewer_keywords:
- diagrams - modeling
- UML, copy and paste
- UML, models
- UML model
- UML, element properties
- UML
- UML, diagrams
ms.assetid: 87affd40-8127-4ee9-9d3a-ad977abe2ed6
caps.latest.revision: 86
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0620f0a1212d7abd864a9428492d95067098ef16
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576401"
---
# <a name="edit-uml-models-and-diagrams"></a>Editar modelos y diagramas UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [modelos y diagramas UML editar](https://docs.microsoft.com/visualstudio/modeling/edit-uml-models-and-diagrams).  
  
Puede crear y modificar un modelo UML a través de las vistas proporcionadas por los distintos tipos de diagrama. Al ofrecer perspectivas diferentes en su sistema, estos diagramas ayudan a comprender y analizar diferentes aspectos de su diseño y los requisitos. Visual Studio proporciona plantillas para cinco de los tipos de diagramas de UML utilizados con más frecuencia.  
  
 Para ver qué versiones de Visual Studio admiten esta característica, vea [Compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 En este tema se describen las técnicas para modificar el modelo que son comunes entre los diferentes tipos de diagramas. Para obtener más información específica para determinados tipos de diagramas, vea [crear modelos para la aplicación](../modeling/create-models-for-your-app.md).  
  
## <a name="in-this-topic"></a>En este tema  
  
-   [Diagramas de UML son vistas de un modelo UML](#Views)  
  
-   [Creación de diagramas de modelado UML](#Creating)  
  
-   [Dibujar diagramas de modelado UML](#Drawing)  
  
-   [Modificar formas y conectores](#Editing)  
  
-   [Deshacer cambios en el modelo](#Undo)  
  
-   [Compartir elementos entre diagramas](#Sharing)  
  
-   [Copiar elementos y grupos de elementos relacionados](#Copying)  
  
-   [Eliminación de un elemento de modelo o sus vistas](#Deleting)  
  
-   [Búsqueda de texto en un diagrama](#Searching)  
  
-   [Preparar un diagrama de presentación](#presentation)  
  
-   [Extender los diseñadores de UML](#extensions)  
  
##  <a name="Views"></a> Diagramas de UML son vistas de un modelo UML  
 Puede crear y usar diagramas de UML solo en proyectos de modelado. Para obtener más información acerca de cómo crear proyectos y diagramas, vea [crear modelos de proyectos y diagramas UML](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
-   Un proyecto de modelado contiene un solo modelo UML. Cada diagrama de UML del proyecto es una vista del modelo UML.  
  
-   Puede ver el modelo en **Explorador de modelos UML**. En el **arquitectura** menú, elija **Windows**y, a continuación, haga clic en **Explorador de modelos UML**.  
  
-   Cada forma de un diagrama es una vista de un elemento en el modelo. Cuando se coloca una forma nueva en un diagrama, se crea un nuevo elemento en el modelo.  
  
-   Cuando se guarda un diagrama, Visual Studio guarda el modelo entero, todos sus diagramas y el modelado del archivo de proyecto.  
  
##  <a name="Creating"></a> Creación de diagramas de modelado UML  
  
1.  En el **arquitectura** menú en Visual Studio, haga clic en **nuevo UML o diagrama de capas**.  
  
2.  Seleccione el diagrama y asígnele un nombre.  
  
3.  En **agregar a proyecto de modelado**, seleccione un proyecto de modelado existente o seleccione **crear un nuevo proyecto de modelado**.  
  
    > [!NOTE]
    >  Los diagramas de modelado solo pueden existir dentro de un proyecto de modelado.  
  
 También puede agregar un diagrama a un proyecto de modelado existente en el Explorador de soluciones. Haga clic en el proyecto de modelado, elija **agregar**y, a continuación, haga clic en **nuevo elemento**.  
  
#### <a name="to-create-an-empty-uml-modeling-project"></a>Para crear un proyecto de modelado UML vacío  
  
-   En el **archivo** menú, elija **New**, haga clic en **proyecto**y en el **nuevo proyecto** cuadro de diálogo, haga doble clic en **de modelado Proyectos**.  
  
 Para obtener más información sobre cómo administrar proyectos de modelado, vea [crear modelos de proyectos y diagramas UML](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
##  <a name="Drawing"></a> Dibujar diagramas de modelado UML  
 Un diagrama de modelado muestra una colección de elementos del modelo vinculados mediante relaciones. Cada elemento se muestra como una forma y cada relación se muestra como un conector entre dos formas.  
  
 Hay dos tipos de herramientas: una para los elementos y otra para las relaciones. Por ejemplo, en el diagrama de clases UML del cuadro de herramientas, **clase** es una herramienta de elemento, y **asociación** es una herramienta de relación.  
  
> [!NOTE]
>  Si desea obtener información específica para determinados tipos de diagramas, vea [crear modelos para la aplicación](../modeling/create-models-for-your-app.md).  
  
#### <a name="to-create-elements-and-relationships-in-a-uml-modeling-diagram"></a>Para crear elementos y relaciones en un diagrama de modelado UML  
  
1.  Para crear un elemento del modelo, haga clic en una herramienta de elemento en el cuadro de herramientas y, a continuación, haga clic en el diagrama donde desea que aparezca. Después de haber creado el elemento, ajuste su tamaño y forma arrastrando sus controladores.  
  
     En algunos casos, puede colocar un nuevo elemento dentro de otro elemento. Por ejemplo, en un diagrama de clases UML, puede colocar una clase dentro de un paquete.  
  
    > [!NOTE]
    >  Si no ve el cuadro de herramientas, haga clic en **cuadro de herramientas** en el **vista** menú.  
  
2.  Para crear una relación, haga clic en una herramienta de relación, haga clic en el elemento donde desea que inicie la relación y, a continuación, haga clic en el elemento donde desea que finalice.  
  
     Distintos tipos de relaciones pueden iniciar o finalizar en distintos tipos de elementos. Por ejemplo, en un diagrama de clases UML, una relación de asociación no puede iniciar o finalizar en un elemento de comentario.  
  
    > [!NOTE]
    >  Para usar la misma herramienta varias veces, haga doble clic en la herramienta. Cuando haya terminado, haga clic en el **puntero** herramienta.  
  
 En algunos tipos de diagramas, también puede dibujar formas simples. Estas formas no son parte del modelo, pero puede usarlas para llamar la atención sobre los elementos del diagrama o para dividirlo en áreas diferentes.  
  
##  <a name="Editing"></a> Modificar formas y conectores  
 Al cambiar el tamaño o color de una forma o reenrutar un conector, no hay ningún efecto en el modelo subyacente. Sin embargo, cuando al cambiar el nombre de una forma en el diagrama o en el Explorador de modelos UML, se cambia el nombre del elemento correspondiente en el Explorador de modelos UML y en cualquier otro diagrama que presente ese elemento.  
  
> [!NOTE]
>  Hay una forma sencilla de crear nuevos elementos de cuadro de herramientas desde los que puede crear grupos de elementos o elementos con su propia elección de propiedades. Para obtener más información, consulte [definir personalizado en un elemento de cuadro de herramientas de modelado](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
 En la siguiente ilustración se muestra cómo cambiar el tamaño de una forma o su nombre.  
  
 ![Ajustar un elemento de modelo](../modeling/media/uml-drawadjust1.png "UML_DrawAdjust1")  
  
> [!TIP]
>  Los comandos integrados no incluyen un comando para alinear las formas perfectamente. Sin embargo, puede crear fácilmente su propio comando de alineación copiando el código en el ejemplo de [mostrar un modelo UML en diagramas](../modeling/display-a-uml-model-on-diagrams.md).  
  
 En la siguiente ilustración se muestra cómo ajustar la ruta y la posición de un conector o de sus etiquetas.  
  
 ![Ajustar un conector](../modeling/media/uml-drawadjust2.png "UML_DrawAdjust2")  
  
#### <a name="to-move-one-end-of-a-connector-to-another-shape"></a>Para mover un extremo de un conector a otra forma  
  
1.  Realice una de las siguientes acciones:  
  
    -   Presione **CTRL** y mueva el extremo.  
  
     \- o -  
  
    -   Haga clic en el conector y, a continuación, haga clic en **volver a conectar**.  
  
2.  Haga clic en el extremo del conector que desea mover.  
  
3.  Haga clic en la forma a la que desea que el conector se mueva.  
  
#### <a name="to-change-color-or-other-properties-of-an-element-relationship-or-diagram"></a>Para cambiar el color u otras propiedades de un elemento, relación o diagrama  
  
-   Haga clic en el elemento y establezca los campos el **propiedades** ventana.  
  
     Si no ve el **propiedades** , haga clic en el elemento y, a continuación, haga clic en **propiedades.**  
  
#### <a name="to-zoom-in-and-out-on-a-modeling-diagram"></a>Para acercar y alejar en un diagrama de modelado  
  
-   Presione y mantenga presionada la **CTRL** clave mientras gira la rueda del mouse.  
  
     \- o -  
  
-   Presione y mantenga **CTRL+MAYÚS**y, a continuación, haga clic en el botón izquierdo o derecho del mouse.  
  
     \- o -  
  
-   En el **diseñadores de arquitectura** barra de herramientas, haga clic en el signo más (**+**) o signo menos (**-**), o elija un nivel de zoom.  
  
##  <a name="Searching"></a> Buscar en un diagrama  
 La función de búsqueda rápida busca elementos en un diagrama. Debe establecer **buscar en:** a **documento actual**.  
  
#### <a name="to-search-for-text-in-a-modeling-diagram"></a>Para buscar texto en un diagrama de modelado  
  
1.  Presione **CTRL + F**.  
  
     \- o -  
  
     En el **editar** menú, elija **buscar y reemplazar**y, a continuación, haga clic en **búsqueda rápida**.  
  
    > [!NOTE]
    >  En el **buscar y reemplazar** cuadro de diálogo, debe dejar el **buscar en** campo establecido en **documento actual**. No se admiten las demás opciones.  
  
2.  Escriba el texto que desea buscar y, a continuación, haga clic en **Buscar siguiente**.  
  
    > [!NOTE]
    >  Si el texto que desea buscar está dentro de una forma contraída, la forma aparecerá resaltada. Expanda la forma y, a continuación, haga clic en **Buscar siguiente** nuevo.  
  
##  <a name="Undo"></a> Deshacer cambios en el modelo  
 Puede deshacer y rehacer los cambios realizados en el modelo y diagramas usando la **deshacer** y **rehacer** comandos en el **editar** menú.  
  
 **Cada proyecto de modelado contiene un único bloque de cambios.** Todos los cambios que realiza en el modelo y los diagramas se mantienen en esta pila. La pila también incluye cambios de foco de un diagrama a otro. El comando Deshacer revierte los cambios de esta pila.  
  
 Por ejemplo, supongamos que realiza las siguientes operaciones: realizar un cambio en Diagrama1, cambiar el foco en Diagrama 2, cambiar Diagrama2. Al deshacer los cambios, la primera vez se revertirá el último cambio, la siguiente vez se volverá a cambiar el foco a Diagrama 1 y la tercera vez se revertirá el cambio en Diagrama1.  
  
 **Al cerrar un diagrama, trunca la pila de cambios.** Si cierra un diagrama, no podrá deshacer los cambios que realizó en dicho diagrama y no podrá deshacer los cambios anteriores en el modelo o cualquiera de sus diagramas.  
  
 **No se puede deshacer mientras se edita una propiedad.** Mientras se edita una propiedad en la ventana Propiedades, o en una etiqueta de un diagrama, solo se pueden deshacer los cambios realizados en esa propiedad. Complete el cambio en la propiedad presionando ENTRAR o cancélelo presionando la tecla ESC. A continuación, podrá deshacer los cambios en el modelo y los diagramas.  
  
 **Al cerrar un diagrama sin guardar los cambios que no tenga el efecto esperado.** Si realiza algunos cambios y luego cierra un diagrama sin guardarlo, todavía se conservarán los cambios en el modelo. Se recomienda cerrar todo el modelo si desea hacerlo sin guardarlo.  
  
##  <a name="Sharing"></a> Compartir elementos entre diagramas  
 Puede hacer que una instancia específica de un elemento de modelo aparezca más de una vez en los diagramas. Esto se aplica a las clases, interfaces, componentes, casos de uso y actores.  
  
 Esto resulta útil si desea mostrar distintos grupos de relaciones en distintos diagramas. Por ejemplo, en un diagrama, puede mostrar las asociaciones entre las clases de dirección y cliente. En otro diagrama puede mostrar de nuevo la clase de dirección con su asociación al área postal.  
  
 Para cambiar las propiedades de un elemento de modelo, como su nombre, seleccione cualquiera de sus vistas en un diagrama o selecciónelo en el Explorador de modelos UML.  
  
 Cada tipo de diagrama solo puede mostrar algunos tipos de elemento de modelo. Por ejemplo, no puede mostrar un caso de uso en un diagrama de componentes. Por lo tanto, los procedimientos siguientes funcionarán exclusivamente en algunas combinaciones de elementos de modelo y diagramas.  
  
#### <a name="to-add-a-new-view-of-a-model-element-by-using-uml-model-explorer"></a>Para agregar una nueva vista de un elemento de modelo mediante el Explorador de modelos UML  
  
1.  Para abrir **Explorador de modelos UML**, en el **arquitectura** menú, elija **Windows**y, a continuación, haga clic en **Explorador de modelos UML**.  
  
2.  Arrastre el elemento de modelo de **Explorador de modelos UML** hasta un diagrama compatible en el mismo proyecto.  
  
     Aparece una forma que proporciona una vista del elemento del modelo, además de las vistas en otros diagramas o en el mismo diagrama.  
  
    > [!NOTE]
    >  El efecto es diferente cuando arrastra una clase o un componente a un diagrama de secuencia. En ese caso, se crea una nueva línea de vida cuyo tipo sea esa clase o componente. Para obtener más información, consulte [diagramas de secuencia UML: instrucciones](../modeling/uml-sequence-diagrams-guidelines.md).  
  
#### <a name="to-add-a-new-view-of-a-model-element-by-using-paste-reference"></a>Para agregar una nueva vista de un elemento de modelo mediante Pegar referencia  
  
1.  Haga clic en un elemento existente y, a continuación, haga clic en **copia**.  
  
    -   Puede copiar varios elementos al mismo tiempo. Mantenga presionada la tecla CTRL mientras hace clic en cada elemento, haga clic en uno de ellos, a continuación, haga clic en **copia**.  
  
2.  Haga clic en un área vacía de un diagrama compatible y, a continuación, haga clic en **Pegar referencia**.  
  
     Aparecerá otra vista del mismo elemento.  
  
    > [!NOTE]
    >  Esto difiere de la **pegar** comando, que crea un nuevo elemento en el modelo. Para obtener más información, consulte [copiar elementos y grupos de elementos relacionados](#Copying).  
  
> [!NOTE]
>  Si agrega a un diagrama vistas de dos elementos de modelo que ya están conectados por una relación, también aparecerá una vista de la relación en el diagrama. Para eliminar esta vista, simplemente quite uno de los elementos del diagrama o elimine la relación del modelo.  
  
##  <a name="Copying"></a> Copiar elementos y grupos de elementos relacionados  
 Puede copiar y pegar elementos del modelo, y puede copiar y pegar grupos de elementos junto con las relaciones entre ellos.  
  
> [!NOTE]
>  El **pegar** y **Pegar referencia** comandos tienen efectos diferentes. **Pegar** crea nuevos elementos cuyas propiedades son similares a las de los elementos copiados. **Pegar referencia** crea nuevas vistas de los mismos elementos.  
  
#### <a name="to-copy-elements-and-their-relationships"></a>Para copiar elementos y sus relaciones  
  
1.  En el diagrama con los elementos que desea copiar, seleccione uno o varios elementos.  
  
    > [!NOTE]
    >  No puede copiar relaciones, excepto como parte de un grupo de elementos.  
  
2.  En el **editar** menú, haga clic en **copia**.  
  
3.  Si desea copiar los elementos en otro diagrama, cree el nuevo diagrama o abra el diagrama existente.  
  
4.  En el **editar** menú, haga clic en **pegar**.  
  
    -   Aparecerán las copias de los elementos, junto con las copias de las relaciones que se vinculan entre ellos.  
  
    -   Cada nuevo elemento tendrá un nombre generado automáticamente.  
  
5.  Ajuste las posiciones, los nombres y otras propiedades de los nuevos elementos y relaciones.  
  
> [!NOTE]
>  No puede copiar un elemento de modelo de un modelo a otro, por ejemplo, si tiene dos modelos en la misma solución. Pero puede copiar elementos de un diagrama a otro.  
  
#### <a name="to-copy-an-entire-diagram"></a>Para copiar un diagrama completo  
  
1.  Cree un nuevo diagrama.  
  
2.  Seleccione todos los elementos en un diagrama existente, cópielos y péguelos en el nuevo.  
  
 No se puede replicar un diagrama copiando y pegando en el Explorador de soluciones.  
  
##  <a name="Deleting"></a> Eliminación de un elemento de modelo o sus vistas  
 Algunos tipos de elementos, especialmente los clasificadores, se pueden quitar de un diagrama sin eliminarlos del modelo. Los clasificadores son los elementos principales que se muestran en los diagramas de clases, diagramas de componentes y diagramas de casos de uso. Pueden aparecer en más de un diagrama. Para estos tipos de elementos, hay dos comandos independientes: **quitar del diagrama** y **eliminar del modelo**.  
  
 Por el contrario, cuando se elimina una relación de un diagrama, siempre se elimina del modelo.  
  
> [!NOTE]
>  Ciertos tipos de elementos en un diagrama UML tienen etiquetas. Al seleccionar estos elementos dibujando un rectángulo en torno a ellos, es posible seleccionar las etiquetas, pero no los elementos que poseen esas etiquetas. No es posible eliminar un subconjunto de los elementos seleccionados de esta manera. Para seleccionar un subconjunto de estos elementos, mantenga presionada la **CTRL** mientras hace clic en cada elemento de la clave.  
  
#### <a name="to-remove-a-classifiers-view-from-a-diagram"></a>Para quitar una vista de clasificador de un diagrama  
  
-   Haga clic en el elemento en el diagrama y, a continuación, haga clic en **quitar del diagrama**.  
  
 \- o -  
  
-   Haga clic en el elemento del diagrama y, a continuación, presione el **eliminar** clave.  
  
    -   Esta vista del elemento desaparece. Sin embargo, el elemento permanece en el modelo y aún puede encontrarlo en **Explorador de modelos UML**. También permanecen las demás vistas del mismo elemento.  
  
    -   Todos los conectores que terminan en esta forma se quitan del diagrama, pero la relación que representa se mantiene en el modelo. Puede ver la relación en **Explorador de modelos UML** en **relaciones**, debajo de cada elemento que se conecta.  
  
#### <a name="to-delete-an-element-from-the-model"></a>Para eliminar un elemento del modelo  
  
-   Haga clic en el elemento o bien en **Explorador de modelos UML** o en un diagrama y, a continuación, haga clic en **eliminar del modelo**.  
  
    -   El elemento se elimina de todos los diagramas en los que aparece.  
  
    -   Todas las relaciones que terminan en este elemento también se eliminan del modelo.  
  
#### <a name="to-delete-a-relationship-from-the-model"></a>Para eliminar una relación del modelo  
  
-   Haga clic en la relación en un diagrama o en **Explorador de modelos UML**y, a continuación, haga clic en **eliminar del modelo**.  
  
    > [!CAUTION]
    >  No se puede quitar una relación de un diagrama sin quitarla del modelo.  
  
     La relación se elimina del modelo y se elimina de todos los diagramas en los que aparece.  
  
##  <a name="presentation"></a> Preparar un diagrama de presentación  
 Las siguientes características le ayudarán a llamar la atención sobre partes específicas del diagrama, agregar explicaciones o dividir un diagrama en distintas áreas de interés.  
  
-   Puede copiar cualquier parte de un diagrama en Word, PowerPoint u otro documento. Seleccione las formas y conectores que desee, haga clic en y, a continuación, haga clic en **copia**.  
  
-   Se puede cambiar el color de cualquier forma o conector. Seleccione una o varias formas y cambie el **Color** propiedad. Si no ve la ventana **Propiedades**, presione **F4**.  
  
-   En algunos tipos de diagramas, puede dibujar líneas, rectángulos y elipses desde la **formas simples** sección del cuadro de herramientas. Estas formas no forman parte del modelo UML.  
  
-   Para etiquetar un área, puede arrastrar un comentario desde el cuadro de herramientas y, a continuación, establecer su **transparente** propiedad **True**. Al igual que las formas simples, los comentarios no forman parte del modelo UML y no aparecen en el Explorador de modelos UML.  
  
-   Para agregar notas y explicaciones a los elementos del modelo, puede crear comentarios y, a continuación, vincularlos a los elementos.  
  
-   Para alinear perfectamente las formas de una columna o fila en el diagrama, puede instalar el comando Alinear formas. Esto está disponible como una extensión UML de ejemplo: [UML: comando para alinear formas](http://code.msdn.microsoft.com/UML-command-to-Align-4139c0d7)  
  
### <a name="to-export-a-diagram-as-an-image"></a>Para exportar un diagrama como imagen  
 Para obtener más información, consulte [exportar diagramas como imágenes](../modeling/export-diagrams-as-images.md).  
  
##  <a name="extensions"></a> Extender los diseñadores de UML  
 Puede agregar nuevas funcionalidades a las herramientas de UML y adaptar la notación del diagrama a sus propias necesidades. Para obtener más información, consulte [modelos y diagramas UML ampliar](../modeling/extend-uml-models-and-diagrams.md).  
  
 Hay varios ejemplos de extensiones disponibles. Simplemente puede instalarlos y usarlos, o bien puede usar su código fuente como base para sus propias extensiones. Entre los ejemplos se incluye:  
  
|||  
|-|-|  
|[Alinear formas](http://code.msdn.microsoft.com/UML-command-to-Align-4139c0d7)|Comando de menú que ayuda a ordenar un diagrama.|  
|[Vincular a documentos](http://code.msdn.microsoft.com/Link-UML-elements-to-0adbf5a8)|Vincule cualquier elemento UML a encabezados de Word, diapositivas de PowerPoint, archivos de cualquier tipo, diagramas UML u otros elementos UML. El vínculo se puede crear simplemente arrastrando el elemento. Más adelante, puede hacer doble clic en el elemento para ver el elemento vinculado. Por ejemplo, puede vincular casos de uso a las especificaciones de Word o diagramas de actividades detallados y acciones para crear diapositivas de guiones gráficos.|  
|[Entrada rápida](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a)|Cree un modelo rápidamente mediante entrada de texto. Resulta útil para capturar ideas en las reuniones.|  
|[Color por estereotipo](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)|Clases de colores según un estereotipo. Puede ampliar fácilmente el código para que funcione con sus propios estereotipos.|  
|[Modelado de dominio](http://code.msdn.microsoft.com/UML-Domain-Modeling-6df6f7f4)|Valores predeterminados convenientes para los modelos de negocios. De manera predeterminada se muestran las asociaciones sin flechas y las operaciones no aparecen en las clases.|  
  
## <a name="see-also"></a>Vea también  
 [Crear diagramas y proyectos de modelado UML](../modeling/create-uml-modeling-projects-and-diagrams.md)   
 [Analizar y modelar la arquitectura](../modeling/analyze-and-model-your-architecture.md)   
 [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)



