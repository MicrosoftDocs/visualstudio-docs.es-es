---
title: "Escribir c&#243;digo para personalizar un lenguaje espec&#237;fico de dominio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lenguaje específico de dominio, programación"
ms.assetid: a4a17f5b-9c97-4575-b2d1-3182c1896b72
caps.latest.revision: 29
caps.handback.revision: 29
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Escribir c&#243;digo para personalizar un lenguaje espec&#237;fico de dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En esta sección se muestra cómo utilizar código personalizado para tener acceso, modificar, o para crear un modelo en un lenguaje específico de dominio.  
  
 Hay varios contextos en los que puede escribir código que funciona con un ADSL:  
  
-   **comandos personalizados.** Puede crear un comando que los usuarios pueden invocar haciendo clic con el botón secundario en el diagrama, y que puede modificar el modelo.  Para obtener más información, vea [Cómo: Agregar un comando a un menú contextual](../Topic/How%20to:%20Add%20a%20Command%20to%20the%20Shortcut%20Menu.md).  
  
-   **validación.** Puede escribir código que comprueba que el modelo está en un estado correcto.  Para obtener más información, vea [Validación en un lenguaje específico de dominio](../modeling/validation-in-a-domain-specific-language.md).  
  
-   **invalidar el comportamiento predeterminado.** Puede modificar muchos aspectos del código que se genera de DslDefinition.dsl.  Para obtener más información, vea [Invalidar y ampliar clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).  
  
-   **Transformación de texto.** Puede escribir plantillas de texto que contienen el código que tiene acceso a un modelo y genera un archivo de texto, por ejemplo para generar código de programa.  Para obtener más información, vea [Generar código a partir de lenguajes específicos de dominio](../modeling/generating-code-from-a-domain-specific-language.md).  
  
-   **otras extensiones de Visual Studio.** Puede escribir extensiones independientes VSIX que leen y modificar modelos.  Para obtener más información, vea [Cómo: Abrir un modelo desde un archivo en el código del programa](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
 Las instancias de las clases que defina en DslDefinition.dsl se mantienen una estructura de datos con *el almacén* de memoria \(IMS\) o almacén *.* Las clases que defina en ADSL presentan siempre un almacén como argumento el constructor.  Por ejemplo, si un DSL define una clase denominada Example:  
  
 `Example element = new Example (theStore);`  
  
 conservar objetos en el almacén \(en lugar de simplemente como objetos ordinarios\) ofrece varias ventajas.  
  
-   **transacciones**.  Puede agrupar una serie de cambios relacionados en una transacción:  
  
     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`  
  
     `{`  
  
     `// make several changes to Store elements here`  
  
     `t.Commit();`  
  
     `}`  
  
     Si se produce una excepción durante los cambios, no para realizar Commit\(\) final, el almacén se restaurará el estado anterior.  Esto ayuda a asegurarse de que los errores no permiten el modelo en un estado incoherente.  Para obtener más información, vea [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
-   **relaciones binarias**.  Si define una relación entre dos clases, instancias en ambos extremos tienen una propiedad que navegue al otro extremo.  los dos extremos se sincronizan siempre.  Por ejemplo, si define una relación de la paternidad con roles denominados Parents y los elementos secundarios, podría escribir:  
  
     `John.Children.Add(Mary)`  
  
     Ambas expresiones siguientes son verdaderas ahora:  
  
     `John.Children.Contains(Mary)`  
  
     `Mary.Parents.Contains(John)`  
  
     También podría lograr el mismo efecto escribiendo:  
  
     `Mary.Parents.Add(John)`  
  
     Para obtener más información, vea [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
-   **reglas y eventos**.  Puede definir reglas que desencadenan siempre que se realicen cambios especificados.  Las reglas se utilizan, por ejemplo, para mantener las formas en el diagrama actualizadas con elementos del modelo que presentan.  Para obtener más información, vea [Responder a los cambios y propagarlos](../modeling/responding-to-and-propagating-changes.md).  
  
-   **serialización**.  El almacén proporciona un método estándar de serializar los objetos que contiene un archivo.  Puede personalizar las reglas para serializar y deserializar.  Para obtener más información, vea [Personalizar el almacenamiento de archivos y la serialización XML](../modeling/customizing-file-storage-and-xml-serialization.md).  
  
## Vea también  
 [Personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md)