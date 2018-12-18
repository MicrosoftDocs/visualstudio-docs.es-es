---
title: Información general sobre la interfaz de usuario de las herramientas de los lenguajes específicos de dominio
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: d54ba969e06f3bd951556f8d8f347977419fc015
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966497"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Información general sobre la interfaz de usuario de las herramientas de los lenguajes específicos de dominio
Primera vez que abra una solución de herramientas de lenguajes específicos de dominio (herramientas DSL) en Visual Studio, la interfaz de usuario será similar a la siguiente imagen.

 ![diseñador dsl](../modeling/media/dsl_designer.png)

 En la tabla siguiente se explica cómo se usan las partes de la interfaz de usuario.

|**Element**|**Definición**|
|-|-|
|Diagram|El diagrama muestra el modelo de dominio.<br /><br /> El diagrama tiene dos lados. Uno de los lados define los tipos de los elementos en los modelos. El otro lado define cómo aparecen los modelos en la pantalla.|
|Cuadro de herramientas|Arrastre las herramientas del cuadro de herramientas para agregar clases de dominio y dar forma a los tipos al diagrama. Para agregar asignaciones de formas, conectores y las relaciones, haga clic en la herramienta, haga clic en el nodo de origen en el diagrama y, a continuación, en el nodo de destino.|
|Explorador de DSL|**Explorador de DSL** aparece cuando una definición de DSL es la ventana activa. Muestra el DSL como un árbol. Explorador de DSL permite editar las características del modelo que no se muestran en el diagrama. Por ejemplo, puede agregar elementos de cuadro de herramientas y activar el proceso de validación mediante el **DSL Explorer**.|
|Ventana Detalles de DSL|El **detalles de DSL** ventana muestra los elementos del modelo que le permiten controlar cómo se muestran los elementos, y cómo se copian y se eliminan los elementos de propiedades del dominio.<br /><br /> : De forma predeterminada, el **detalles de DSL** ventana aparece junto a la **lista de errores** y **salida** windows.|

## <a name="the-domain-model-diagram"></a>El diagrama del modelo de dominio
 El diagrama del modelo de dominio se divide en dos partes. Un lado del diagrama muestra los elementos y relaciones en el modelo. El otro lado, muestra cómo el modelo es que se mostrará e incluye las formas que se usan para mostrar los elementos y las propiedades del diagrama de modelo. La siguiente imagen muestra los elementos del diagrama.

 ![diseñador dsl con carril (cal](../modeling/media/dsl_desinger.png)

 En la tabla siguiente se explica algunos de los elementos del diagrama de modelo de dominio.

|**Término**|**Definición**|
|-|-|
|Clase de dominio|Clases de dominio son los tipos de elementos de los modelos.<br /><br /> Una clase de dominio puede aparecer más de una vez en un diagrama, si es el destino de más de una relación.<br /><br /> Para agregar una clase de dominio, arrastre la herramienta de la clase de dominio desde el **cuadro de herramientas** a la **clases y relaciones** en paralelo del diagrama.|
|Relación de dominio|Las relaciones de dominio son los tipos de vínculos entre los elementos de los modelos.<br /><br /> Un *relación de incrustación* indica que el elemento de destino es propietario o contiene el elemento de origen y aparece como una línea sólida. Todos los elementos de un modelo deben ser el destino de una relación de incrustación, para que el modelo conforma un árbol. Un *relación de referencia* indica un vínculo entre los elementos del modelo general y aparece como una línea discontinua. Cualquier elemento puede tener cualquier número de vínculos de referencia.<br /><br /> Crear una relación, haga clic en la herramienta en el **cuadro de herramientas**, al hacer clic en la clase de dominio de origen y, a continuación, haga clic en la clase de destino.|
|Formas y conectores|Formas de especifican cómo deben mostrarse los elementos del modelo en un diagrama DSL., conectores líneas en un diagrama DSL que se puede usar para mostrar las relaciones.<br /><br /> Para crear una forma o conector, arrastre la herramienta para la **elementos del diagrama** en paralelo del diagrama.|
|Asignaciones de formas|Un mapa de formas aparece como una línea en el diagrama del modelo de dominio, la vinculación de una forma a la clase de dominio que muestra, o un conector a la relación de dominio que muestra.|

## <a name="see-also"></a>Vea también

- [Información general sobre las herramientas de los lenguajes específicos de dominio](../modeling/overview-of-domain-specific-language-tools.md)
- [Glosario de las herramientas de lenguajes específicos de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
- [Personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md)