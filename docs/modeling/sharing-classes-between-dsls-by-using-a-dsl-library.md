---
title: Uso compartido de las clases entre DSL mediante una biblioteca de DSL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: "7"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: ed225f315c92cf9276eb97fcb78e1730250ecd4c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Compartir clases entre DSL mediante una biblioteca DSL
En el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de visualización y modelado de SDK, puede crear una definición incompleta de DSL que puede importar en otro ADSL. Esto le permite tener partes comunes de modelos similares.  
  
## <a name="creating-and-using-dsl-libraries"></a>Crear y usar bibliotecas de DSL  
  
#### <a name="to-create-a-dsl-library"></a>Para crear una biblioteca de DSL  
  
1.  Cree un nuevo proyecto DSL y elija la plantilla de solución de biblioteca de DSL.  
  
     Se creará un único proyecto DSL con un modelo vacío.  
  
2.  Puede agregar clases de dominio, relaciones, formas y así sucesivamente.  
  
     Los elementos de la biblioteca no es necesario que formar un único árbol de incrustación.  
  
     Para definir una relación que se pueden usar importadores, cree dos clases de dominio y crear la relación entre ellos.  
  
     Considere establecer el **modificador de herencia** de las clases de dominio para `Abstract`.  
  
3.  Puede agregar elementos que definen en el Explorador de DSL, como los compiladores de conexión.  
  
4.  Puede agregar personalizaciones que requieren código adicional, como las restricciones de validación.  
  
5.  Haga clic en **Transformar todas las plantillas de**.  
  
6.  Compile el proyecto.  
  
7.  Cuando se distribuye la DSL para otras personas, debe proporcionar el ensamblado compilado (DLL) y el archivo `DslDefinition.dsl`. Puede encontrar el ensamblado compilado en una carpeta bajo`Dsl\bin\*`  
  
#### <a name="to-import-a-dsl-library"></a>Para importar una biblioteca de DSL  
  
1.  En otra definición DSL, en **DSL explorador**, haga clic en la clase raíz de DSL y, a continuación, haga clic en **agregar nueva importación DslLibrary**.  
  
2.  En la ventana Propiedades, establezca la **ruta de acceso del archivo** de la biblioteca. Puede usar una ruta de acceso absoluta o relativa.  
  
     La biblioteca importada aparece en el Explorador de DSL, en modo de solo lectura.  
  
3.  Puede usar las clases importadas como clases base. Crear una clase de dominio en la importación DSL y en las propiedades de ventana, establezca **una clase Base** a una clase importada.  
  
4.  Haga clic en Transformar todas las plantillas.  
  
5.  Agregue al proyecto DSL una referencia al ensamblado (DLL) que se generó el proyecto de biblioteca de DSL.  
  
6.  Compile la solución.  
  
 Una biblioteca de DSL puede importar otras bibliotecas. Al importar una biblioteca, las importaciones aparecen automáticamente en el Explorador de DSL.  
  
## <a name="see-also"></a>Vea también  
 [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
