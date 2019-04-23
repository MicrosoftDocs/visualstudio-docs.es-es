---
title: 'Diagramas de capas: Instrucciones | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 2903bec7-a93b-46a6-aac6-994ac4f3f1a7
caps.latest.revision: 57
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 255843682034ab784f8271b2f454a60fdd4a77fa
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60096613"
---
# <a name="layer-diagrams-guidelines"></a>Diagramas de capas: Instrucciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Describe la arquitectura de la aplicación en un nivel alto mediante la creación de *diagramas de capas* en Visual Studio. Para asegurarse de que el código mantiene la coherencia con este diseño, valide el código con un diagrama de capas. También puede incluir la validación de capas en el proceso de compilación. Consulte [vídeo de Channel 9: Diseñar y validar la arquitectura mediante diagramas de capas](http://go.microsoft.com/fwlink/?LinkID=252073).  
  
 Para ver qué versiones de Visual Studio admiten esta característica, vea [Compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="what-is-a-layer-diagram"></a>¿Qué es un diagrama de capas?  
 Al igual que en un diagrama de arquitectura tradicional, en un diagrama de capas se identifican los componentes primarios o las unidades funcionales del diseño y sus interdependencias. Cada nodo en el diagrama, denominado un *capa*, representa un grupo lógico de espacios de nombres, proyectos u otros artefactos. Puede dibujar las dependencias que debería haber en el diseño. A diferencia de un diagrama de arquitectura tradicional, puede comprobar que las dependencias reales del código fuente se ajustan a las dependencias especificadas que se pretenden. Al incluir la validación en el proceso de compilación normal de [!INCLUDE[esprtfs](../includes/esprtfs-md.md)], tiene la garantía de que el código de programa seguirá ajustándose a la arquitectura del sistema cuando se realicen cambios. Consulte [diagramas de capas: referencia](../modeling/layer-diagrams-reference.md).  
  
## <a name="Update"></a> Cómo diseñar o actualizar la aplicación con diagramas de capas  
 Los siguientes pasos proporcionan información general sobre cómo utilizar los diagramas de capas dentro del proceso de desarrollo. Las secciones posteriores de este tema describen cada paso con más detalle. Si está desarrollando un nuevo diseño, omita los pasos en los que se hace referencia al código existente.  
  
> [!NOTE]
>  Estos pasos aparecen en un orden aproximado. Es probable que desee superponer las tareas, reorganizarlas para que se adapten a su situación particular y revisarlas al inicio de cada iteración del proyecto.  
  
1. [Crear un diagrama de capas](#Create) para toda la aplicación, o para una capa dentro de él.  
  
2. [Definir capas para representar las principales áreas o componentes funcionales](#CreateLayers) de la aplicación. Denomine estos niveles según su función, por ejemplo, "Presentación" o "Servicios". Si tiene un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] solución, puede asociar cada capa a una colección de *artefactos*, como proyectos, espacios de nombres, archivos y así sucesivamente.  
  
3. [Detecte las dependencias existentes](#Generate) entre capas.  
  
4. [Modifique las capas y dependencias](#EditArchitecture) para mostrar la actualización que desea que el código para reflejar el diseño.  
  
5. [Diseñe nuevas áreas de la aplicación](#NewAreas) mediante la creación de capas que representen los principales bloques arquitectónicos o componentes y definir las dependencias para mostrar cómo cada capa emplea las otras.  
  
6. [Editar el diseño y la apariencia del diagrama](#EditLayout) que le ayudarán a ponerse en contacto con sus compañeros.  
  
7. [Valide el código con el diagrama de capas](#Validate) para resaltar los conflictos entre el código y la arquitectura necesaria.  
  
8. [Actualice el código para que se ajuste a la nueva arquitectura](#UpdateCode). Desarrolle y refactorice el código en iteraciones hasta que la validación no muestre ningún conflicto.  
  
9. [Incluir validación de capas en el proceso de compilación](#BuildValidation) para asegurarse de que el código seguirá ajustándose a su diseño.  
  
## <a name="Create"></a> Crear un diagrama de capas  
 Los diagramas de capas deben crearse dentro de un proyecto de modelado. Se puede agregar un nuevo diagrama de capas a un proyecto de modelado ya existente, crear un nuevo proyecto de modelado para el diagrama de capas o bien copiar un diagrama de capas ya existente en el mismo proyecto de modelado.  
  
> [!IMPORTANT]
>  No agregue, arrastre ni copie un diagrama de capas de un proyecto de modelado a otro, ni a otra ubicación de la solución. Un diagrama de capas que se copia de esta manera tendrá las mismas referencias que el diagrama original, incluso si se modifica. Esto impide que la validación de capas se haga correctamente y es posible que cause otros problemas, como la pérdida de elementos u otros errores al intentar abrir el diagrama.  
  
 Consulte [crear diagramas de capas desde el código](../modeling/create-layer-diagrams-from-your-code.md).  
  
## <a name="CreateLayers"></a> Definir capas para representar áreas o componentes funcionales  
 Las capas representan grupos lógicos de *artefactos*, como proyectos, archivos de código, espacios de nombres, clases y métodos. Se pueden crear capas a partir de artefactos de proyectos de Visual C# .NET y Visual Basic .NET, o bien se pueden adjuntar especificaciones o planes a una capa vinculando documentos, como archivos de Word o presentaciones de PowerPoint. Cada capa aparece como un rectángulo en el diagrama y muestra el número de artefactos vinculados a ella. Una capa puede contener capas anidadas que describan tareas más específicas.  
  
 Como regla general, denomine las capas según su función, por ejemplo, "Presentación" o "Servicios." Si los artefactos tienen una estrecha interdependencia, colóquelos en la misma capa. Si los artefactos se pueden actualizar de forma independiente o usar en aplicaciones diferentes, sitúelos en capas distintas. Para obtener información sobre los patrones de capas, visite el sitio Patterns & Practices en [ http://go.microsoft.com/fwlink/?LinkId=145794 ](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
> [!TIP]
>  Existen ciertos tipos de artefactos que se pueden vincular a capas, pero que no admiten la validación con el diagrama de capas. Para ver si el artefacto admite la validación, abra **Explorador de capas** para examinar el **Supports Validation** propiedad del vínculo de artefacto. Consulte [detectar las dependencias existentes entre capas](#Generate).  
  
 Al actualizar una aplicación desconocida, también puede crear mapas de código. Estos diagramas pueden ayudarle a detectar patrones y dependencias mientras explora el código. También puede usar el Explorador de soluciones para examinar los espacios de nombres y las clases, que suelen corresponderse con las capas existentes. Asigne estos artefactos de código a las capas arrastrándolos desde el Explorador de soluciones hasta los diagramas de capas. Después, puede usar diagramas de capas, que le ayudarán a actualizar el código y mantener la coherencia con el diseño.  
  
 Vea:  
  
- [Crear diagramas de capas a partir del código](../modeling/create-layer-diagrams-from-your-code.md)  
  
- [Usar mapas de código para depurar aplicaciones](../modeling/use-code-maps-to-debug-your-applications.md)  
  
- [Asignar dependencias en las soluciones](../modeling/map-dependencies-across-your-solutions.md)  
  
## <a name="Generate"></a> Detectar las dependencias existentes entre capas  
 Una dependencia existe cuando un artefacto que está asociado a una capa tiene una referencia a un artefacto que está asociado a otra capa. Por ejemplo, una clase de una capa declara una variable que tiene una clase en otra capa. Puede detectar las dependencias existentes aplicándoles técnicas de ingeniería inversa.  
  
> [!NOTE]
>  No se puede realizar ingeniería inversa en las dependencias de ciertos tipos de artefactos. Por ejemplo, no se va a realizar ingeniería inversa en ninguna dependencia que tenga como origen o destino una capa vinculada a un archivo de texto. Para ver qué artefactos tienen dependencias que puede realizar ingeniería inversa, haga clic en una o varias capas y, a continuación, haga clic en **ver vínculos**. En **Explorador de capas**, examine el **admite validación** columna. Las dependencias no será de ingeniería inversa para los artefactos para el que esta columna muestra **False**.  
  
#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Para realizar ingeniería inversa de las dependencias existentes entre capas  
  
- Seleccione una o varias capas, haga clic en una capa seleccionada y, a continuación, haga clic en **generar dependencias**.  
  
  Normalmente, verá algunas dependencias que no deberían existir. Puede editar estas dependencias para alinearlas con el diseño buscado.  
  
## <a name="EditArchitecture"></a> Editar capas y dependencias para mostrar el diseño previsto  
 Para describir los cambios que piensa realizar en el sistema o la arquitectura deseada, use los pasos siguientes para editar el diagrama de capas. También podría realizar algunos cambios de refactorización para mejorar la estructura del código antes de extenderlo. Consulte [mejorar la estructura del código](#Improving).  
  
|**En**|**Siga estos pasos**|  
|------------|-----------------------------|  
|Eliminar una dependencia que no debería existir|Haga clic en la dependencia y, a continuación, presione **eliminar**.|  
|Cambiar o restringir la dirección de una dependencia|Establezca su **dirección** propiedad.|  
|Crear nuevas dependencias|Use la **dependencia** y **dependencia bidireccional** herramientas.<br /><br /> Para dibujar varias dependencias, haga doble clic en la herramienta. Cuando haya terminado, haga clic en el **puntero** herramientas o presione la **ESC** clave.|  
|Especificar qué artefactos asociados a una capa no pueden depender de los espacios de nombres especificados|Escriba los espacios de nombres en la capa **Forbidden Namespace Dependencies** propiedad. Use un punto y coma (**;**) para separar los espacios de nombres.|  
|Especificar qué artefactos asociados a una capa no deben pertenecer a los espacios de nombres especificados|Escriba los espacios de nombres en la capa **Forbidden Namespaces** propiedad. Use un punto y coma (**;**) para separar los espacios de nombres.|  
|Especificar qué artefactos asociados a una capa no deben pertenecer a uno de los espacios de nombres especificados|Escriba el espacio de nombres en la capa **Required Namespaces** propiedad. Use un punto y coma (**;**) para separar los espacios de nombres.|  
  
### <a name="Improving"></a> Mejorar la estructura del código  
 Los cambios de refactorización son mejoras que no afectan al comportamiento de la aplicación, pero que facilitan los cambios y las ampliaciones del código en el futuro. Un código bien estructurado tiene un diseño que resulta fácil abstraer en un diagrama de capas.  
  
 Por ejemplo, si crea una capa para cada espacio de nombres del código y, a continuación, aplica técnicas de ingeniería inversa a las dependencias, debe haber un conjunto mínimo de dependencias unidireccionales entre las capas. Si crea un diagrama más detallado usando clases o métodos como capas, el resultado debería tener también las mismas características.  
  
 De lo contrario, el código resultará más difícil de modificar a lo largo de su vida útil y será menos apropiado para llevar a cabo la validación con diagramas de capas.  
  
## <a name="NewAreas"></a> Diseñe nuevas áreas de la aplicación  
 Cuando comience el desarrollo de un nuevo proyecto, o una nueva área de un nuevo proyecto, puede dibujar capas y dependencias que le ayuden a identificar los componentes primarios antes de empezar a desarrollar el código.  
  
- **Muestre modelos arquitectónicos identificables** en los diagramas de capas, si es posible. Por ejemplo, un diagrama de capas en el que se describa una aplicación de escritorio puede incluir capas como Presentación, Lógica del dominio y Almacén de datos. Un diagrama de capas que abarque una única característica de una aplicación puede tener las capas Modelo, Ver y Controlador. Para obtener más información acerca de estos patrones, consulte [Patterns & Practices: Arquitectura de la aplicación](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
     Si genera a menudo modelos similares, cree una herramienta personalizada. Consulte [definir personalizado en un elemento de cuadro de herramientas de modelado](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
- **Crear un artefacto de código para cada capa** como un espacio de nombres, clase o componente. De este modo, le resultará más fácil hacer un seguimiento del código y vincular los artefactos de código a las capas. Tan pronto como cree cada uno de los artefactos, vincúlelo a la capa apropiada.  
  
- **No es necesario vincular la mayoría de las clases y otros artefactos a las capas** pues pertenecen a artefactos mayores, como espacios de nombres que ya han vinculado a las capas.  
  
- **Cree un nuevo diagrama de una nueva característica**. Normalmente, habrá uno o varios diagramas de capas en los que se describa toda la aplicación. Si está diseñando una nueva característica de la aplicación, no agregue ni cambie los diagramas existentes. En su lugar, cree un diagrama propio en el que refleje los nuevos elementos del código. Las capas del nuevo diagrama pueden incluir las capas de la presentación, la lógica del dominio y la base de datos de la nueva característica.  
  
     Cuando compile la aplicación, el código se validará con el diagrama general y con el diagrama más detallado de la característica.  
  
## <a name="EditLayout"></a> Editar el diseño para su presentación y explicación  
 Para que le resulte más fácil identificar las capas y dependencias o para analizarlas con los miembros del equipo, edite el aspecto y el diseño del diagrama de los siguientes modos:  
  
- Cambiar el tamaño, la forma y la posición de las capas.  
  
- Cambiar el color de las capas y las dependencias.  
  
    - Seleccione una o varias capas o dependencias, con el botón secundario y, a continuación, haga clic en **propiedades**. En el **propiedades** ventana, edite el **Color** propiedad.  
  
## <a name="Validate"></a> Valide el código con el diagrama  
 Una vez editado el diagrama, puede validarlo con el código manualmente en cualquier momento o automáticamente cada vez que se ejecute una compilación local o [!INCLUDE[esprbuild](../includes/esprbuild-md.md)].  
  
 Vea:  
  
- [Validar código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md)  
  
- [Incluir validación de capas en el proceso de compilación](#BuildValidation)  
  
## <a name="UpdateCode"></a> Actualice el código para que se ajuste a la nueva arquitectura  
 Normalmente, los errores aparecerán la primera vez que valide el código contra un diagrama de capas actualizado. Estos errores pueden tener varias causas:  
  
- Un artefacto se ha asignado a la capa equivocada. En este caso, mueva el artefacto.  
  
- Un artefacto, como por ejemplo una clase, usa otra clase de forma que hay conflictos con su arquitectura. En este caso, tiene que refactorizar el código para quitar la dependencia.  
  
  Para resolver estos errores, actualice el código hasta no aparezcan más errores durante la validación. Normalmente, este es un proceso iterativo. Para obtener más información acerca de estos errores, vea [validar código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md).  
  
> [!NOTE]
>  A medida que desarrolla o refactoriza el código, es posible que tenga nuevos artefactos que deba vincular al diagrama de capas. Sin embargo, esto podría no ser necesario, por ejemplo, si tiene capas que representan espacios de nombres existentes, y el nuevo código solo agrega más material a estos espacios de nombres.  
  
 Durante el proceso de desarrollo, puede que desee suprimir algunos de los conflictos notificados durante la validación. Por ejemplo, es posible que desee suprimir errores de los que ya se ha ocupado o que no son pertinentes para su escenario concreto. Cuando se suprime un error, conviene registrar un elemento de trabajo en [!INCLUDE[esprfound](../includes/esprfound-md.md)]. Para llevar a cabo esta tarea, vea [validar código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md).  
  
## <a name="BuildValidation"></a> Incluir validación de capas en el proceso de compilación  
 Para asegurarse de que los futuros cambios que se hagan en el código cumplen los requisitos de los diagramas de capas, incluya la validación de capas en el proceso de compilación estándar de la solución. Cuando otros miembros del equipo compilen la solución, cualquier diferencia entre las dependencias del código y el diagrama de capas se notificará como un error de compilación. Para obtener más información sobre cómo incluir la validación de capas en el proceso de compilación, véase [validar código con diagramas de capas](../modeling/validate-code-with-layer-diagrams.md).  
  
## <a name="see-also"></a>Vea también  
 [Diagramas de capas: Referencia](../modeling/layer-diagrams-reference.md)   
 [Crear diagramas de capas a partir del código](../modeling/create-layer-diagrams-from-your-code.md)
