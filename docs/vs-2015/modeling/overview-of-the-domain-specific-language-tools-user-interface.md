---
title: Información general sobre la interfaz de usuario de las Herramientas del lenguaje específico de dominio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: overview
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
ms.assetid: 81ae6b35-6819-41d0-953b-6b4ed81f9227
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c75032649e76bb927011c3bb0a34bbcd0a11c55e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65674963"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Información general sobre la interfaz de usuario de las herramientas de los lenguajes específicos de dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando se abre una solución de las Herramientas del lenguaje específico de dominio (Herramientas DSL) en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], la interfaz de usuario será algo parecido a esta imagen.  
  
 ![diseñador dsl](../modeling/media/dsl-designer.png "dsl_designer")  
  
 En esta tabla se explica cómo se usan las distintas partes de la interfaz de usuario.  
  
|**Element**|**Definición**|  
|-----------------|--------------------|  
|Diagram|El diagrama muestra el modelo de dominio.<br /><br /> El diagrama tiene dos lados. Uno de los lados define los tipos de elementos en los modelos. El otro lado define cómo aparecen los modelos en la pantalla.|  
|Cuadro de herramientas|Arrastre herramientas del cuadro de herramientas para agregar clases de dominio y tipos de formas al diagrama. Para agregar relaciones, conectores y asignaciones de formas, haga clic en la herramienta, después haga clic en el nodo de origen en el diagrama y luego en el nodo de destino.|  
|Explorador de DSL|El **Explorador de DSL** aparece cuando una definición de DSL es la ventana activa. Muestra el DSL como un árbol. El Explorador de DSL permite editar las características del modelo que no se muestran en el diagrama. Por ejemplo, puede agregar elementos del cuadro de herramientas y activar el proceso de validación mediante el **Explorador de DSL**.|  
|Ventana Detalles de DSL|La ventana **Detalles de DSL** muestra las propiedades de los elementos del modelo de dominio que le permiten controlar cómo se muestran los elementos y cómo se copian y se eliminan los elementos.<br /><br /> De forma predeterminada, la ventana **Detalles de DSL** aparece junto a las ventanas **Lista de errores** y **Resultados**.|  
  
## <a name="the-domain-model-diagram"></a>Diagrama Modelo de dominio  
 El diagrama Modelo de dominio se divide en dos partes. Una parte del diagrama muestra los elementos y relaciones en el modelo. La otra parte muestra cómo se va a mostrar el modelo e incluye las formas que se usan para mostrar los elementos y las propiedades del diagrama de modelo. En esta imagen se muestran los elementos del diagrama.  
  
 ![diseñador dsl con carril](../modeling/media/dsl-desinger.png "dsl_desinger")  
  
 En esta tabla se explican algunos de los elementos del diagrama de modelo de dominio.  
  
|**Término**|**Definición**|  
|--------------|--------------------|  
|Clase de dominio|Las clases de dominio son los tipos de elementos de los modelos.<br /><br /> Una clase de dominio puede aparecer más de una vez en un diagrama, si es el destino de más de una relación.<br /><br /> Para agregar una clase de dominio, arrastre la herramienta de la clase de dominio desde el **Cuadro de herramientas** a la parte **Clases y relaciones** del diagrama.|  
|Relación de dominio|Las relaciones de dominio son los tipos de vínculos entre los elementos de los modelos.<br /><br /> Una *relación de inclusión* indica que el elemento de destino es propiedad del elemento de origen o está incluido en él y aparece como una línea sólida. Todos los elementos de un modelo deben ser el destino de una relación de inclusión para que el modelo forme un árbol. Una *relación de referencia* indica un vínculo general entre los elementos del modelo general y aparece como una línea discontinua. Cualquier elemento puede tener cualquier número de vínculos de referencia.<br /><br /> Cree una relación haciendo clic en la herramienta en el **Cuadro de herramientas**. Después, haga clic en la clase de dominio de origen y luego en la clase de destino.|  
|Formas y conectores|Las formas especifican cómo deben mostrarse los elementos del modelo en un diagrama de DSL. Los conectores especifican las líneas en un diagrama de DSL que se pueden usar para mostrar las relaciones.<br /><br /> Para crear una forma o un conector, arrastre la herramienta a la parte **Elementos de diagrama** del diagrama.|  
|Asignaciones de formas|Un mapa de formas aparece como una línea en el diagrama del modelo de dominio y vincula una forma a la clase de dominio que se muestra, o un conector a la relación de dominio que se muestra.|  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre las Herramientas del lenguaje específico de dominio](../modeling/overview-of-domain-specific-language-tools.md)   
 [Glosario de las Herramientas del lenguaje específico de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)   
 [Personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md)
