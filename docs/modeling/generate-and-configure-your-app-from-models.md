---
title: "Generar y configurar la aplicación de modelos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4dc8f572-a09e-4d19-a92d-f1df383e728b
caps.latest.revision: "7"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.workload: multiple
ms.openlocfilehash: a08d7a94dcd512f650564a07a1e6784bffe8c45e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="generate-and-configure-your-app-from-models"></a>Generar y configurar la aplicación a partir de modelos
Puede generar o configurar partes de la aplicación a partir de un modelo.
  
 El modelo representa los requisitos de forma más directa que el código. Al derivar el comportamiento de la aplicación directamente desde el modelo, puede responder a los cambios en los requisitos de forma mucho más rápida y confiable que actualizando el código. Aunque es necesario algún trabajo inicial para configurar la derivación, este esfuerzo queda compensado si espera que los requisitos varíen o si piensa crear diversas variantes del producto.  
  
## <a name="generating-the-code-of-your-application-from-a-model"></a>Generar el código de la aplicación a partir de un modelo  
 La forma más sencilla de generar código es usar plantillas de texto. Puede generar código en el mismo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solución en el que mantener el modelo. Para obtener más información, consulte:  
  
-   [Generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
-   [Generar código a partir de lenguajes específicos de dominio](../modeling/generating-code-from-a-domain-specific-language.md)  
  
 Este método es fácil de aplicar de forma incremental. Comience con una aplicación que funcione únicamente para un caso específico y elija algunas partes de la misma que quiera que varíen con respecto al modelo. Cambie los archivos de origen de esas partes para convertirlos en archivos de texto de plantilla (.tt). En este punto, los archivos de código fuente .cs se generarán automáticamente a partir de los archivos de plantilla, por lo que la aplicación funcionará igual que antes.  
  
 Después, puede tomar una parte del código y reemplazarlo por una expresión de plantilla de texto que lea el modelo y genere esa parte del archivo de origen. Al menos un valor del modelo debe generar el código fuente original para que pueda ejecutar la aplicación y funcione igual que antes. Después de probar los valores de modelo diferente, puede pasar a insertar expresiones de plantilla en otra parte del código.  
  
 Este método incremental significa que la generación de código es generalmente un enfoque de bajo riesgo. Las aplicaciones resultantes suelen tener un rendimiento casi tan bueno como las escritas a mano.  
  
 Pero si empieza con una aplicación existente, podría encontrarse con que es necesaria una gran cantidad de refactorización para separar los distintos comportamientos que se rigen por el modelo, de modo que puedan modificarse independientemente. Se recomienda evaluar este aspecto de la aplicación al calcular el costo del proyecto.  
  
## <a name="configuring-your-application-from-a-model"></a>Configuración de la aplicación a partir de un modelo  
 Si quiere variar el comportamiento de la aplicación en tiempo de ejecución, no podrá usar la generación de código, que crea código fuente antes de compilar la aplicación. En su lugar, puede diseñar la aplicación para leer el modelo y para modificar su comportamiento en consecuencia. Para obtener más información, consulte:  
  
-   [Cómo: Abrir un modelo desde un archivo en el código del programa](../modeling/how-to-open-a-model-from-file-in-program-code.md)  
  
 Este método también puede aplicarse de forma incremental, pero requiere más trabajo al principio. Deberá escribir el código que leerá el modelo y configurar un marco que permita que sus valores sean accesibles a las partes variables. Hacer que las partes variables sean genéricas es más costoso que generar código.  
  
 El rendimiento de una aplicación genérica normalmente es inferior al de sus homólogas específicas. Si el rendimiento es crucial, el plan de proyecto debe incluir una evaluación de este riesgo.  
  
## <a name="developing-a-derived-application"></a>Desarrollar una aplicación derivada  
 Las siguientes pautas generales podrían resultarle de utilidad:  
  
-   **Iniciar específico, a continuación, generalize.** Escriba en primer lugar una versión específica de la aplicación. Esta versión debería funcionar con un conjunto de condiciones. Cuando esté satisfecho con su funcionamiento, puede hacer que algunas de ellas deriven de un modelo. Amplíe gradualmente los elementos derivados.  
  
     Por ejemplo, puede diseñar un sitio web que tiene un conjunto específico de las páginas web antes de diseñar una aplicación web que presenta las páginas que se definen en un modelo.  
  
-   **Los aspectos de la variantes del modelo.** Identifique los aspectos variables, ya sea entre implementaciones o a lo largo del tiempo, a medida que los requisitos cambian. Estos son los aspectos que se deben derivar de un modelo.  
  
     Por ejemplo, si el conjunto de páginas web y los vínculos entre ellos cambian pero el estilo y el formato de las páginas es siempre el mismo, el modelo debe describir los vínculos, pero no tiene que describir el formato de las páginas.  
  
-   **Preocupaciones independientes.** Si los aspectos de las variables pueden dividirse en zonas independientes, use modelos independientes para cada área. Con ModelBus, puede definir las operaciones que afectan a los dos modelos y las restricciones entre ellos.  
  
     Por ejemplo, puede usar un modelo para definir la navegación entre las páginas web y un modelo diferente para definir el diseño de las páginas.
  
-   **Modelar el requisito, no la solución.** Diseñar el modelo para que se describen los requisitos de usuario. Por el contrario, no diseñe la notación de acuerdo con los aspectos variables de la implementación.  
  
     Por ejemplo, el modelo de exploración web debe representar las páginas web y los hipervínculos entre ellas. El modelo de exploración web no debería representar fragmentos de HTML o clases de la aplicación.  
  
-   **Generar o interpretar?** Si los requisitos de una implementación determinada cambian con poca frecuencia, genere código de programa a partir del modelo. Si los requisitos pueden cambiar con frecuencia o coexistir en más de una variante de la misma implementación, escriba la aplicación de modo que pueda leer e interpretar un modelo.  
  
     Por ejemplo, si usa el modelo del sitio web para desarrollar una serie de sitios web diferentes e instalados por separado, es recomendable que genere el código del sitio a partir del modelo. No obstante, si usa el modelo para controlar un sitio que cambia a diario, es preferible escribir en servidor web que lea el modelo y presente el sitio según corresponda.  
  
-   **¿UML o DSL?** Estudie la posibilidad de crear la notación de modelado usando estereotipos para ampliar UML. Defina un DSL si ningún diagrama UML puede ajustarse al propósito, pero intente no romper la semántica estándar de UML.  
  
     Por ejemplo, un diagrama de clases UML es una colección de cuadros y flechas; con esta notación, en teoría, es posible definir cualquier cosa. Tenga en cuenta que no le recomendamos usar el diagrama de clases, excepto para describir un conjunto de tipos. Por ejemplo, podría adaptar los diagramas de clases para describir distintos tipos de páginas web.  
  
## <a name="see-also"></a>Vea también  
 [Generar código a partir de un lenguaje específico de dominio](../modeling/generating-code-from-a-domain-specific-language.md)   
 [Cómo: abrir un modelo de archivo en el código de programa](../modeling/how-to-open-a-model-from-file-in-program-code.md)   
 [Generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)