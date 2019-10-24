---
title: Generar y configurar la aplicación a partir de modelos
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13d943b8d86bd9ca912816e0f19993959ca303c1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748399"
---
# <a name="generate-and-configure-your-app-from-models"></a>Generar y configurar la aplicación a partir de modelos
Puede generar o configurar partes de la aplicación a partir de un modelo.

 El modelo representa los requisitos de forma más directa que el código. Al derivar el comportamiento de la aplicación directamente desde el modelo, puede responder a los cambios en los requisitos de forma mucho más rápida y confiable que actualizando el código. Aunque es necesario algún trabajo inicial para configurar la derivación, este esfuerzo queda compensado si espera que los requisitos varíen o si piensa crear diversas variantes del producto.

## <a name="generating-the-code-of-your-application-from-a-model"></a>Generar el código de la aplicación a partir de un modelo
 La forma más sencilla de generar código es usar plantillas de texto. Puede generar código en la misma solución de Visual Studio en la que se mantiene el modelo. Para obtener más información, consulte:

- [Generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

- [Generar código a partir de lenguajes específicos de dominio](../modeling/generating-code-from-a-domain-specific-language.md)

  Este método es fácil de aplicar de forma incremental. Comience con una aplicación que funcione únicamente para un caso específico y elija algunas partes de la misma que quiera que varíen con respecto al modelo. Cambie los archivos de origen de esas partes para convertirlos en archivos de texto de plantilla (.tt). En este punto, los archivos de código fuente .cs se generarán automáticamente a partir de los archivos de plantilla, por lo que la aplicación funcionará igual que antes.

  Después, puede tomar una parte del código y reemplazarlo por una expresión de plantilla de texto que lea el modelo y genere esa parte del archivo de origen. Al menos un valor del modelo debe generar el código fuente original para que pueda ejecutar la aplicación y funcione igual que antes. Después de probar los valores de modelo diferente, puede pasar a insertar expresiones de plantilla en otra parte del código.

  Este método incremental significa que la generación de código es generalmente un enfoque de bajo riesgo. Las aplicaciones resultantes suelen tener un rendimiento casi tan bueno como las escritas a mano.

  Pero si empieza con una aplicación existente, podría encontrarse con que es necesaria una gran cantidad de refactorización para separar los distintos comportamientos que se rigen por el modelo, de modo que puedan modificarse independientemente. Se recomienda evaluar este aspecto de la aplicación al calcular el costo del proyecto.

## <a name="configuring-your-application-from-a-model"></a>Configuración de la aplicación a partir de un modelo
 Si quiere variar el comportamiento de la aplicación en tiempo de ejecución, no podrá usar la generación de código, que crea código fuente antes de compilar la aplicación. En su lugar, puede diseñar la aplicación para leer el modelo y modificar su comportamiento en consecuencia. Para obtener más información, consulte:

- [Cómo: Abrir un modelo desde un archivo en el código del programa](../modeling/how-to-open-a-model-from-file-in-program-code.md)

  Este método también puede aplicarse de forma incremental, pero requiere más trabajo al principio. Deberá escribir el código que leerá el modelo y configurar un marco que permita que sus valores sean accesibles a las partes variables. Hacer que las partes variables sean genéricas es más costoso que generar código.

  El rendimiento de una aplicación genérica normalmente es inferior al de sus homólogas específicas. Si el rendimiento es crucial, el plan de proyecto debe incluir una evaluación de este riesgo.

## <a name="developing-a-derived-application"></a>Desarrollar una aplicación derivada
 Las siguientes pautas generales podrían resultarle de utilidad:

- **Específico de inicio y luego generalizar.** Escriba en primer lugar una versión específica de la aplicación. Esta versión debería funcionar con un conjunto de condiciones. Cuando esté satisfecho con su funcionamiento, puede hacer que algunas de ellas deriven de un modelo. Amplíe gradualmente los elementos derivados.

     Por ejemplo, diseñe un sitio web que tenga un conjunto específico de páginas web antes de diseñar una aplicación web que presente las páginas que se definen en un modelo.

- **Modelar los aspectos variantes.** Identifique los aspectos variables, ya sea entre implementaciones o a lo largo del tiempo, a medida que los requisitos cambian. Estos son los aspectos que se deben derivar de un modelo.

     Por ejemplo, si el conjunto de páginas web y vínculos entre ellos cambian, pero el estilo y el formato de las páginas siempre son los mismos, el modelo debe describir los vínculos, pero no es necesario describir el formato de las páginas.

- **Aspectos independientes.** Si los aspectos de las variables pueden dividirse en zonas independientes, use modelos independientes para cada área. Con ModelBus, puede definir las operaciones que afectan a los dos modelos y las restricciones entre ellos.

     Por ejemplo, use un modelo para definir la navegación entre las páginas web y un modelo diferente para definir el diseño de las páginas.

- **Modelar el requisito, no la solución.** Diseñe el modelo para que describa los requisitos del usuario. Por el contrario, no diseñe la notación de acuerdo con los aspectos variables de la implementación.

     Por ejemplo, el modelo de navegación web debe representar páginas web e hipervínculos entre ellos. El modelo de navegación web no debe representar fragmentos de HTML o clases de la aplicación.

- **¿Generar o interpretar?** Si los requisitos de una implementación determinada cambian con poca frecuencia, genere código de programa a partir del modelo. Si los requisitos pueden cambiar con frecuencia o coexistir en más de una variante de la misma implementación, escriba la aplicación de modo que pueda leer e interpretar un modelo.

     Por ejemplo, si usa el modelo de sitio web para desarrollar una serie de sitios web diferentes y instalados por separado, debe generar el código del sitio a partir del modelo. Pero se usa el modelo para controlar un sitio que cambia cada día, es mejor escribir un servidor Web que lea el modelo y presente el sitio según corresponda.

- **¿UML o DSL?** Estudie la posibilidad de crear la notación de modelado usando estereotipos para ampliar UML. Defina un DSL si ningún diagrama UML puede ajustarse al propósito, pero intente no romper la semántica estándar de UML.

     Por ejemplo, un diagrama de clases UML es una colección de cuadros y flechas; con esta notación, en teoría, es posible definir cualquier cosa. Tenga en cuenta que no le recomendamos usar el diagrama de clases, excepto para describir un conjunto de tipos. Por ejemplo, puede adaptar los diagramas de clases para describir los distintos tipos de páginas Web.

## <a name="see-also"></a>Vea también

- [Generar código a partir de lenguajes específicos de dominio](../modeling/generating-code-from-a-domain-specific-language.md)
- [Cómo: Abrir un modelo desde un archivo en el código del programa](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [Generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)