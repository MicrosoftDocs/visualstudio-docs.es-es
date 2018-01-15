---
title: "Generar código a partir de un lenguaje específico de dominio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ebfb92bb316cc8c4dc192192c1a00ea42420bcff
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="generating-code-from-a-domain-specific-language"></a>Generar código a partir de lenguajes específicos de dominio
Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] proporciona una forma eficaz para generar código, documentos, archivos de configuración y otros artefactos de datos representados en los modelos. Usar [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], puede crear un conjunto de clases que representan los datos y puede escribir las plantillas de texto en las clases cuyos nombres y propiedades reflejan esos datos.  
  
 Por ejemplo, Fabrikam tiene un archivo XML de los nombres de cliente y direcciones de correo electrónico. Los programadores crear un modelo en el que el cliente es una clase con propiedades nombre y correo electrónico. Escriben varias plantillas de texto para procesar los datos, incluido este fragmento que genera una tabla de todos los clientes como parte de una página HTML:  
  
```  
<table>  
<# foreach (Customer c in ContactList) {  #>  
  <tr><td> <#= c.FullName #> </td>   
      <td> <#= c.EmailAddress #> </td> </tr>  
<# } #>  </table>  
```  
  
 Cuando se procesa la base de datos de cliente, se lee el archivo XML en el almacén de modelos. A *procesador de directivas*, creado mediante el uso de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], hace que la clase Customer disponible para el código de la plantilla de texto. Muchas plantillas de texto se pueden ejecutar en el mismo almacén.  
  
 Plantillas de texto son esenciales para [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. Se usan para generar el código fuente para los elementos del modelo de dominio, así como para el VSPackage y los controles que se usan para integrar las herramientas con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 En esta sección se describe algunas de las formas de crear, modificar y depurar plantillas de texto que se utilizan en [!INCLUDE[dsl](../modeling/includes/dsl_md.md)].  
  
## <a name="in-this-section"></a>En esta sección  
 [Acceso a modelos a partir de plantillas de texto](../modeling/accessing-models-from-text-templates.md)  
  
 Proporciona información básica acerca de cómo hacer referencia al lenguaje específico de dominio en las plantillas de texto.  
  
 [Tutorial: Depurar una plantilla de texto que tiene acceso a un modelo](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)  
  
 Describe cómo realizar la solución de problemas y depuración en una plantilla de texto que hace referencia a un lenguaje específico de dominio.  
  
 [Tutorial: Conectar un host a un procesador de directivas personalizadas](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)  
  
 Describe cómo conectar un host personalizado para un procesador de directivas generado.  
  
 [El comando DslTextTransform](../modeling/the-dsltexttransform-command.md)  
  
 Describe el archivo de comandos que se ejecuta el ejecutable TextTransform en la línea de comandos para plantillas de texto que hacen referencia a lenguajes específicos de dominio.  
  
## <a name="reference"></a>Referencia  
 [Escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md)  
  
 Proporciona la sintaxis de directivas de plantilla de texto y bloques de control.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Generación de código en tiempo de diseño mediante plantillas de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
 Explica el proceso de transformación de plantillas de texto.  
  
 [Generación de código en un proceso de compilación](../modeling/code-generation-in-a-build-process.md)  
  
 Lea este tema si va a generar los archivos de un DSL en un servidor de compilación.