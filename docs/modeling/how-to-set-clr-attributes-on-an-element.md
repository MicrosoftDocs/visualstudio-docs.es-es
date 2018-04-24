---
title: 'Cómo: Establecer atributos de CLR en un elemento'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 43691225434a06fc7b3831367efb21980373dfa1
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Cómo: Establecer atributos de CLR en un elemento
Atributos personalizados son atributos especiales que se pueden agregar a los diagramas, formas, conectores y elementos de dominio. Puede agregar cualquier atributo que hereda de la `System.Attribute` clase.

### <a name="to-add-a-custom-attribute"></a>Para agregar un atributo personalizado

1.  En el **DSL explorador**, seleccione el elemento al que desea agregar un atributo personalizado.

2.  En el **propiedades** ventana, junto a la **atributos personalizados** propiedad, haga clic en el botón Examinar (**...** ) icono.

     El **editar atributos** abre el cuadro de diálogo.

3.  En el **nombre** columna, haga clic en  **\<Agregar atributo >** y escriba el nombre del atributo. Presione ENTRAR.

4.  La línea en el nombre del atributo muestra entre paréntesis. En esta línea, escriba un tipo de parámetro para el atributo (por ejemplo, `string`), y, a continuación, presione ENTRAR.

5.  En el **propiedad Name** columna, escriba un nombre adecuado, por ejemplo, `MyString`.

6.  Haga clic en **Aceptar**.

     El **atributos personalizados** propiedad ahora muestra el atributo en el formato siguiente:

     `[` *AttributeName* `(` *ParameterName* `=` *tipo* `)]`

## <a name="see-also"></a>Vea también

- [Glosario de herramientas de lenguaje específico de dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)