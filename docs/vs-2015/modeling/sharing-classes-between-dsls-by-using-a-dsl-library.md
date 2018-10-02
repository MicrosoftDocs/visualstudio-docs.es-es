---
title: Compartir clases entre DSL mediante una biblioteca DSL | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a4ec7820be2cc4f308582e71f3ba64ded5c296e7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577299"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Compartir clases entre DSL mediante una biblioteca DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [compartir clases entre DSL mediante una biblioteca DSL](https://docs.microsoft.com/visualstudio/modeling/sharing-classes-between-dsls-by-using-a-dsl-library).  
  
En el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] SDK de modelado y visualización, puede crear una definición incompleta de DSL que pueden importar a otro DSL. Esto le permite incluir partes comunes de modelos similares.  
  
## <a name="creating-and-using-dsl-libraries"></a>Crear y usar las bibliotecas DSL  
  
#### <a name="to-create-a-dsl-library"></a>Para crear una biblioteca DSL  
  
1.  Cree un nuevo proyecto DSL y elija la plantilla de solución de la biblioteca DSL.  
  
     Con un modelo vacío, se creará un único proyecto DSL.  
  
2.  Puede agregar clases de dominio, relaciones, formas y así sucesivamente.  
  
     Los elementos de la biblioteca no es necesario que formar un único árbol de incrustación.  
  
     Para definir una relación que pueden utilizar los importadores, cree dos clases de dominio y crear la relación entre ellos.  
  
     Considere la posibilidad de la **modificador de herencia** de las clases de dominio para `Abstract`.  
  
3.  Puede agregar elementos que se definen en el Explorador de DSL, por ejemplo, los generadores de conexiones.  
  
4.  Puede agregar las personalizaciones que requieren código adicional, como las restricciones de validación.  
  
5.  Haga clic en **Transformar todas las plantillas**.  
  
6.  Compile el proyecto.  
  
7.  Cuando se distribuye el DSL para otras personas usar, debe proporcionar el ensamblado compilado (DLL) y el archivo `DslDefinition.dsl`. Puede encontrar el ensamblado compilado en una carpeta bajo `Dsl\bin\*`  
  
#### <a name="to-import-a-dsl-library"></a>Para importar una biblioteca DSL  
  
1.  En otra definición de DSL en **DSL Explorer**, haga clic en la clase raíz del DSL y, a continuación, haga clic en **agregar una nueva importación de DslLibrary**.  
  
2.  En la ventana Propiedades, establezca la **ruta de acceso del archivo** de la biblioteca. Puede usar una ruta de acceso absoluta o relativa.  
  
     La biblioteca importada aparece en el Explorador de DSL, en modo de solo lectura.  
  
3.  Puede usar las clases importadas como clases base. Crear una clase de dominio en la importación de DSL, y en las propiedades de ventana, establezca **clase Base** a una clase importada.  
  
4.  Haga clic en Transformar todas las plantillas.  
  
5.  En el proyecto DSL, agregue una referencia al ensamblado (DLL) que se compiló el proyecto de biblioteca DSL.  
  
6.  Compile la solución.  
  
 Una biblioteca DSL que puede importar otras bibliotecas. Al importar una biblioteca, sus importaciones aparecen automáticamente en el Explorador de DSL.  
  
## <a name="see-also"></a>Vea también  
 [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)



