---
title: 'Diagramas de dependencia: Instrucciones | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 2903bec7-a93b-46a6-aac6-994ac4f3f1a7
caps.latest.revision: 55
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 8233d0d6ce81a0869e99f5baf45b7ef7b3fc9019
ms.lasthandoff: 02/22/2017

---
# <a name="dependency-diagrams-guidelines"></a>Diagramas de dependencia: instrucciones
Describe la arquitectura de la aplicación en un nivel alto mediante la creación de *diagramas de dependencia* en Visual Studio. Asegúrese de que su código sea coherente con este diseño, valide el código con un diagrama de dependencia. También puede incluir la validación de capas en el proceso de compilación. Consulte [vídeo de Channel 9: diseño y validar la arquitectura mediante diagramas de dependencia](http://go.microsoft.com/fwlink/?LinkID=252073).  
  
 Para ver qué versiones de Visual Studio admiten esta característica, consulte [compatibilidad con la versión de arquitectura y herramientas de modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="what-is-a-dependency-diagram"></a>¿Qué es un diagrama de dependencia?  
 Al igual que un diagrama de arquitectura tradicional, un diagrama de dependencia identifica los componentes primarios o las unidades funcionales del diseño y sus interdependencias. Cada nodo en el diagrama, se denomina un *capa*, representa un grupo lógico de espacios de nombres, proyectos u otros artefactos. Puede dibujar las dependencias que debería haber en el diseño. A diferencia de un diagrama de arquitectura tradicional, puede comprobar que las dependencias reales del código fuente se ajustan a las dependencias especificadas que se pretenden. Al incluir la validación en el proceso de compilación normal de [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)], tiene la garantía de que el código de programa seguirá ajustándose a la arquitectura del sistema cuando se realicen cambios. Consulte [diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md).  
  
##  <a name="a-nameupdatea-how-to-design-or-update-your-app-with-dependency-diagrams"></a><a name="Update"></a>Diseñar o actualizar la aplicación con diagramas de dependencia  
 Los pasos siguientes proporcionan una visión general de cómo utilizar los diagramas de dependencia dentro del proceso de desarrollo. Las secciones posteriores de este tema describen cada paso con más detalle. Si está desarrollando un nuevo diseño, omita los pasos en los que se hace referencia al código existente.  
  
> [!NOTE]
>  Estos pasos aparecen en un orden aproximado. Es probable que desee superponer las tareas, reorganizarlas para que se adapten a su situación particular y revisarlas al inicio de cada iteración del proyecto.  
  
1.  [Crear un diagrama de dependencia](#Create) para toda la aplicación, o para una de sus capas.  
  
2.  [Definir capas para representar las principales áreas o componentes funcionales](#CreateLayers) de la aplicación. Denomine estos niveles según su función, por ejemplo, "Presentación" o "Servicios". Si tiene una [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solución, puede asociar cada capa a una colección de *artefactos*, como proyectos, espacios de nombres, archivos y así sucesivamente.  
  
3.  [Detecte las dependencias existentes](#Generate) entre capas.  
  
4.  [Modifique las capas y dependencias](#EditArchitecture) para mostrar los archivos que desea que el código refleje el diseño.  
  
5.  [Diseñar nuevas áreas de la aplicación](#NewAreas) mediante la creación de capas para representar los principales bloques arquitectónicos o componentes y definir las dependencias para mostrar cómo cada capa emplea las otras.  
  
6.  [Modifique el diseño y el aspecto del diagrama](#EditLayout) que le ayudarán a ponerse en contacto con sus colegas.  
  
7.  [Valide el código con el diagrama de dependencia](#Validate) para resaltar los conflictos entre el código y la arquitectura necesaria.  
  
8.  [Actualice el código para que se ajuste a la nueva arquitectura](#UpdateCode). Desarrolle y refactorice el código en iteraciones hasta que la validación no muestre ningún conflicto.  
  
9. [Incluir validación de capas en el proceso de compilación](#BuildValidation) para asegurarse de que el código no se desvía del diseño.  
  
##  <a name="a-namecreatea-create-a-dependency-diagram"></a><a name="Create"></a>Crear un diagrama de dependencia  
 Un diagrama de dependencia debe crearse dentro de un proyecto de modelado. Puede agregar un nuevo diagrama de dependencia a un proyecto de modelado existente, cree un nuevo proyecto de modelado para el diagrama de dependencia o copiar un diagrama de dependencia existente en el mismo proyecto de modelado.  
  
> [!IMPORTANT]
>  No agregue, arrastre o copie un diagrama de dependencia existente de un proyecto de modelado a otro proyecto de modelado o a otra ubicación en la solución. Un diagrama de dependencia que se copia de esta manera tendrá las mismas referencias que el diagrama original, incluso si se modifica el diagrama. Esto impide que la validación de capas se haga correctamente y es posible que cause otros problemas, como la pérdida de elementos u otros errores al intentar abrir el diagrama.  
  
 Consulte [crear diagramas de dependencia desde el código](../modeling/create-layer-diagrams-from-your-code.md).  
  
##  <a name="a-namecreatelayersa-define-layers-to-represent-functional-areas-or-components"></a><a name="CreateLayers"></a>Definir capas para representar áreas o componentes funcionales  
 Las capas representan grupos lógicos de *artefactos*, como proyectos, archivos de código, espacios de nombres, clases y métodos. Se pueden crear capas a partir de artefactos de proyectos de Visual C# .NET y Visual Basic .NET, o bien se pueden adjuntar especificaciones o planes a una capa vinculando documentos, como archivos de Word o presentaciones de PowerPoint. Cada capa aparece como un rectángulo en el diagrama y muestra el número de artefactos vinculados a ella. Una capa puede contener capas anidadas que describan tareas más específicas.  
  
 Como regla general, denomine las capas según su función, por ejemplo, "Presentación" o "Servicios." Si los artefactos tienen una estrecha interdependencia, colóquelos en la misma capa. Si los artefactos se pueden actualizar de forma independiente o usar en aplicaciones diferentes, sitúelos en capas distintas. Para obtener más información acerca de los patrones de capas, visite el sitio de modelos y prácticas aspecto en [http://go.microsoft.com/fwlink/?LinkId=145794](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
> [!TIP]
>  Existen ciertos tipos de artefactos que se pueden vincular a capas, pero que no admiten la validación con el diagrama de dependencia. Para ver si el artefacto admite la validación, abra **Explorador de capas** para examinar el **admite validación** propiedades del vínculo de artefacto. Consulte [detectar las dependencias existentes entre capas](#Generate).  
  
 Al actualizar una aplicación desconocida, también puede crear mapas de código. Estos diagramas pueden ayudarle a detectar patrones y dependencias mientras explora el código. También puede usar el Explorador de soluciones para examinar los espacios de nombres y las clases, que suelen corresponderse con las capas existentes. Asignar estos artefactos de código a las capas arrastrándolos desde el Explorador de soluciones a los diagramas de dependencia. A continuación, puede utilizar diagramas de dependencia para ayudarle a actualizar el código y mantener la coherencia con el diseño.  
  
 Vea:  
  
-   [Crear diagramas de dependencia desde el código](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)  
  
##  <a name="a-namegeneratea-discover-existing-dependencies-between-layers"></a><a name="Generate"></a>Detectar las dependencias existentes entre capas  
 Una dependencia existe cuando un artefacto que está asociado a una capa tiene una referencia a un artefacto que está asociado a otra capa. Por ejemplo, una clase de una capa declara una variable que tiene una clase en otra capa. Puede detectar las dependencias existentes aplicándoles técnicas de ingeniería inversa.  
  
> [!NOTE]
>  No se puede realizar ingeniería inversa en las dependencias de ciertos tipos de artefactos. Por ejemplo, no se va a realizar ingeniería inversa en ninguna dependencia que tenga como origen o destino una capa vinculada a un archivo de texto. Para ver qué artefactos tienen dependencias que se puede aplicar ingeniería inversa, haga clic en una o varias capas y, a continuación, haga clic en **ver vínculos**. En **Explorador de capas**, examine la **admite validación** columna. Dependencias no se pueden realizar ingeniería inversa de artefactos en el que se muestra esta columna **False**.  
  
#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Para realizar ingeniería inversa de las dependencias existentes entre capas  
  
-   Seleccione una o varias capas, haga clic en una capa seleccionada y, a continuación, haga clic en **generar dependencias**.  
  
 Normalmente, verá algunas dependencias que no deberían existir. Puede editar estas dependencias para alinearlas con el diseño buscado.  
  
##  <a name="a-nameeditarchitecturea-edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditArchitecture"></a>Editar capas y dependencias para mostrar el diseño previsto  
 Para describir los cambios que piensa realizar en el sistema o la arquitectura deseada, use los siguientes pasos para editar el diagrama de dependencia. También podría realizar algunos cambios de refactorización para mejorar la estructura del código antes de extenderlo. Consulte [mejorar la estructura del código](#Improving).  
  
|**En**|**Siga estos pasos**|  
|------------|-----------------------------|  
|Eliminar una dependencia que no debería existir|Haga clic en la dependencia y, a continuación, presione **eliminar**.|  
|Cambiar o restringir la dirección de una dependencia|Establezca su **dirección** propiedad.|  
|Crear nuevas dependencias|Utilice la **dependencia** y **dependencia bidireccional** herramientas.<br /><br /> Para dibujar varias dependencias, haga doble clic en la herramienta. Cuando haya terminado, haga clic en el **puntero** herramienta o presione la **ESC** clave.|  
|Especificar qué artefactos asociados a una capa no pueden depender de los espacios de nombres especificados|Escriba los espacios de nombres en la capa **Forbidden Namespace Dependencies** propiedad. Utilice un punto y coma (**;**) para separar los espacios de nombres.|  
|Especificar qué artefactos asociados a una capa no deben pertenecer a los espacios de nombres especificados|Escriba los espacios de nombres en la capa **Forbidden Namespaces** propiedad. Utilice un punto y coma (**;**) para separar los espacios de nombres.|  
|Especificar qué artefactos asociados a una capa no deben pertenecer a uno de los espacios de nombres especificados|Escriba el espacio de nombres en la capa **Required Namespaces** propiedad. Utilice un punto y coma (**;**) para separar los espacios de nombres.|  
  
###  <a name="a-nameimprovinga-improving-the-structure-of-the-code"></a><a name="Improving"></a>Mejorar la estructura del código  
 Los cambios de refactorización son mejoras que no afectan al comportamiento de la aplicación, pero que facilitan los cambios y las ampliaciones del código en el futuro. Un código bien estructurado tiene un diseño que resulta fácil abstraer en un diagrama de dependencia.  
  
 Por ejemplo, si crea una capa para cada espacio de nombres del código y, a continuación, aplica técnicas de ingeniería inversa a las dependencias, debe haber un conjunto mínimo de dependencias unidireccionales entre las capas. Si crea un diagrama más detallado usando clases o métodos como capas, el resultado debería tener también las mismas características.  
  
 Si no es así, el código será más difícil de modificar a lo largo de su vida útil y será menos apropiado para la validación con diagramas de dependencia.  
  
##  <a name="a-namenewareasa-design-new-areas-of-your-application"></a><a name="NewAreas"></a>Diseñar nuevas áreas de la aplicación  
 Cuando comience el desarrollo de un nuevo proyecto, o una nueva área de un nuevo proyecto, puede dibujar capas y dependencias que le ayuden a identificar los componentes primarios antes de empezar a desarrollar el código.  
  
-   **Muestre modelos arquitectónicos identificables** en los diagramas de dependencia, si es posible. Por ejemplo, un diagrama de dependencia que describe una aplicación de escritorio puede incluir capas como presentación, lógica del dominio y almacén de datos. Un diagrama de dependencia que abarque una única característica de una aplicación puede tener las capas modelo, vista y controlador. Para obtener más información sobre esos patrones, consulte [modelos y prácticas de aspecto: arquitectura de la aplicación](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
     Si genera a menudo modelos similares, cree una herramienta personalizada. Consulte [definir personalizado en un elemento de cuadro de herramientas de modelado](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
-   **Cree un artefacto de código para cada capa** como un espacio de nombres, clase o componente. De este modo, le resultará más fácil hacer un seguimiento del código y vincular los artefactos de código a las capas. Tan pronto como cree cada uno de los artefactos, vincúlelo a la capa apropiada.  
  
-   **No es necesario vincular la mayoría de las clases y otros artefactos a las capas** pues pertenecen a artefactos mayores, como espacios de nombres que ya han vinculado a las capas.  
  
-   **Cree un nuevo diagrama para una característica nueva**. Normalmente, habrá uno o varios diagramas de dependencia que se describa toda la aplicación. Si está diseñando una nueva característica de la aplicación, no agregue ni cambie los diagramas existentes. En su lugar, cree un diagrama propio en el que refleje los nuevos elementos del código. Las capas del nuevo diagrama pueden incluir las capas de la presentación, la lógica del dominio y la base de datos de la nueva característica.  
  
     Cuando compile la aplicación, el código se validará con el diagrama general y con el diagrama más detallado de la característica.  
  
##  <a name="a-nameeditlayouta-edit-the-layout-for-presentation-and-discussion"></a><a name="EditLayout"></a>Editar el diseño para su presentación y explicación  
 Para que le resulte más fácil identificar las capas y dependencias o para analizarlas con los miembros del equipo, edite el aspecto y el diseño del diagrama de los siguientes modos:  
  
-   Cambiar el tamaño, la forma y la posición de las capas.  
  
-   Cambiar el color de las capas y las dependencias.  
  
    -   Seleccione una o varias capas o dependencias, con el botón secundario y, a continuación, haga clic en **propiedades**. En el **propiedades** ventana, editar la **Color** propiedad.  
  
##  <a name="a-namevalidatea-validate-the-code-against-the-diagram"></a><a name="Validate"></a>Valide el código con el diagrama  
 Una vez editado el diagrama, puede validarlo con el código manualmente en cualquier momento o automáticamente cada vez que se ejecute una compilación local o [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)].  
  
 Vea:  
  
-   [Validar código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md)  
  
-   [Incluir validación de capas en el proceso de compilación](#BuildValidation)  
  
##  <a name="a-nameupdatecodea-update-the-code-to-conform-to-the-new-architecture"></a><a name="UpdateCode"></a>Actualice el código para que se ajuste a la nueva arquitectura  
 Normalmente, los errores aparecerán la primera vez que valide el código contra un diagrama de dependencias actualizado. Estos errores pueden tener varias causas:  
  
-   Un artefacto se ha asignado a la capa equivocada. En este caso, mueva el artefacto.  
  
-   Un artefacto, como por ejemplo una clase, usa otra clase de forma que hay conflictos con su arquitectura. En este caso, tiene que refactorizar el código para quitar la dependencia.  
  
 Para resolver estos errores, actualice el código hasta no aparezcan más errores durante la validación. Normalmente, este es un proceso iterativo. Para obtener más información acerca de estos errores, vea [validar código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md).  
  
> [!NOTE]
>  Medida que desarrolla o refactoriza el código, tenga nuevos artefactos que deba vincular al diagrama de dependencia. Sin embargo, esto podría no ser necesario, por ejemplo, si tiene capas que representan espacios de nombres existentes, y el nuevo código solo agrega más material a estos espacios de nombres.  
  
 Durante el proceso de desarrollo, puede que desee suprimir algunos de los conflictos notificados durante la validación. Por ejemplo, es posible que desee suprimir errores de los que ya se ha ocupado o que no son pertinentes para su escenario concreto. Cuando se suprime un error, conviene registrar un elemento de trabajo en [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]. Para realizar esta tarea, vea [validar código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md).  
  
##  <a name="a-namebuildvalidationa-include-layer-validation-in-the-build-process"></a><a name="BuildValidation"></a>Incluir validación de capas en el proceso de compilación  
 Para asegurarse de que los futuros cambios en el código se ajustan a los diagramas de dependencia, incluir la validación de capas al proceso de compilación estándar de la solución. Cuando otros miembros del equipo compilen la solución, cualquier diferencia entre las dependencias en el código y el diagrama de dependencia se notificará como errores de compilación. Para obtener más información acerca de cómo incluir la validación de capas en el proceso de compilación, consulte [validar código con diagramas de dependencia](../modeling/validate-code-with-layer-diagrams.md).  
  
## <a name="see-also"></a>Vea también  
 [Diagramas de dependencia: referencia](../modeling/layer-diagrams-reference.md)   
 [Crear diagramas de dependencia desde el código](../modeling/create-layer-diagrams-from-your-code.md)

