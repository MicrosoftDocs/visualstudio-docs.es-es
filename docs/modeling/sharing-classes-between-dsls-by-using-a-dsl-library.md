---
title: Compartir clases entre DSL mediante una biblioteca DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: ccfb4fa9de6513ecc36cad7156117d70879fca2e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49814931"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Compartir clases entre DSL mediante una biblioteca DSL
En Visual Studio de visualización y SDK de modelado, puede crear una definición incompleta de DSL que pueden importar a otro DSL. Esto le permite incluir partes comunes de modelos similares.

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

1. En otra definición de DSL en **DSL Explorer**, haga clic en la clase raíz del DSL y, a continuación, haga clic en **agregar una nueva importación de DslLibrary**.

2. En la ventana Propiedades, establezca la **ruta de acceso del archivo** de la biblioteca. Puede usar una ruta de acceso absoluta o relativa.

    La biblioteca importada aparece en el Explorador de DSL, en modo de solo lectura.

3. Puede usar las clases importadas como clases base. Crear una clase de dominio en la importación de DSL, y en las propiedades de ventana, establezca **clase Base** a una clase importada.

4. Haga clic en Transformar todas las plantillas.

5. En el proyecto DSL, agregue una referencia al ensamblado (DLL) que se compiló el proyecto de biblioteca DSL.

6. Compile la solución.

   Una biblioteca DSL que puede importar otras bibliotecas. Al importar una biblioteca, sus importaciones aparecen automáticamente en el Explorador de DSL.

## <a name="see-also"></a>Vea también

- [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
