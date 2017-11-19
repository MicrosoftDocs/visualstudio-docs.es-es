---
title: "En información general sobre supresiones de origen | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f35833df8e84a4e4caba8fd46f8daea8dd5119a1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="in-source-suppression-overview"></a>Información general sobre supresiones en código fuente
Supresión en el código fuente es la capacidad para suprimir o pasar por alto infracciones de análisis de código en código administrado mediante la adición de la **SuppressMessage** atribuir a los segmentos de código que producen esas infracciones. El **SuppressMessage** es un atributo condicional que se incluye en los metadatos IL del ensamblado de código administrado solo si el símbolo de compilación CODE_ANALYSIS se define en tiempo de compilación.  
  
 En C++ / CLI, use las macros CA_SUPPRESS_MESSAGE o CA_GLOBAL_SUPPRESS_MESSAGE en el archivo de encabezado, agregar el atributo.  
  
 No se deben usar supresiones en código fuente en versiones de lanzamiento para evitar distribuir los metadatos de supresión en código fuente accidentalmente. Debido al costo de procesamiento de supresión en el código fuente, el rendimiento de la aplicación también puede reducirse mediante la inclusión de los metadatos de supresión en el código fuente.  
  
> [!NOTE]
>  No tienes a mano código estos atributos por sí mismo. Para obtener más información, consulte [Cómo: Suprimir advertencias mediante el elemento de menú](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md). El elemento de menú no está disponible para código de C++.  
  
## <a name="suppressmessage-attribute"></a>SuppressMessage (atributo)  
 Cuando hace doble clic en una advertencia de análisis de código en el **lista de errores** y, a continuación, haga clic en **Suprimir mensajes**, **SuppressMessage** se agrega el atributo en el código o en el archivo de supresiones globales del proyecto.  
  
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
  
-   **Categoría de regla** -la categoría en la que se define la regla. Para obtener más información acerca de las categorías de regla de análisis de código, vea [Code Analysis for Managed Code Warnings](../code-quality/code-analysis-for-managed-code-warnings.md).  
  
-   **Identificador de regla** -el identificador de la regla. La compatibilidad incluye tanto un nombre corto y largo para el identificador de regla. El nombre corto es la regla. el nombre corto es CAXXXX.  
  
-   **Justificación** -el texto que se utiliza para documentar el motivo para suprimir el mensaje.  
  
-   **Id. de mensaje** -identificador único de un problema para cada mensaje.  
  
-   **Ámbito** -el destino en el que se suprime la advertencia. Si no se especifica el destino, se establece en el destino del atributo. Los ámbitos admitidos son los siguientes:  
  
    -   Módulo  
  
    -   Espacio de nombres  
  
    -   Recurso  
  
    -   Tipo  
  
    -   Miembro  
  
-   **Destino** : un identificador que se utiliza para especificar el destino en el que se suprime la advertencia. Debe contener un nombre de elemento completo.  
  
## <a name="suppressmessage-usage"></a>Uso de SuppressMessage  
 Se suprimen las advertencias de análisis de código en el nivel al que una instancia de la **SuppressMessage** se aplica el atributo. El propósito de este es acoplar estrechamente la información de supresión al código donde se produce la infracción.  
  
 La forma general de supresión incluye la categoría de regla y un identificador de regla que contiene una representación legible opcional del nombre de la regla. Por ejemplo,  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 Si hay motivos de rendimiento estricta para minimizar los metadatos de supresión en el código fuente, se puede omitir el nombre de la regla. La categoría de regla y el identificador de regla constituyen en conjunto un identificador de regla suficientemente único. Por ejemplo,  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 No se recomienda este formato debido a problemas de mantenimiento.  
  
## <a name="suppressing-multiple-violations-within-a-method-body"></a>Suprimir varias infracciones contenidas dentro de un cuerpo de método  
 Atributos solo se puede aplicar a un método y no se puede incrustar dentro del cuerpo del método. Sin embargo, puede especificar el identificador como identificador del mensaje para distinguir varias apariciones de una infracción dentro de un método.  
  
 [!code-cpp[InSourceSuppression#1](../code-quality/codesnippet/CPP/in-source-suppression-overview_1.cpp)]
 [!code-vb[InSourceSuppression#1](../code-quality/codesnippet/VisualBasic/in-source-suppression-overview_1.vb)]
 [!code-csharp[InSourceSuppression#1](../code-quality/codesnippet/CSharp/in-source-suppression-overview_1.cs)]  
  
## <a name="generated-code"></a>Código generado  
 Los compiladores de código administrado y algunas herramientas de otros fabricantes generan código para facilitar el desarrollo rápido de código. Código generado por el compilador que aparece en los archivos de código fuente normalmente se marca con la **GeneratedCodeAttribute** atributo.  
  
 Puede elegir si se debe suprimir las advertencias de análisis de código y los errores de código generado. Para obtener información sobre cómo suprimir estas advertencias y errores, vea [Cómo: Suprimir advertencias de código generado por](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).  
  
 Tenga en cuenta que el análisis de código omite **GeneratedCodeAttribute** cuando se aplica a todo un ensamblado o un parámetro único. Rara vez se producen estas situaciones.  
  
## <a name="global-level-suppressions"></a>Supresiones de nivel global  
 La herramienta de análisis de código administrado examina **SuppressMessage** atributos que se aplican en el nivel de ensamblado, módulo, tipo, miembro o parámetro. También se desencadena infracciones contra los recursos y los espacios de nombres. Estas infracciones deben aplicarse en el nivel global y se ámbito y se aplican. Por ejemplo, el mensaje siguiente suprime una infracción de espacio de nombres:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  Cuando se suprime una advertencia con ámbito de espacio de nombres, se suprime la advertencia contra el espacio de nombres. No se suprime la advertencia contra los tipos dentro del espacio de nombres.  
  
 Cualquier supresión se puede expresar especificando un ámbito explícito. Estas supresiones deben residir en el nivel global. No se puede especificar la supresión de nivel de miembro decorando un tipo.  
  
 Supresiones de nivel global son la única manera de suprimir mensajes que hacen referencia al código generado por el compilador que no se asigna a la fuente de usuario proporcionado de manera explícita. Por ejemplo, el siguiente código elimina una infracción contra un constructor emitido por el compilador:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  El destino siempre contiene el nombre del elemento completo.  
  
## <a name="global-suppression-file"></a>Archivo de supresión global  
 El archivo de supresión global mantiene supresiones supresiones de nivel global o supresiones que no especifican un destino. Por ejemplo, supresiones de las infracciones de nivel de ensamblado se almacenan en este archivo. Además, algunas supresiones de ASP.NET se almacenan en este archivo porque la configuración del nivel de proyecto no está disponibles para el código detrás de un formulario. Una supresión global se crea y se agrega al proyecto la primera vez que seleccione la **en el archivo de supresión de proyecto** opción de la **Suprimir mensajes** comando en la ventana Lista de errores. Para obtener más información, consulte [Cómo: Suprimir advertencias mediante el elemento de menú](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Diagnostics.CodeAnalysis>