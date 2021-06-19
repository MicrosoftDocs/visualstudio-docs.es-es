---
title: Personalización de un lenguaje específico de dominio
description: Aprenda a usar código personalizado para acceder, modificar o crear un modelo en un lenguaje específico del dominio (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2231ef94bee01558e2c26899a5d9a0c855489e94
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388053"
---
# <a name="write-code-to-customize-a-domain-specific-language"></a>Escribir código para personalizar un lenguaje específico de dominio

En esta sección se muestra cómo usar código personalizado para acceder, modificar o crear un modelo en un lenguaje específico del dominio.

Hay varios contextos en los que puede escribir código que funcione con un DSL:

- **Comandos personalizados.** Puede crear un comando que los usuarios puedan invocar haciendo clic con el botón derecho en el diagrama y que pueda modificar el modelo. Para obtener más información, [vea Cómo: Agregar un comando al menú contextual.](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)

- **Validation (Validación).** Puede escribir código que compruebe que el modelo está en un estado correcto. Para obtener más información, [vea Validación en un Domain-Specific lenguaje .](../modeling/validation-in-a-domain-specific-language.md)

- **Invalidar el comportamiento predeterminado.** Puede modificar muchos aspectos del código generado a partir de DslDefinition.dsl. Para obtener más información, [vea Invalidar y extender las clases generadas.](../modeling/overriding-and-extending-the-generated-classes.md)

- **Transformación texto.** Puede escribir plantillas de texto que contengan código que acceda a un modelo y genere un archivo de texto, por ejemplo, para generar código de programa. Para obtener más información, vea [Generating Code from a Domain-Specific Language](../modeling/generating-code-from-a-domain-specific-language.md).

- **Otras Visual Studio de datos.** Puede escribir extensiones VSIX independientes que lean y modifiquen modelos. Para obtener más información, [vea Cómo: Abrir un modelo desde un archivo en el código del programa.](../modeling/how-to-open-a-model-from-file-in-program-code.md)

Las instancias de las clases que se definen en DslDefinition.dsl se mantienen en una estructura de datos denominada *Almacén* en memoria (IMS) o *Store*. Las clases que defina en un DSL siempre toman store como argumento para el constructor. Por ejemplo, si el DSL define una clase denominada Ejemplo:

`Example element = new Example (theStore);`

mantener objetos en el Almacén (en lugar de igual que los objetos normales) proporciona varias ventajas.

- **Transacciones**. Puede agrupar una serie de cambios relacionados en una transacción:

     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

     `{`

     `// make several changes to Store elements here`

     `t.Commit();`

     `}`

     Si se produce una excepción durante los cambios, para que no se realice la confirmación final(), store se restablecerá a su estado anterior. Esto le ayuda a asegurarse de que los errores no dejan el modelo en un estado incoherente. Para obtener más información, [vea Navegar y actualizar un modelo en código de programa.](../modeling/navigating-and-updating-a-model-in-program-code.md)

- **Relaciones binarias**. Si define una relación entre dos clases, las instancias de ambos extremos tienen una propiedad que navega al otro extremo. Los dos extremos siempre se sincronizan. Por ejemplo, si define una relación parentmatriz con roles denominados Elementos primarios e secundarios, podría escribir:

     `John.Children.Add(Mary)`

     Ahora se cumplen las dos expresiones siguientes:

     `John.Children.Contains(Mary)`

     `Mary.Parents.Contains(John)`

     También podría lograr el mismo efecto escribiendo:

     `Mary.Parents.Add(John)`

     Para obtener más información, [vea Navegar y actualizar un modelo en código de programa.](../modeling/navigating-and-updating-a-model-in-program-code.md)

- **Reglas y eventos**. Puede definir reglas que se activa cada vez que se realizan los cambios especificados. Las reglas se usan, por ejemplo, para mantener las formas del diagrama actualizadas con los elementos del modelo que presentan. Para obtener más información, [vea Responder a y propagar cambios.](../modeling/responding-to-and-propagating-changes.md)

- **Serialización**. Store proporciona una manera estándar de serializar los objetos que contiene en un archivo. Puede personalizar las reglas para serializar y deserializar. Para obtener más información, vea [Personalización de File Storage y serialización XML.](../modeling/customizing-file-storage-and-xml-serialization.md)

## <a name="see-also"></a>Vea también

- [Personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md)