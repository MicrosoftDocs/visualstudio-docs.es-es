---
title: "Generar c&#243;digo a partir de lenguajes espec&#237;ficos de dominio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: 13
caps.handback.revision: 13
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Generar c&#243;digo a partir de lenguajes espec&#237;ficos de dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] proporciona una forma eficaz de generar código, documentos, los archivos de configuración y otros artefactos de los datos representados en modelos.  Mediante [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], puede crear un conjunto de clases que representan los datos, y puede escribir plantillas de texto en las clases cuyas nombres y propiedades reflejan que los datos.  
  
 Por ejemplo, Fabrikam tiene un archivo XML de los nombres y las direcciones de correo electrónico de cliente.  Los desarrolladores crean un modelo en el que el cliente es una clase, con nombre y el correo electrónico de propiedades.  Escriba varias plantillas de texto para procesar los datos, como este fragmento que muestra una tabla de todos los clientes como parte de una página HTML:  
  
```  
<table>  
<# foreach (Customer c in ContactList) {  #>  
  <tr><td> <#= c.FullName #> </td>   
      <td> <#= c.EmailAddress #> </td> </tr>  
<# } #>  </table>  
```  
  
 Cuando se procesa la base de datos de cliente, el archivo XML se lee en al almacén.  *Un procesador*de directivas, creado con [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], coloca la clase customer a disposición del código de la plantilla de texto. Muchas plantillas de texto se pueden ejecutar en el mismo almacén.  
  
 Las plantillas de texto son esenciales para [!INCLUDE[dsl](../modeling/includes/dsl_md.md)].  Se utilizan para generar el código fuente para los elementos de modelo de dominio así como del Paquete y los controles que se utilizan para integrar las herramientas con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Esta sección describe algunas de las maneras de crear, de modificar, y depurar las plantillas de texto utilizadas en [!INCLUDE[dsl](../modeling/includes/dsl_md.md)].  
  
## En esta sección  
 [Acceso a modelos a partir de plantillas de texto](../modeling/accessing-models-from-text-templates.md)  
  
 Proporciona información básica sobre cómo hacer referencia a un lenguaje específico de las plantillas de texto.  
  
 [Tutorial: Depurar una plantilla de texto que tiene acceso a un modelo](../Topic/Walkthrough:%20Debugging%20a%20Text%20Template%20that%20Accesses%20a%20Model.md)  
  
 Describe cómo hacer que la solución de problemas y la depuración en una plantilla de texto que hace referencia a un lenguaje específico.  
  
 [Tutorial: Conectar un host a un procesador de directivas personalizadas](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)  
  
 Describe cómo conectar un host personalizado a un procesador de directivas generado.  
  
 [El comando DslTextTransform](../modeling/the-dsltexttransform-command.md)  
  
 Describe el archivo de comandos que ejecuta la aplicación ejecutable de TextTransform en la línea de comandos para las plantillas de texto que hacen referencia los lenguajes específicos.  
  
## Referencia  
 [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md)  
  
 Proporciona la sintaxis de las directivas y los bloques de control de plantilla de texto.  
  
## Secciones relacionadas  
 [Design\-Time Code Generation by using T4 Text Templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
 Explica el proceso de transformación de plantillas de texto.  
  
 [Code Generation in a Build Process](../modeling/code-generation-in-a-build-process.md)  
  
 Lea este tema si está generando los archivos ADSL en un servidor de compilación.