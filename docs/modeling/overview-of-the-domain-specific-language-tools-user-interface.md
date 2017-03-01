---
title: "Información general sobre el lenguaje específico de dominio herramientas de interfaz de usuario | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
ms.assetid: 81ae6b35-6819-41d0-953b-6b4ed81f9227
caps.latest.revision: 25
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d76ed4d14e7333678fcf927dfa1b2f21d8573be5
ms.lasthandoff: 02/22/2017

---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Información general sobre la interfaz de usuario de las herramientas de los lenguajes específicos de dominio
Cuando se abre una solución de herramientas de lenguajes específicos de dominio (herramientas DSL) en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la interfaz de usuario será similar a la siguiente imagen.  
  
 ![Diseñador DSL](../modeling/media/dsl_designer.png "dsl_designer")  
  
 La tabla siguiente explica cómo se usan las partes de la interfaz de usuario.  
  
|**Elemento**|**Definición**|  
|-----------------|--------------------|  
|Diagram|El diagrama muestra el modelo de dominio.<br /><br /> El diagrama tiene dos vertientes. Un lado define los tipos de los elementos en los modelos. El otro lado define cómo aparecerán los modelos en la pantalla.|  
|Cuadro de herramientas|Arrastre las herramientas del cuadro de herramientas para agregar clases de dominio y la forma de tipos al diagrama. Para agregar relaciones, conectores y asignaciones de formas, haga clic en la herramienta, haga clic en el nodo de origen en el diagrama y, a continuación, en el nodo de destino.|  
|Explorador de DSL|**Explorador de DSL** aparece cuando una definición de DSL es la ventana activa. Muestra el DSL como un árbol. Explorador de DSL permite editar características del modelo que no se muestran en el diagrama. Por ejemplo, puede agregar elementos de cuadro de herramientas y activar el proceso de validación mediante el **DSL Explorer**.|  
|Ventana Detalles de DSL|El **detalles de DSL** ventana muestra los elementos del modelo que permiten controlar cómo se muestran los elementos y cómo se copian y se eliminan los elementos de propiedades del dominio.<br /><br /> : De forma predeterminada, el **detalles de DSL** ventana aparece junto a la **lista de errores** y **salida** windows.|  
  
## <a name="the-domain-model-diagram"></a>El diagrama de modelo de dominio  
 El diagrama de modelo de dominio se divide en dos partes. Un lado del diagrama muestra los elementos y relaciones en el modelo. El otro lado muestra cómo se puede mostrar, el modelo e incluye las formas que se utilizan para mostrar los elementos y las propiedades del diagrama de modelo. En la siguiente imagen muestra los elementos del diagrama.  
  
 ![Diseñador DSL con swimlane](../modeling/media/dsl_desinger.png "dsl_desinger")  
  
 La tabla siguiente explican algunos de los elementos del diagrama de modelo de dominio.  
  
|**Término**|**Definición**|  
|--------------|--------------------|  
|Clase de dominio|Clases de dominio son los tipos de elementos de los modelos.<br /><br /> Una clase de dominio puede aparecer más de una vez en un diagrama, si es el destino de más de una relación.<br /><br /> Para agregar una clase de dominio, arrastre la herramienta de la clase de dominio desde el **herramientas** a la **clases y relaciones** lateral del diagrama.|  
|Relación de dominio|Las relaciones de dominio son los tipos de vínculos entre los elementos de los modelos.<br /><br /> Un *relación de incrustación* indica que el elemento de destino es propietario o incluido en el elemento de origen y aparece como una línea sólida. Cada elemento de un modelo debe ser el destino de una relación de incrustación, para que el modelo conforma un árbol. Un *referencia relación* indica un vínculo entre los elementos del modelo general y aparece como una línea discontinua. Cualquier elemento puede tener cualquier número de vínculos de referencia.<br /><br /> Crear una relación haciendo clic en la herramienta en el **herramientas**, haga clic en la clase de dominio de origen y, a continuación, haga clic en la clase de destino.|  
|Formas y conectores|Formas de especifican cómo se deben mostrar los elementos del modelo en un diagrama DSL., conectores líneas en un diagrama DSL que puede utilizarse para mostrar las relaciones.<br /><br /> Para crear un conector o una forma, arrastre la herramienta para la **elementos del diagrama** lateral del diagrama.|  
|Asignaciones de formas|Un mapa de forma aparece como una línea en el diagrama de modelo de dominio, vincular una forma a la clase de dominio que se muestra, o un conector para la relación de dominio que se muestra.|  
  
## <a name="see-also"></a>Vea también  
 [Información general de las herramientas de lenguajes específicos de dominio](../modeling/overview-of-domain-specific-language-tools.md)   
 [Glosario de herramientas de lenguajes específicos de dominio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)   
 [Personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md)
