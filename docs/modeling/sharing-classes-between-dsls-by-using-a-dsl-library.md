---
title: "Compartir clases entre DSL mediante una biblioteca DSL | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: 7
caps.handback.revision: 7
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Compartir clases entre DSL mediante una biblioteca DSL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En el SDK de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de visualización y modelado, puede crear una definición incompleta ADSL que puede importar en otro ADSL.  Esto permite las partes comunes del factor de modelos similares.  
  
## Crear y con bibliotecas ADSL  
  
#### Para crear una biblioteca ADSL  
  
1.  Cree un nuevo proyecto ADSL, y elija la plantilla de solución de biblioteca ADSL.  
  
     Un único proyecto ADSL se creará con un modelo vacío.  
  
2.  Puede agregar clases de dominio, relaciones, formas y así sucesivamente.  
  
     Los elementos de la biblioteca no tienen que formar un único árbol de incrustación.  
  
     Para definir una relación que los importadores pueden utilizar, cree dos clases de dominio y crear la relación entre ellas.  
  
     Considere establecer **Modificador de herencia** de las clases de dominio a `Abstract`.  
  
3.  Puede agregar los elementos que se definen en el Explorador ADSL, como generadores de Conexión.  
  
4.  Puede agregar las personalizaciones que requieren código adicional, como restricciones de validación.  
  
5.  Haga clic en **Transformar todas las plantillas**.  
  
6.  Compile el proyecto.  
  
7.  Cuando se distribuyen ADSL para que otras personas utilizan, debe proporcionar el ensamblado compilado \(DLL\) y el archivo `DslDefinition.dsl`.  Puede encontrar el ensamblado compilado en una carpeta bajo `Dsl\bin\*`  
  
#### Para importar una biblioteca ADSL  
  
1.  En otra definición ADSL, en **Explorador ADSL**, haga clic con el botón secundario en la clase raíz ADSL, y haga clic en **agregue la nueva importación de DslLibrary**.  
  
2.  En la ventana Propiedades, establezca **Ruta de acceso del archivo** de biblioteca.  Puede utilizar una ruta de acceso relativa o absoluta.  
  
     La biblioteca importada aparece en el Explorador ADSL, en modo de sólo lectura.  
  
3.  Puede utilizar las clases importadas como clases base.  Cree una clase de dominio en ADSL que importa, y en la ventana Propiedades, establezca **clase base** a una clase importada.  
  
4.  Transformación en todas las plantillas.  
  
5.  Agregue al proyecto ADSL una referencia al ensamblado \(DLL\) compilado en el proyecto de biblioteca de ADSL.  
  
6.  Compile la solución.  
  
 Una biblioteca ADSL puede importar otras bibliotecas.  Cuando se importa una biblioteca, sus importaciones también aparecen automáticamente en el Explorador de ADSL.  
  
## Vea también  
 [Cómo: Definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)