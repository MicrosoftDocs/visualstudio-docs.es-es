---
title: Escribir código para personalizar lenguajes específicos de dominio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming
ms.assetid: a4a17f5b-9c97-4575-b2d1-3182c1896b72
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: affa3db292ed23ca52b0cca810daf5ca70ad0fd1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866329"
---
# <a name="writing-code-to-customise-a-domain-specific-language"></a>Escribir código para personalizar lenguajes específicos de dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En esta sección se muestra cómo usar código personalizado para acceder, modificar o crear un modelo en un lenguaje específico de dominio.  
  
 Hay varios contextos en los que puede escribir código que funciona con un DSL:  
  
- **Comandos personalizados.** Puede crear un comando que los usuarios pueden invocar con el botón secundario en el diagrama, y que puede modificar el modelo. Para obtener más información, consulte [Cómo: agregar un comando al menú contextual](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
- **Validation (Validación).** Puede escribir código que comprueba que el modelo está en un estado correcto. Para obtener más información, consulte [validación en los lenguajes específicos de dominio](../modeling/validation-in-a-domain-specific-language.md).  
  
- **Invalidar el comportamiento predeterminado.** Puede modificar muchos aspectos del código que se genera a partir de DslDefinition.dsl. Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).  
  
- **Transformación de texto.** Puede escribir plantillas de texto que contienen código que tiene acceso a un modelo y genera un archivo de texto, por ejemplo, para generar código de programa. Para obtener más información, consulte [generar código desde un lenguaje específico de dominio](../modeling/generating-code-from-a-domain-specific-language.md).  
  
- **Otras extensiones de Visual Studio.** Puede escribir extensiones VSIX independientes que leer y modificar los modelos. Para obtener más información, vea [Cómo: abrir un modelo desde un archivo de código de programa](../modeling/how-to-open-a-model-from-file-in-program-code.md)  
  
  Las instancias de las clases que defina en DslDefinition.dsl se mantienen en una estructura de datos denominada el *Store In-Memory* (IMS) o *Store*. Las clases que defina en un DSL siempre toman un Store como argumento al constructor. Por ejemplo, si su DSL define una clase llamada de ejemplo:  
  
  `Example element = new Example (theStore);`  
  
  mantener los objetos en el Store (en lugar de objetos como normales) ofrece varias ventajas.  
  
- **Las transacciones**. Puede agrupar una serie de cambios relacionados en una transacción:  
  
   `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`  
  
   `{`  
  
   `// make several changes to Store elements here`  
  
   `t.Commit();`  
  
   `}`  
  
   Si se produce una excepción durante los cambios, por lo que no se realiza el Commit() final, se restablecerá el Store a su estado anterior. Esto le ayudará a asegurarse de que los errores no dejar el modelo en un estado incoherente. Para obtener más información, consulte [navegar y actualizar un modelo en el código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
- **Las relaciones binarias**. Si define una relación entre dos clases, las instancias en ambos extremos tienen una propiedad que se navega hacia el otro extremo. Los dos extremos siempre están sincronizados. Por ejemplo, si define una relación de parenthood con roles denominados padres e hijos, podría escribir:  
  
   `John.Children.Add(Mary)`  
  
   Ahora las dos expresiones siguientes son verdaderas:  
  
   `John.Children.Contains(Mary)`  
  
   `Mary.Parents.Contains(John)`  
  
   También podría lograr el mismo efecto escribiendo:  
  
   `Mary.Parents.Add(John)`  
  
   Para obtener más información, consulte [navegar y actualizar un modelo en el código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
- **Reglas y eventos**. Puede definir reglas que se activan cada vez que se realizan cambios especificados. Por ejemplo, las reglas se usan para mantener las formas en el diagrama al día con los elementos del modelo que presenta. Para obtener más información, consulte [responde a y propagar los cambios](../modeling/responding-to-and-propagating-changes.md).  
  
- **Serialización**. El Store proporciona una manera estándar para serializar los objetos que contiene a un archivo. Puede personalizar las reglas para serializar y deserializar. Para obtener más información, consulte [personalizar el almacenamiento de archivos y serialización XML](../modeling/customizing-file-storage-and-xml-serialization.md).  
  
## <a name="see-also"></a>Vea también  
 [Personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md)



