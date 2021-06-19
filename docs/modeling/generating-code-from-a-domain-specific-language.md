---
title: Generar código a partir de lenguajes específicos de dominio
description: Obtenga información sobre Domain-Specific Language Tools proporciona una manera eficaz de generar código, documentos y otros artefactos a partir de datos representados en modelos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6eee4fe2400bac1534bdc9c208fa60d9af8d3cfd
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388846"
---
# <a name="generating-code-from-a-domain-specific-language"></a>Generar código a partir de lenguajes específicos de dominio

Microsoft proporciona una manera eficaz de generar código, documentos, archivos de configuración y otros artefactos a partir [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] de datos representados en modelos. Con , puede crear un conjunto de clases que representen los datos y escribir las plantillas de texto en clases cuyos nombres y propiedades [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] reflejen los datos.

Por ejemplo, Fabrikam tiene un archivo XML de nombres de cliente y direcciones de correo electrónico. Sus desarrolladores crean un modelo en el que Customer es una clase, con el nombre de las propiedades y el correo electrónico. Escriben varias plantillas de texto para procesar los datos, incluido este fragmento que genera una tabla de todos los clientes como parte de una página HTML:

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

Cuando se procesa la base de datos del cliente, el archivo XML se lee en el almacén de modelos. Un *procesador de directivas*, creado mediante , hace que la clase Customer esté disponible para el código de la plantilla de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] texto. Muchas plantillas de texto se pueden ejecutar en el mismo almacén.

Las plantillas de texto son esenciales para [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] . Se usan para generar el código fuente para los elementos del modelo de dominio, así como para el VSPackage y los controles que se usan para integrar las herramientas con Visual Studio.

En esta sección se de abordan algunas de las formas de crear, modificar y depurar plantillas de texto usadas en [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] .

## <a name="in-this-section"></a>En esta sección

[Acceso a modelos desde plantillas de texto](../modeling/accessing-models-from-text-templates.md)\
Proporciona información básica sobre cómo hacer referencia a un lenguaje específico del dominio en las plantillas de texto.

[Tutorial: Depurar una plantilla de texto que tiene acceso a un modelo](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)\
Describe cómo solucionar problemas y depurar en una plantilla de texto que hace referencia a un lenguaje específico del dominio.

[Tutorial: Conectar un host a un procesador de directivas generado](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)\
Describe cómo conectar un host personalizado a un procesador de directivas generado.

[El comando DslTextTransform](../modeling/the-dsltexttransform-command.md)\
Describe el archivo de comandos que ejecuta el ejecutable TextTransform en la línea de comandos para las plantillas de texto que hacen referencia a lenguajes específicos del dominio.

## <a name="reference"></a>Referencia

[Escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md)\
Proporciona la sintaxis de directivas de plantilla de texto y bloques de control.

## <a name="related-sections"></a>Secciones relacionadas

[Generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)\
Explica el proceso de transformación de la plantilla de texto.

[Generación de código en un proceso de compilación](../modeling/code-generation-in-a-build-process.md)\
Lea este tema si va a generar archivos desde un DSL en un servidor de compilación.
