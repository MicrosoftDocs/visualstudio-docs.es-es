---
title: Personalización de un lenguaje específico de dominio
description: Aprenda a usar código personalizado para obtener acceso, modificar o crear un modelo en un lenguaje específico de dominio (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31b97b113b763a8f294386d4fa5fe66233a3f980
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360460"
---
# <a name="write-code-to-customize-a-domain-specific-language"></a>Escribir código para personalizar un lenguaje específico de dominio

En esta sección se muestra cómo usar código personalizado para obtener acceso, modificar o crear un modelo en un lenguaje específico de dominio.

Hay varios contextos en los que se puede escribir código que funcione con un DSL:

- **Comandos personalizados.** Puede crear un comando que los usuarios pueden invocar haciendo clic con el botón derecho en el diagrama y que puede modificar el modelo. Para obtener más información, vea [Cómo: agregar un comando al menú contextual](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

- **Validation (Validación).** Puede escribir código que compruebe que el modelo se encuentra en un estado correcto. Para obtener más información, vea [validación en un lenguaje Domain-Specific](../modeling/validation-in-a-domain-specific-language.md).

- **Invalidar el comportamiento predeterminado.** Puede modificar muchos aspectos del código que se genera a partir de DslDefinition. DSL. Para obtener más información, vea [invalidación y extensión de las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).

- **Transformación de texto.** Puede escribir plantillas de texto que contengan código que tenga acceso a un modelo y genere un archivo de texto, por ejemplo, para generar código de programa. Para obtener más información, vea [generar código a partir de un lenguaje Domain-Specific](../modeling/generating-code-from-a-domain-specific-language.md).

- **Otras extensiones de Visual Studio.** Puede escribir extensiones VSIX independientes que lean y modifiquen modelos. Para obtener más información, consulte [Cómo: abrir un modelo desde un archivo en el código del programa.](../modeling/how-to-open-a-model-from-file-in-program-code.md)

Las instancias de las clases que se definen en DslDefinition. DSL se mantienen en una estructura de datos denominada *almacén en memoria* (IMS) o *almacén*. Las clases que se definen en un DSL siempre toman un almacén como argumento para el constructor. Por ejemplo, si el DSL define una clase denominada example:

`Example element = new Example (theStore);`

mantener los objetos en el almacén (en lugar de los objetos normales) proporciona varias ventajas.

- **Transacciones**. Puede agrupar una serie de cambios relacionados en una transacción:

     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

     `{`

     `// make several changes to Store elements here`

     `t.Commit();`

     `}`

     Si se produce una excepción durante los cambios, para que no se realice la confirmación final (), el almacén se restablecerá a su estado anterior. Esto le ayuda a asegurarse de que los errores no salen del modelo en un estado incoherente. Para obtener más información, vea [navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md).

- **Relaciones binarias**. Si define una relación entre dos clases, las instancias en ambos extremos tienen una propiedad que navega hasta el otro extremo. Los dos extremos siempre están sincronizados. Por ejemplo, si define una relación de Parenthood con roles denominados elementos primarios y secundarios, podría escribir:

     `John.Children.Add(Mary)`

     Las dos expresiones siguientes ahora son verdaderas:

     `John.Children.Contains(Mary)`

     `Mary.Parents.Contains(John)`

     También puede lograr el mismo efecto si escribe:

     `Mary.Parents.Add(John)`

     Para obtener más información, vea [navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md).

- **Reglas y eventos**. Puede definir reglas que se activen cuando se realicen los cambios especificados. Las reglas se usan, por ejemplo, para mantener las formas del diagrama actualizadas con los elementos del modelo que presentan. Para obtener más información, consulte [responder a los cambios y propagarlos](../modeling/responding-to-and-propagating-changes.md).

- **Serialización**. El almacén proporciona un método estándar para serializar los objetos que contiene en un archivo. Puede personalizar las reglas para la serialización y deserialización. Para obtener más información, vea [personalizar File Storage y serialización XML](../modeling/customizing-file-storage-and-xml-serialization.md).

## <a name="see-also"></a>Consulta también

- [Personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md)