---
title: "Ninguno de los m&#233;todos &#39;Main&#39; a los que se tiene acceso con las signaturas apropiadas encontrados en &#39;&lt;nombreDeTipo&gt;&#39; puede ser el m&#233;todo de inicio porque son gen&#233;ricos o est&#225;n anidados en tipos gen&#233;ricos | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30796"
  - "BC30796"
helpviewer_keywords: 
  - "BC30796"
ms.assetid: 606b3629-5a92-4c79-ace2-a530cab8c978
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ninguno de los m&#233;todos &#39;Main&#39; a los que se tiene acceso con las signaturas apropiadas encontrados en &#39;&lt;nombreDeTipo&gt;&#39; puede ser el m&#233;todo de inicio porque son gen&#233;ricos o est&#225;n anidados en tipos gen&#233;ricos
Una clase, un módulo o una estructura no tiene ningún procedimiento `Main` que califica como procedimiento de inicio de proyecto.  
  
 Visual Basic requiere que el procedimiento de inicio de un proyecto no debe depender de argumentos de tipo. Por lo tanto, debe poder tener acceso, como mínimo, a un procedimiento `Main` que no sea genérico ni esté incluido en un tipo genérico.  
  
 **Identificador de error:** BC30796  
  
### Para corregir este error  
  
-   Definir al menos uno de los procedimientos `Main` para que no sea genérico y no esté incluido en un tipo genérico.  
  
     O bien  
  
-   En la página **Propiedades** del proyecto, especifique otro formulario o módulo para **Formulario de inicio** u **Objeto de inicio**.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN Cómo: modificar las propiedades y los valores de configuración del proyecto](http://msdn.microsoft.com/es-es/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [NO ESTÁ EN LA COMPILACIÓN: Versión de Visual Basic del programa Hola a todos](http://msdn.microsoft.com/es-es/9d030b60-e148-4366-a462-69532f02294c)