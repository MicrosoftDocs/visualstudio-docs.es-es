---
title: Generar código a partir de un lenguaje específico de dominio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 32cafb9e68fc2535ed3b570022a59d284f4c4cae
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666110"
---
# <a name="generating-code-from-a-domain-specific-language"></a>Generar código a partir de lenguajes específicos de dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft [!INCLUDE[dsl](../includes/dsl-md.md)] proporciona una manera eficaz de generar código, documentos, archivos de configuración y otros artefactos a partir de los datos representados en los modelos. Con [!INCLUDE[dsl](../includes/dsl-md.md)], puede crear un conjunto de clases que representen los datos y puede escribir sus plantillas de texto en clases cuyos nombres y propiedades reflejen los datos.

 Por ejemplo, Fabrikam tiene un archivo XML de nombres de clientes y direcciones de correo electrónico. Sus desarrolladores crean un modelo en el que el cliente es una clase, con el nombre de las propiedades y el correo electrónico. Escriben varias plantillas de texto para procesar los datos, incluido este fragmento que genera una tabla de todos los clientes como parte de una página HTML:

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

 Cuando se procesa la base de datos del cliente, el archivo XML se lee en el almacén de modelos. Un *procesador de directivas*, creado mediante [!INCLUDE[dsl](../includes/dsl-md.md)], hace que la clase Customer esté disponible para el código de la plantilla de texto. Muchas plantillas de texto se pueden ejecutar en el mismo almacén.

 Las plantillas de texto son esenciales para [!INCLUDE[dsl](../includes/dsl-md.md)]. Se usan para generar el código fuente para los elementos del modelo de dominio, así como para el VSPackage y los controles que se usan para integrar las herramientas con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 En esta sección se describen algunas de las formas de crear, modificar y depurar plantillas de texto que se usan en [!INCLUDE[dsl](../includes/dsl-md.md)].

## <a name="in-this-section"></a>En esta sección
 [Acceso a modelos a partir de plantillas de texto](../modeling/accessing-models-from-text-templates.md)

 Proporciona información básica sobre cómo hacer referencia a lenguaje específico de dominio en plantillas de texto.

 [Tutorial: Depurar una plantilla de texto que tiene acceso a un modelo](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)

 Describe cómo solucionar problemas y depurar en una plantilla de texto que hace referencia a un lenguaje específico del dominio.

 [Tutorial: Conectar un host a un procesador de directivas personalizadas](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)

 Describe cómo conectar un host personalizado a un procesador de directivas generado.

 [El comando DslTextTransform](../modeling/the-dsltexttransform-command.md)

 Describe el archivo de comandos que ejecuta el ejecutable de TextTransform en la línea de comandos para las plantillas de texto que hacen referencia a lenguajes específicos de dominio.

## <a name="reference"></a>Referencia
 [Escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md)

 Proporciona la sintaxis de las directivas de plantilla de texto y los bloques de control.

## <a name="related-sections"></a>Secciones relacionadas
 [Generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

 Explica el proceso de transformación de plantillas de texto.

 [Generación de código en un proceso de compilación](../modeling/code-generation-in-a-build-process.md)

 Lea este tema si va a generar archivos a partir de un DSL en un servidor de compilación.
