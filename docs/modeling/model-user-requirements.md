---
title: Modelar los requisitos de usuario | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- requirements
- stories
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1401328b53f03d6ff1121e93ac7e56ebba0e585e
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="model-user-requirements"></a>Requisitos del usuario de modelos

Con Visual Studio, es más fácil entender, analizar y comunicar las necesidades de los usuarios a través de diagramas sobre sus actividades, así como la importancia del sistema para ayudarles a lograr sus objetivos. Un modelo de requisitos es un conjunto de estos diagramas, cada uno de los cuales se centra en un aspecto diferente de las necesidades de los usuarios. Para ver una demostración en vídeo, consulte [Modeling the Business Domain](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-3-Modeling-the-Business-Domain/)(Crear modelos del ámbito empresarial).  
  
 Para ver qué versiones de Visual Studio admite cada tipo de modelo, consulte [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Un modelo de requisitos le ayuda a:  
  
-   Centrarse en el comportamiento externo del sistema, independientemente de su diseño interno.  
  
-   Describir las necesidades de los usuarios y otras partes interesadas con mucha menos ambigüedad que con el lenguaje natural.  
  
-   Definir un glosario de términos coherente que puedan usar los usuarios, los desarrolladores y los evaluadores.  
  
-   Reducir los vacíos y las incoherencias de los requisitos.  
  
-   Reducir el trabajo necesario para responder a los cambios de los requisitos.  
  
-   Planear el orden en el que se van a desarrollar las características.  
  
-   Usar los modelos como base para las pruebas del sistema, estableciendo una relación inequívoca entre las pruebas y los requisitos. Si cambian los requisitos, esta relación le ayudará a actualizar las pruebas correctamente. Esto garantiza que el sistema cumple los requisitos nuevos.  
  
 Un modelo de requisitos proporciona el máximo beneficio si lo usa para centrar las conversaciones con los usuarios o sus representantes y vuelve a visitarlo al principio de cada iteración. No es necesario completarlo detalladamente antes de escribir el código. Una aplicación parcialmente operativa, aunque esté muy simplificada, suele constituir la base más estimulante para tratar los requisitos con los usuarios. El modelo es un método eficaz para resumir los resultados de estas conversaciones. Para obtener más información, consulte [usar modelos en el proceso de desarrollo](../modeling/use-models-in-your-development-process.md).  
  
> [!NOTE]
> En estos temas, "sistema" hace referencia al sistema o la aplicación que está desarrollando. Podría ser una colección grande de muchos componentes de hardware y software, una sola aplicación o un componente de software incluido en un sistema de mayor tamaño. En cada caso, el modelo de requisitos describe el comportamiento que es visible desde fuera del sistema, ya sea a través de una API o interfaz de usuario.  
  
## <a name="common-tasks"></a>Tareas comunes

Puede crear varias vistas diferentes de los requisitos de los usuarios.  Cada vista proporciona un tipo determinado de información.  Al crear estas vistas, es mejor pasar con frecuencia de una a otra. Puede empezar desde cualquier vista.  
  
|Diagrama o documento|Qué se describe en un modelo de requisitos|Sección|  
|-------------------------|-----------------------------------------------|-------------|  
|Diagrama de clases conceptuales|Glosario de los tipos que se usan para describir los requisitos; los tipos visibles en la interfaz del sistema.||  
|Otros documentos o elementos de trabajo|Criterios de rendimiento, seguridad, facilidad de uso y confiabilidad.|[Describir los requisitos de calidad de servicio](#QoSRequirements)|  
|Otros documentos o elementos de trabajo|Restricciones y reglas no específicas para un determinado caso de uso|[Mostrar reglas de negocio](#BusinessRules)|  
  
 Observe que la mayoría de los tipos de diagramas se pueden usar para otros fines. Para obtener información general de tipos de diagramas, vea [crear modelos para la aplicación](../modeling/create-models-for-your-app.md).
  
##  <a name="BusinessRules"></a> Showing Business Rules

Una regla de negocio es un requisito que no está asociado a ningún caso de uso determinado y que se debe observar en todo el sistema.  
  
 Muchas reglas de negocio son restricciones en las relaciones entre las clases conceptuales. Puede escribir estos *estático ** reglas de negocios* como comentarios asociados con las clases pertinentes en un diagrama de clases conceptuales. Por ejemplo:  
  
 ![Regla en comentario adjunto a la clase Order. ] (../modeling/media/uml_reqmcd2.png "UML_ReqmCD2")  
  
 Las*reglas de negocio dinámicas* restringen las secuencias de eventos permitidas. Por ejemplo, puede usar un diagrama de secuencia o actividades para mostrar que un usuario debe iniciar sesión antes de realizar otras operaciones en el sistema.  
  
 Pero muchas reglas dinámicas se pueden aplicar de una forma más eficaz y genérica al reemplazarlas por reglas estáticas. Por ejemplo, puede agregar un atributo booleano "Logged In" a una clase en el modelo de clases conceptuales. Agregaría "Logged In" como condición posterior del caso de uso de inicio de sesión y lo agregaría como condición previa de la mayoría de los demás casos de uso. Este enfoque le permite evitar definir todas las combinaciones de secuencias de eventos posibles. También es más flexible cuando necesita agregar nuevos casos de uso al modelo.  
  
 Observe que la opción es sobre la definición de los requisitos, y que esto es independiente de la implementación de los requisitos en el código del programa.  
  
 Para obtener más información, consulte los temas siguientes:  
  
|Más información|Leer|  
|--------------------|----------|  
|Cómo desarrollar código que cumple las reglas de negocio|[Modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md)|  
  
##  <a name="QoSRequirements"></a> Describing Quality of Service Requirements

Existen varias categorías de requisito de calidad de servicio. Entre esos tipos se incluyen los siguientes:  
  
-   Rendimiento  
  
-   Seguridad  
  
-   Facilidad de uso  
  
-   Confiabilidad  
  
-   Solidez  
  
Puede incluir algunos de estos requisitos en las descripciones de casos de uso concretos. Otros requisitos no son específicos de los casos de uso y resulta más eficaz incluirlos en un documento independiente. Cuando sea posible, resulta útil ajustarse al vocabulario definido en el modelo de requisitos. En el ejemplo siguiente, observe que las principales palabras que se usan en el requisito son los títulos de los actores, los casos de uso y las clases de las ilustraciones anteriores:

Si un restaurante elimina un elemento del menú mientras un cliente pide un menú, cualquier elemento del pedido que haga referencia a ese elemento del menú se mostrará de color rojo.

Vea [modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md) para obtener información sobre cómo desarrollar código que cumple los requisitos de servicio de calidad de.

## <a name="see-also"></a>Vea también

[Usar modelos en el proceso de desarrollo](../modeling/use-models-in-your-development-process.md)  
[Modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md)
