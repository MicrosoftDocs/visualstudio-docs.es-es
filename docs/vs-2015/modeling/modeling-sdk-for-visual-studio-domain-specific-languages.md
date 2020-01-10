---
title: 'SDK de modelado: lenguajes específicos de dominio | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
ms.assetid: 17a531e2-1964-4a9d-84fd-6fb1b4aee662
caps.latest.revision: 79
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0673f7511276799804dc327bab67637f3fc450b7
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850095"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Modelar el SDK de Visual Studio - Lenguajes específicos de dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con el SDK de modelado para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (MSDK), puede crear eficaces herramientas de desarrollo basadas en modelos que puede integrar en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Como ejemplo, las herramientas UML se crean mediante el MSDK. De la misma manera, puede crear una o más definiciones de modelo e integrarlas en un conjunto de herramientas.

 En el núcleo de MSDK se encuentra la definición de un modelo creado para representar conceptos del área de negocio. Puede rodear el modelo con varias herramientas, como una vista en forma de diagrama, la capacidad de generar código y otros artefactos, comandos para transformar el modelo y la capacidad de interactuar con código y otros objetos en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Al desarrollar el modelo, puede combinarlo con otros modelos y herramientas para formar un conjunto de herramientas eficaz centrado en el desarrollo.

 MSDK permite desarrollar un modelo rápidamente en forma de lenguaje específico de dominio (DSL). Se comienza por usar un editor especializado para definir un esquema o sintaxis abstracta junto con una notación gráfica. A partir de esta definición, VMSDK genera:

- Una implementación del modelo con una API fuertemente tipada que se ejecuta en un almacén basado en transacciones.

- Un explorador basado en un árbol.

- Un editor gráfico en el que los usuarios pueden ver el modelo o las partes definidas de este.

- Métodos de serialización que guardan los modelos en XML legible.

- Medios para generar código de programa y otros artefactos mediante plantillas de texto.

  Puede personalizar y ampliar todas estas características. Las extensiones se integran de modo que sigue siendo posible actualizar la definición de DSL y regenerar las características sin perder las extensiones.

## <a name="samples-and-the-latest-information"></a>Ejemplos e información más reciente
 [Descargar el SDK de modelado para Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48148)

 [Ejemplos](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples) del SDK de modelado para Visual Studio.

 Para obtener información sobre técnicas avanzadas y solución de problemas, visite [foro DSL de Visual Studio y herramientas de extensibilidad del modelado](https://social.msdn.microsoft.com/Forums/vstudio/en-US/home?forum=dslvsarchx).

## <a name="in-this-section"></a>Esta sección
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
