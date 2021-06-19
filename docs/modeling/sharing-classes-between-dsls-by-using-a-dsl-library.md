---
title: Compartir clases entre DSL mediante una biblioteca DSL
description: Obtenga información sobre que, en Visual Studio SDK de visualización y modelado, puede crear una definición de DSL incompleta que puede importar a otro DSL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c3729e4f386ec5a21c8f30ee3f0df6e7ffa8d891
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385505"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Compartir clases entre DSL mediante una biblioteca DSL
En el SDK Visual Studio visualización y modelado, puede crear una definición de DSL incompleta que puede importar a otro DSL. Esto le permite tener en cuenta las partes comunes de modelos similares.

## <a name="creating-and-using-dsl-libraries"></a>Creación y uso de bibliotecas DSL

#### <a name="to-create-a-dsl-library"></a>Para crear una biblioteca DSL

1. Cree un nuevo proyecto DSL y elija la plantilla de solución Biblioteca DSL.

     Se creará un único proyecto DSL con un modelo vacío.

2. Puede agregar clases de dominio, relaciones, formas, entre otras.

     Los elementos de la biblioteca no tienen que formar un único árbol de inserción.

     Para definir una relación que los importadores puedan usar, cree dos clases de dominio y cree la relación entre ellas.

     Considere la posibilidad de **establecer el modificador de herencia** de las clases de dominio en `Abstract` .

3. Puede agregar elementos que defina en el Explorador de DSL, como Generadores de conexiones.

4. Puede agregar personalizaciones que requieran código adicional, como restricciones de validación.

5. Haga clic **en Transformar todas las plantillas.**

6. Compile el proyecto.

7. Al distribuir el DSL para que lo usen otras personas, debe proporcionar tanto el ensamblado compilado (DLL) como el archivo `DslDefinition.dsl` . Puede encontrar el ensamblado compilado en una carpeta en `Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>Para importar una biblioteca DSL

1. En otra definición de DSL, en el Explorador **de DSL,** haga clic con el botón derecho en la clase raíz del DSL y, a continuación, haga clic en Agregar nueva **importación dsllibrary**.

2. En la ventana Propiedades, establezca la ruta **de acceso del** archivo de la biblioteca. Puede usar una ruta de acceso relativa o absoluta.

    La biblioteca importada aparece en el Explorador de DSL, en modo de solo lectura.

3. Puede usar las clases importadas como clases base. Cree una clase de dominio en el DSL de importación y, en la ventana Propiedades, establezca **Clase base** en una clase importada.

4. Haga clic en Transformar todas las plantillas.

5. Agregue al proyecto DSL una referencia al ensamblado (DLL) compilado por el proyecto de biblioteca DSL.

6. Compile la solución.

   Una biblioteca DSL puede importar otras bibliotecas. Al importar una biblioteca, sus importaciones también aparecen automáticamente en el Explorador de DSL.

## <a name="see-also"></a>Vea también

- [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
