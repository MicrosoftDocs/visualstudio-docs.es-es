---
title: Escribir código para personalizar un lenguaje específico de dominio | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: cb058ba2467ae852491339dc64a3fba837249688
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="writing-code-to-customise-a-domain-specific-language"></a>Escribir código para personalizar lenguajes específicos de dominio
En esta sección se muestra cómo utilizar código personalizado para acceder, modificar o crear un modelo en un lenguaje específico de dominio.  
  
 Hay varios contextos en los que puede escribir código que funcione con un DSL:  
  
-   **Comandos personalizados.** Puede crear un comando que los usuarios pueden invocar con el botón secundario en el diagrama, y que puede modificar el modelo. Para obtener más información, consulte [Cómo: agregar un comando al menú contextual](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
-   **Validation (Validación).** Puede escribir código que comprueba si el modelo está en un estado correcto. Para obtener más información, consulte [validación en un lenguaje específico de dominio](../modeling/validation-in-a-domain-specific-language.md).  
  
-   **Invalidar el comportamiento predeterminado.** Puede modificar muchos aspectos del código que se genera a partir de DslDefinition.dsl. Para obtener más información, consulte [reemplazar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).  
  
-   **Transformación de texto.** Puede escribir plantillas de texto que contienen código que tiene acceso a un modelo y genera un archivo de texto, por ejemplo, para generar código de programa. Para obtener más información, consulte [generar código desde un lenguaje específico de dominio](../modeling/generating-code-from-a-domain-specific-language.md).  
  
-   **Otras extensiones de Visual Studio.** Puede escribir extensiones VSIX independientes que leen y modificar los modelos. Para obtener más información, vea [Cómo: abrir un modelo de archivo en el código de programa](../modeling/how-to-open-a-model-from-file-in-program-code.md)  
  
 Instancias de las clases que definen en DslDefinition.dsl se mantienen en una estructura de datos denominada el *almacén de datos en memoria* (IMS) o *almacén*. Las clases que defina en un DSL siempre toman un almacén como argumento al constructor. Por ejemplo, si tu DSL define una clase denominada ejemplo:  
  
 `Example element = new Example (theStore);`  
  
 mantener los objetos en el almacén (en lugar de los objetos ordinarios simplemente como) ofrece varias ventajas.  
  
-   **Las transacciones**. Puede agrupar una serie de cambios relacionados en una transacción:  
  
     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`  
  
     `{`  
  
     `// make several changes to Store elements here`  
  
     `t.Commit();`  
  
     `}`  
  
     Si se produce una excepción durante los cambios, por lo que no se realiza el Commit() final, el almacén se restablecerá a su estado anterior. Esto le ayuda a asegurarse de que los errores no dejar el modelo en un estado incoherente. Para obtener más información, consulte [navegar y actualizar un modelo de código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
-   **Las relaciones binarias**. Si define una relación entre dos clases, instancias en ambos extremos tienen una propiedad que se desplaza hacia el otro extremo. Los dos extremos siempre están sincronizados. Por ejemplo, si define una relación filiación con roles con el nombre de elementos primarios y secundarios, podría escribir:  
  
     `John.Children.Add(Mary)`  
  
     Ahora las dos expresiones siguientes son verdaderas:  
  
     `John.Children.Contains(Mary)`  
  
     `Mary.Parents.Contains(John)`  
  
     También podría conseguir el mismo efecto escribiendo:  
  
     `Mary.Parents.Add(John)`  
  
     Para obtener más información, consulte [navegar y actualizar un modelo de código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
-   **Reglas y eventos**. Puede definir reglas que se activan cada vez que se realizan cambios especificados. Por ejemplo, las reglas se usan para mantener al día con los elementos del modelo que presenta las formas en el diagrama. Para obtener más información, consulte [responder a y propagar los cambios](../modeling/responding-to-and-propagating-changes.md).  
  
-   **Serialización**. El almacén proporciona un método estándar para serializar los objetos que contiene a un archivo. Puede personalizar las reglas para serializar y deserializar. Para obtener más información, consulte [personalizar el almacenamiento de archivos y serialización XML](../modeling/customizing-file-storage-and-xml-serialization.md).  
  
## <a name="see-also"></a>Vea también  
 [Personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md)