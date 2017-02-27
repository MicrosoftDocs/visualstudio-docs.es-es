---
title: "Creating Custom T4 Text Template Directive Processors | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, custom directive processors"
ms.assetid: 422b47af-5441-4b02-b5ad-1b8b328457e3
caps.latest.revision: 29
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 29
---
# Creating Custom T4 Text Template Directive Processors
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El *proceso de transformación de plantillas de texto* toma un archivo de *plantilla de texto* como entrada y produce un archivo de texto como salida.  El *motor de transformación de plantillas de texto* controla el proceso e interactúa con un host de transformación de plantillas de texto y uno o más *procesadores de directivas* de plantilla de texto para completar el proceso.  Para obtener más información, vea [The Text Template Transformation Process](../modeling/the-text-template-transformation-process.md).  
  
 Para crear un procesador de directivas personalizado, crea una clase que herede de <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.  
  
 La diferencia entre ambas es que <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> implementa la interfaz mínima necesaria para obtener parámetros del usuario y generar el código que produce el archivo de salida de la plantilla.  <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementa el modelo de diseño requires\/provides.  <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> controla dos parámetros especiales, `requires` y `provides`.  Por ejemplo, un procesador de directivas personalizado puede aceptar un nombre de archivo del usuario, abrir y leer el archivo y, a continuación, almacenar el texto del archivo en una variable con el nombre `fileText`.  Una subclase de la clase <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> puede tomar un nombre de archivo del usuario como valor del parámetro `requires` y el nombre de la variable donde se va a guardar el texto como valor del parámetro `provides`.  Este procesador abre y lee el archivo y, a continuación, almacena el texto del archivo en la variable especificada.  
  
 Antes de llamar a un procesador de directivas personalizado desde una plantilla de texto en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], debe registrarlo.  
  
 Para obtener más información sobre cómo agregar la clave del Registro, vea [Deploying a Custom Directive Processor](../modeling/deploying-a-custom-directive-processor.md).  
  
## Directivas personalizadas  
 Una directiva personalizada tiene el siguiente aspecto:  
  
 `<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" … #>`  
  
 Puede utilizar un procesador de directivas personalizado si desea tener acceso a recursos o datos externos desde una plantilla de texto.  
  
 Diferentes plantillas de texto pueden compartir la funcionalidad que proporciona un único procesador de directivas, de modo que los procesadores de directivas proporcionan una manera de factorizar el código para volver a usarlo.  La directiva `include` integrada es similar, porque puede usarla para factorizar el código y compartirlo entre varias plantillas de texto.  La diferencia es que cualquier funcionalidad que la directiva `include` proporciona es fija y no acepta parámetros.  Si desea proporcionar funcionalidad común a una plantilla de texto y permitir que la plantilla pase parámetros, debe crear un procesador de directivas personalizado.  
  
 Algunos ejemplos de procesadores de directivas personalizados podrían ser:  
  
-   Un procesador de directivas que devuelve datos de una base de datos que acepta un nombre de usuario y una contraseña como parámetros.  
  
-   Un procesador de directivas para abrir y leer un archivo que acepta el nombre del archivo como parámetro.  
  
### Partes principales de un procesador de directivas personalizado  
 Para desarrollar un procesador de directivas, debe crear una clase que herede de <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.  
  
 Los métodos más importantes de `DirectiveProcessor` que debe implementar son los siguientes.  
  
-   `bool IsDirectiveSupported(string directiveName)`: devuelve `true` si el procesador de directivas puede trabajar con la directiva indicada.  
  
-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)`: el motor de la plantilla llama a este método en cada aparición de una directiva en la plantilla.  El procesador debe guardar los resultados.  
  
 Después de todas las llamadas a ProcessDirective\(\), el motor de plantillas llamará a estos métodos:  
  
-   `string[] GetReferencesForProcessingRun()`: devuelve los nombres de los ensamblados que necesita el código de plantilla.  
  
-   `string[] GetImportsForProcessingRun()`: devuelve los espacios de nombres que se pueden utilizar en el código de plantilla.  
  
-   `string GetClassCodeForProcessingRun()`: devuelve el código de métodos, propiedades y otras declaraciones que el código de plantilla puede utilizar.  La manera más fácil de usarlo es compilar una cadena que contenga el código de C\# o de Visual Basic.  Para que se pueda llamar al procesador de directivas desde una plantilla que utiliza cualquier lenguaje de CLR, puede construir las instrucciones como un árbol CodeDom y, a continuación, devolver el resultado de serializar el árbol en el lenguaje utilizado por la plantilla.  
  
-   Para obtener más información, vea [Walkthrough: Creating a Custom Directive Processor](../modeling/walkthrough-creating-a-custom-directive-processor.md).  
  
## En esta sección  
 [Deploying a Custom Directive Processor](../modeling/deploying-a-custom-directive-processor.md)  
 Explica cómo registrar un procesador de directivas personalizado.  
  
 [Walkthrough: Creating a Custom Directive Processor](../modeling/walkthrough-creating-a-custom-directive-processor.md)  
 Describe cómo crear un procesador de directivas personalizado, cómo registrar y probar el procesador de directivas, y cómo dar formato al archivo de salida como HTML.