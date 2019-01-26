---
title: Generar código a partir de lenguajes específicos de dominio
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: add2458989cc52d38ddefd80ce9f3310f0688f2b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54958581"
---
# <a name="generating-code-from-a-domain-specific-language"></a>Generar código a partir de lenguajes específicos de dominio
Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] proporciona una forma eficaz para generar código, documentos, archivos de configuración y otros artefactos de los datos representados en modelos. Uso de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], puede crear un conjunto de clases que representan los datos y puede escribir sus plantillas de texto en las clases cuyos nombres y propiedades reflejan dichos datos.

 Por ejemplo, Fabrikam tiene un archivo XML de los nombres de cliente y direcciones de correo electrónico. Los desarrolladores creación un modelo en el que el cliente es una clase, con las propiedades nombre y correo electrónico. Escriben varias plantillas de texto para procesar los datos, incluido este fragmento que genera una tabla de todos los clientes como parte de una página HTML:

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

 Cuando se procesa la base de datos de cliente, se lee el archivo XML en el almacén de modelos. Un *procesador de directivas*, creado mediante el uso de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], pone a disposición el código de la clase Customer en la plantilla de texto. Muchas plantillas de texto se pueden ejecutar en el mismo almacén.

 Las plantillas de texto son esenciales para [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. Se utilizan para generar el código fuente para los elementos del modelo de dominio, así como para el VSPackage y los controles que se usan para integrar las herramientas con Visual Studio.

 En esta sección se describe algunas de las formas de crear, modificar y depurar las plantillas de texto utilizadas en [!INCLUDE[dsl](../modeling/includes/dsl_md.md)].

## <a name="in-this-section"></a>En esta sección
 [Acceso a modelos a partir de plantillas de texto](../modeling/accessing-models-from-text-templates.md)

 Proporciona información básica sobre la que hace referencia a lenguajes específicos de dominio en las plantillas de texto.

 [Tutorial: Depurar una plantilla de texto que tiene acceso a un modelo](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)

 Describe cómo realizar la solución de problemas y depuración en una plantilla de texto que hace referencia a un lenguaje específico de dominio.

 [Tutorial: Conectar un Host a un procesador de directivas personalizadas](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)

 Describe cómo conectar un host personalizado a un procesador de directivas personalizadas.

 [El comando DslTextTransform](../modeling/the-dsltexttransform-command.md)

 Describe el archivo de comandos que se ejecuta el ejecutable TextTransform en la línea de comandos para las plantillas de texto que hacen referencia a lenguajes específicos de dominio.

## <a name="reference"></a>Referencia
 [Escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md)

 Proporciona la sintaxis de directivas de plantilla de texto y bloques de control.

## <a name="related-sections"></a>Secciones relacionadas
 [Generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

 Explica el proceso de transformación de plantillas de texto.

 [Generación de código en un proceso de compilación](../modeling/code-generation-in-a-build-process.md)

 Lea este tema si está generando los archivos desde un DSL en un servidor de compilación.