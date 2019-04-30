---
title: Procedimiento Establecer atributos de CLR en un elemento
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8954aa6a42e743617080bb6918508273c1dd9528
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62811282"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Procedimiento Establecer atributos de CLR en un elemento
Los atributos personalizados son atributos especiales que se pueden agregar a diagramas, formas, conectores y elementos de dominio. Puede agregar cualquier atributo que hereda de la `System.Attribute` clase.

### <a name="to-add-a-custom-attribute"></a>Para agregar un atributo personalizado

1. En el **DSL Explorer**, seleccione el elemento al que desea agregar un atributo personalizado.

2. En el **propiedades** ventana, junto a la **atributos personalizados** propiedad, haga clic en el (**...** ) icono.

     El **editar atributos** abre el cuadro de diálogo.

3. En el **nombre** columna, haga clic en  **\<Agregar atributo >** y escriba el nombre del atributo. Presione ENTRAR.

4. La línea bajo el nombre del atributo muestra entre paréntesis. En esta línea, escriba un tipo de parámetro para el atributo (por ejemplo, `string`), y, a continuación, presione ENTRAR.

5. En el **nombre de propiedad** columna, escriba un nombre adecuado, por ejemplo, `MyString`.

6. Haga clic en **Aceptar**.

     El **atributos personalizados** propiedad ahora muestra el atributo en el formato siguiente:

     `[` *AttributeName* `(` *ParameterName* `=` *tipo* `)]`

## <a name="see-also"></a>Vea también

- [Glosario de las herramientas de lenguajes específicos de dominio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)