---
title: Compartir clases entre DSL mediante una biblioteca DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a09622a2cc7ae6d2a2451ac1de6b628020cff19f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747404"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Compartir clases entre DSL mediante una biblioteca DSL
En el SDK de visualización y modelado de Visual Studio, puede crear una definición de DSL incompleta que se puede importar en otro DSL. Esto le permite factorizar partes comunes de modelos similares.

## <a name="creating-and-using-dsl-libraries"></a>Crear y usar bibliotecas DSL

#### <a name="to-create-a-dsl-library"></a>Para crear una biblioteca DSL

1. Cree un nuevo proyecto DSL y elija la plantilla de solución biblioteca DSL.

     Se creará un solo proyecto DSL con un modelo vacío.

2. Puede Agregar clases de dominio, relaciones, formas, etc.

     Los elementos de la biblioteca no tienen que formar un único árbol de incrustación.

     Para definir una relación que puedan usar los importadores, cree dos clases de dominio y cree la relación entre ellas.

     Considere la posibilidad de establecer el **modificador de herencia** de las clases de dominio en `Abstract`.

3. Puede Agregar los elementos que defina en el explorador de DSL, como los generadores de conexiones.

4. Puede Agregar personalizaciones que requieran código adicional, como restricciones de validación.

5. Haga clic en **transformar todas las plantillas**.

6. Compile el proyecto.

7. Al distribuir el DSL para que lo usen otras personas, debe proporcionar el ensamblado compilado (DLL) y el `DslDefinition.dsl` de archivos. Puede encontrar el ensamblado compilado en una carpeta en `Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>Para importar una biblioteca DSL

1. En otra definición de DSL, en el **Explorador de DSL**, haga clic con el botón secundario en la clase raíz del DSL y, a continuación, haga clic en **Agregar nueva DslLibrary importar**.

2. En el ventana Propiedades, establezca la **ruta de acceso de archivo** de la biblioteca. Puede usar una ruta de acceso relativa o absoluta.

    La biblioteca importada aparece en el explorador de DSL, en modo de solo lectura.

3. Puede utilizar las clases importadas como clases base. Cree una clase de dominio en el ADSL de importación y, en el ventana Propiedades, establezca **clase base** en una clase importada.

4. Haga clic en transformar todas las plantillas.

5. Agregue al proyecto DSL una referencia al ensamblado (DLL) compilado por el proyecto de biblioteca DSL.

6. Compile la solución.

   Una biblioteca DSL puede importar otras bibliotecas. Al importar una biblioteca, sus importaciones también aparecen automáticamente en el explorador de DSL.

## <a name="see-also"></a>Vea también

- [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
