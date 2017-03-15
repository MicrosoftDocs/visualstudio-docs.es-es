---
title: "Modelar el SDK de Visual Studio - lenguajes específicos de dominio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
ms.assetid: 17a531e2-1964-4a9d-84fd-6fb1b4aee662
caps.latest.revision: 77
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
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
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 86e70eb82260cdced1ee4d74965832fbc7fa56ab
ms.lasthandoff: 02/22/2017

---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Modelar el SDK de Visual Studio - Lenguajes específicos de dominio
Mediante el SDK de modelado para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], puede crear herramientas de desarrollo basado en modelo eficaz que puede integrar en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. De la misma manera, puede crear una o más definiciones de modelo e integrarlas en un conjunto de herramientas.  
  
 En el núcleo de MSDK se encuentra la definición de un modelo creado para representar conceptos del área de negocio. Puede rodear el modelo con varias herramientas, como una vista en forma de diagrama, la capacidad de generar código y otros artefactos, comandos para transformar el modelo y la capacidad de interactuar con código y otros objetos en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Al desarrollar el modelo, puede combinarlo con otros modelos y herramientas para formar un conjunto de herramientas eficaz centrado en el desarrollo.  
  
 MSDK permite desarrollar un modelo rápidamente en forma de lenguaje específico de dominio (DSL). Se comienza por usar un editor especializado para definir un esquema o sintaxis abstracta junto con una notación gráfica. A partir de esta definición, VMSDK genera:  
  
-   Una implementación del modelo con una API fuertemente tipada que se ejecuta en un almacén basado en transacciones.  
  
-   Un explorador basado en un árbol.  
  
-   Un editor gráfico en el que los usuarios pueden ver el modelo o las partes definidas de este.  
  
-   Métodos de serialización que guardan los modelos en XML legible.  
  
-   Medios para generar código de programa y otros artefactos mediante plantillas de texto.  
  
 Puede personalizar y ampliar todas estas características. Las extensiones se integran de modo que sigue siendo posible actualizar la definición de DSL y regenerar las características sin perder las extensiones.  
  
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
 
 [Blogs relacionados](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
  
 Para obtener información sobre técnicas avanzadas y solución de problemas, visite [foro de Visual Studio DSL aspecto herramientas extensibilidad del modelado](http://go.microsoft.com/fwlink/?LinkID=186074).  
  
## <a name="in-this-section"></a>En esta sección  
 [Introducción a los lenguajes específicos de dominio](../modeling/getting-started-with-domain-specific-languages.md)  
  
 [Introducción a los modelos, las clases y las relaciones](../modeling/understanding-models-classes-and-relationships.md)  
  
 [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)  
  
 [Personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md)  
  
 [La validación en los lenguajes específicos de dominio](../modeling/validation-in-a-domain-specific-language.md)  
  
 [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)  
  
 [Generar código a partir de lenguajes específicos de dominio](../modeling/generating-code-from-a-domain-specific-language.md)  
  
 [Descripción del código DSL](../modeling/understanding-the-dsl-code.md)  
  
 [Personalizar el almacenamiento de archivos y la serialización XML](../modeling/customizing-file-storage-and-xml-serialization.md)  
  
 [Implementar soluciones de lenguajes específicos de dominio](../modeling/deploying-domain-specific-language-solutions.md)  
  
 [Crear lenguajes específicos de dominio basados en Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)  
  
 [Crear lenguajes específicos de dominio basados en WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)  
  
 [Cómo: Ampliar el diseñador de lenguajes específicos de dominio](../modeling/how-to-extend-the-domain-specific-language-designer.md)  
  
 [Ediciones de Visual Studio compatibles con el SDK de visualización y modelado](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)  
  
 [Cómo: Migrar lenguajes específicos de dominio a una nueva versión](../modeling/how-to-migrate-a-domain-specific-language-to-a-new-version.md)  
  
 [Referencia de API para modelar el SDK de Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)

