---
title: En información general sobre supresiones de origen | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 046ae576880c6749c6bb033f66124c0085dfab16
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60057165"
---
# <a name="in-source-suppression-overview"></a>Información general sobre supresiones en código fuente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Supresión en el código fuente es la capacidad para suprimir o pasar por alto infracciones de análisis de código en código administrado mediante la adición de la **SuppressMessage** los segmentos de código que provocan las infracciones de atributo. El **SuppressMessage** es un atributo condicional que se incluye en los metadatos de IL del ensamblado de código administrado solo si se ha definido el símbolo de compilación CODE_ANALYSIS en tiempo de compilación.  
  
 En C++/CLI, use las macros CA_GLOBAL_SUPPRESS_MESSAGE o CA_SUPPRESS_MESSAGE en el archivo de encabezado para agregar el atributo.  
  
 No debe utilizar supresiones en código fuente en las compilaciones de versión para evitar que los metadatos de supresión en el origen de trasvase de registros por accidente. Debido al costo de procesamiento de supresión en el código fuente, también puede disminuir el rendimiento de la aplicación mediante la inclusión de los metadatos de supresión en el código fuente.  
  
> [!NOTE]
>  No tiene a mano código estos atributos por sí mismo. Para obtener más información, vea [Cómo: Suprimir advertencias mediante el elemento de menú](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md). El elemento de menú no está disponible para código C++.  
  
## <a name="suppressmessage-attribute"></a>Atributo SuppressMessage  
 Cuando haga clic en una advertencia de análisis de código en el **lista de errores** y, a continuación, haga clic en **Suprimir mensajes**, un **SuppressMessage** se agrega un atributo en el código o en el archivo de supresiones globales del proyecto.  
  
 El **SuppressMessage** atributo tiene el formato siguiente:  
  
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
  
- **Categoría de regla** -la categoría en la que se define la regla. Para obtener más información acerca de las categorías de regla de análisis de código, vea [Code Analysis for Managed Code Warnings](../code-quality/code-analysis-for-managed-code-warnings.md).  
  
- **Id. de regla** -el identificador de la regla. La compatibilidad incluye tanto un nombre corto y largo para el identificador de regla. El nombre corto es la regla. el nombre corto es CAXXXX.  
  
- **Justificación** -el texto que se usa para documentar el motivo para suprimir el mensaje.  
  
- **Id. de mensaje** -identificador único de un problema para cada mensaje.  
  
- **Ámbito** -el destino en el que se suprime la advertencia. Si el destino no se especifica, se establece en el destino del atributo. Los ámbitos admitidos incluyen lo siguiente:  
  
    - Module  
  
    - Espacio de nombres  
  
    - Recurso  
  
    - Tipo  
  
    - Miembro  
  
- **Destino** : un identificador que se usa para especificar el destino en el que se suprime la advertencia. Debe contener un nombre de elemento completo.  
  
## <a name="suppressmessage-usage"></a>Uso de SuppressMessage  
 Se suprimen las advertencias de análisis de código en el nivel al que una instancia de la **SuppressMessage** se aplica el atributo. El propósito de esto es acoplando la información de supresión en el código donde se produce la infracción.  
  
 La forma general de supresión incluye la categoría de regla y un identificador de regla que contiene una representación legible opcional del nombre de la regla. Por ejemplo,  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 Si hay razones de rendimiento estricta para minimizar los metadatos de supresión en el código fuente, se puede omitir el nombre de la regla. La categoría de regla y el identificador de regla constituyen en conjunto un identificador de regla lo suficientemente exclusivos. Por ejemplo,  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 No se recomienda este formato debido a problemas de mantenimiento.  
  
## <a name="suppressing-multiple-violations-within-a-method-body"></a>Suprimir varias infracciones dentro de un cuerpo de método  
 Los atributos solo se pueden aplicar a un método y no se puede incrustar dentro del cuerpo del método. Sin embargo, puede especificar el identificador como el identificador del mensaje para distinguir varias apariciones de una infracción dentro de un método.  
  
 [!code-cpp[InSourceSuppression#1](../snippets/cpp/VS_Snippets_CodeAnalysis/InSourceSuppression/cpp/insourcesuppression.cpp#1)]
 [!code-csharp[InSourceSuppression#1](../snippets/csharp/VS_Snippets_CodeAnalysis/InSourceSuppression/cs/InSourceSuppression.cs#1)]
 [!code-vb[InSourceSuppression#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/InSourceSuppression/vb/InSourceSuppression.vb#1)]  
  
## <a name="generated-code"></a>Código generado  
 Los compiladores de código administrado y algunas herramientas de otros fabricantes generan código para facilitar el desarrollo rápido de código. Código generado por el compilador que aparece en los archivos de código fuente normalmente está marcado con el **GeneratedCodeAttribute** atributo.  
  
 Puede elegir si se debe suprimir las advertencias de análisis de código y los errores de código generado. Para obtener información sobre cómo suprimir estas advertencias y errores, vea [Cómo: Suprimir advertencias de código generado](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).  
  
 Tenga en cuenta que el análisis de código omite **GeneratedCodeAttribute** cuando se aplica a todo el ensamblado o un parámetro único. Estas situaciones se producen con poca frecuencia.  
  
## <a name="global-level-suppressions"></a>Supresiones de nivel global  
 La herramienta de análisis de código administrado examina **SuppressMessage** atributos que se aplican en el nivel de ensamblado, módulo, tipo, miembro o parámetro. También se desencadena las infracciones contra los recursos y los espacios de nombres. Estas infracciones deben aplicarse en el nivel global y son ámbito y de destino. Por ejemplo, el mensaje siguiente suprime una infracción de espacio de nombres:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  Al suprimir una advertencia con ámbito de espacio de nombres, se suprime la advertencia en el espacio de nombres. No se suprime la advertencia contra los tipos del espacio de nombres.  
  
 Cualquier supresión se puede expresar mediante la especificación de un ámbito explícito. Estas supresiones deben residir en el nivel global. No se puede especificar la supresión de nivel de miembro mediante la decoración de un tipo.  
  
 Las supresiones de nivel global son la única manera para suprimir los mensajes que hacen referencia al código generado por el compilador que no se asigna a la fuente de usuario proporcionado explícitamente. Por ejemplo, el código siguiente suprime la infracción contra un constructor emitido por el compilador:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  Destino siempre contiene el nombre del elemento completo.  
  
## <a name="global-suppression-file"></a>Archivo de supresión global  
 El archivo de supresión global mantiene supresiones de nivel global o supresiones que no especifican un destino. Por ejemplo, las supresiones de las infracciones de nivel de ensamblado se almacenan en este archivo. Además, algunas supresiones de ASP.NET se almacenan en este archivo porque la configuración del nivel de proyecto no está disponibles para el código detrás de un formulario. Se crea y se agrega al proyecto la primera vez que seleccione una supresión global la **en el archivo de supresión del proyecto** opción de la **Suprimir mensajes** comando en la ventana Lista de errores. Para obtener más información, vea [Cómo: Suprimir advertencias mediante el elemento de menú](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Diagnostics.CodeAnalysis>
