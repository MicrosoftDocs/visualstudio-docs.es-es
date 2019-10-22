---
title: En información general sobre supresión de código fuente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 63d405b0e62735c0c1e3d7bb716ea2db29bc19fe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651576"
---
# <a name="in-source-suppression-overview"></a>Información general sobre supresiones en código fuente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La supresión en el código fuente es la capacidad de suprimir u omitir las infracciones de análisis de código en el código administrado agregando el atributo **SuppressMessage** a los segmentos de código que causan las infracciones. El atributo **SuppressMessage** es un atributo condicional que se incluye en los metadatos de Il del ensamblado de código administrado solo si el símbolo de compilación CODE_ANALYSIS se define en tiempo de compilación.

 En C++/CLI, use las macros CA_SUPPRESS_MESSAGE o CA_GLOBAL_SUPPRESS_MESSAGE en el archivo de encabezado para agregar el atributo.

 No debe usar supresiones en el origen en las compilaciones de versión para evitar que los metadatos de supresión en el código fuente se envíen accidentalmente. Debido al costo de procesamiento de la supresión en el código fuente, el rendimiento de la aplicación también se puede degradar incluyendo los metadatos de supresión en el código fuente.

> [!NOTE]
> No tiene que codificar manualmente estos atributos. Para obtener más información, vea [Cómo: suprimir advertencias mediante el elemento de menú](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md). El elemento de menú no está disponible C++ para el código.

## <a name="suppressmessage-attribute"></a>SuppressMessage (atributo)
 Al hacer clic con el botón secundario en una advertencia de análisis de código en el **lista de errores** y, a continuación, hacer clic en **suprimir mensajes**, se agrega un atributo **SuppressMessage** en el código o en el archivo de supresiones global del proyecto.

 El atributo **SuppressMessage** tiene el formato siguiente:

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]

```

 [C++]

```
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")

```

 Dónde:

- **Categoría de regla** : la categoría en la que se define la regla. Para obtener más información sobre las categorías de reglas de análisis de código, vea [análisis de código para advertencias de código administrado](../code-quality/code-analysis-for-managed-code-warnings.md).

- **Identificador de regla** : el identificador de la regla. La compatibilidad incluye un nombre corto y largo para el identificador de regla. El nombre corto es CAXXXX; el nombre largo es CAXXXX: FriendlyTypeName.

- **Justificación** : el texto que se usa para documentar el motivo de la supresión del mensaje.

- **Identificador de mensaje** : identificador único de un problema para cada mensaje.

- **Ámbito** : el destino en el que se va a suprimir la advertencia. Si no se especifica el destino, se establece en el destino del atributo. Entre los ámbitos admitidos se incluyen los siguientes:

  - Module

  - Espacio de nombres

  - Recurso

  - Type

  - Miembro

- **Target** : un identificador que se usa para especificar el destino en el que se va a suprimir la advertencia. Debe contener un nombre de elemento completo.

## <a name="suppressmessage-usage"></a>Uso de SuppressMessage
 Las advertencias de análisis de código se suprimen en el nivel al que se aplica una instancia del atributo **SuppressMessage** . La finalidad de esto es acoplar estrechamente la información de supresión en el código donde se produce la infracción.

 La forma general de supresión incluye la categoría de regla y un identificador de regla que contiene una representación opcional inteligible del nombre de la regla. Por ejemplo,

 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

 Si hay razones de rendimiento estrictas para minimizar los metadatos de supresión en el código fuente, se puede dejar el propio nombre de la regla. La categoría de regla y su identificador de regla forman un identificador de regla suficientemente único. Por ejemplo,

 `[SuppressMessage("Microsoft.Design", "CA1039")]`

 No se recomienda este formato debido a problemas de mantenimiento.

## <a name="suppressing-multiple-violations-within-a-method-body"></a>Suprimir varias infracciones dentro del cuerpo de un método
 Los atributos solo se pueden aplicar a un método y no se pueden incrustar en el cuerpo del método. Sin embargo, puede especificar el identificador como el identificador de mensaje para distinguir varias repeticiones de una infracción dentro de un método.

 [!code-cpp[InSourceSuppression#1](../snippets/cpp/VS_Snippets_CodeAnalysis/InSourceSuppression/cpp/insourcesuppression.cpp#1)]
 [!code-csharp[InSourceSuppression#1](../snippets/csharp/VS_Snippets_CodeAnalysis/InSourceSuppression/cs/InSourceSuppression.cs#1)]
 [!code-vb[InSourceSuppression#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/InSourceSuppression/vb/InSourceSuppression.vb#1)]

## <a name="generated-code"></a>Código generado
 Los compiladores de código administrado y algunas herramientas de terceros generan código para facilitar el desarrollo rápido de código. El código generado por el compilador que aparece en los archivos de código fuente normalmente se marca con el atributo **GeneratedCodeAttribute** .

 Puede decidir si desea suprimir los errores y advertencias de análisis de código para el código generado. Para obtener información sobre cómo suprimir estas advertencias y errores, consulte [Cómo: suprimir advertencias para el código generado](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

 Tenga en cuenta que el análisis de código omite **GeneratedCodeAttribute** cuando se aplica a un ensamblado completo o a un solo parámetro. Estas situaciones se producen con poca frecuencia.

## <a name="global-level-suppressions"></a>Supresiones de nivel global
 La herramienta de análisis de código administrado examina los atributos **SuppressMessage** que se aplican en el nivel de ensamblado, módulo, tipo, miembro o parámetro. También activa las infracciones en los recursos y espacios de nombres. Estas infracciones deben aplicarse en el nivel global y tienen el ámbito y el destino. Por ejemplo, el siguiente mensaje suprime una infracción del espacio de nombres:

 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Cuando se suprime una advertencia con el ámbito de espacio de nombres, se suprime la advertencia en el espacio de nombres. No suprime la advertencia en los tipos del espacio de nombres.

 Cualquier supresión se puede expresar especificando un ámbito explícito. Estas supresiones deben residir en el nivel global. No se puede especificar la supresión de nivel de miembro decorando un tipo.

 Las supresiones de nivel global son la única manera de suprimir los mensajes que hacen referencia al código generado por el compilador que no se asigna a un origen de usuario proporcionado explícitamente. Por ejemplo, el siguiente código suprime una infracción en un constructor emitido por compilador:

 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> Target siempre contiene el nombre de elemento completo.

## <a name="global-suppression-file"></a>Archivo de supresión global
 El archivo de supresión global mantiene las supresiones que son supresiones de nivel global o supresiones que no especifican un destino. Por ejemplo, las supresiones para las infracciones de nivel de ensamblado se almacenan en este archivo. Además, algunas supresiones de ASP.NET se almacenan en este archivo porque la configuración de nivel de proyecto no está disponible para el código subyacente de un formulario. Una supresión global se crea y se agrega al proyecto la primera vez que se selecciona la opción **en el archivo de supresión del proyecto** del comando **suprimir mensajes** en la ventana de lista de errores. Para obtener más información, vea [Cómo: suprimir advertencias mediante el elemento de menú](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).

## <a name="see-also"></a>Vea también
 <xref:System.Diagnostics.CodeAnalysis>
