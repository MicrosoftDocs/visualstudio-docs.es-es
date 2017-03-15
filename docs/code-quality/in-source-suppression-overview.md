---
title: "Informaci&#243;n general sobre supresiones en c&#243;digo fuente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "supresión de fuente, análisis de código"
  - "análisis de código, supresión de fuente"
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 40
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 40
---
# Informaci&#243;n general sobre supresiones en c&#243;digo fuente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La supresión en código fuente es la capacidad de suprimir u obviar las infracciones de análisis de código administrado agregando el atributo **SuppressMessage** a los segmentos de código que producen esas infracciones.  El atributo **SuppressMessage** es un atributo condicional que se incluye en los metadatos IL del ensamblado de código administrado solo si el símbolo de compilación CODE\_ANALYSIS se define en tiempo de compilación.  
  
 En C\+\+\/CLI, utilice las macros CA\_SUPPRESS\_MESSAGE o CA\_GLOBAL\_SUPPRESS\_MESSAGE del archivo de encabezado, agregar el atributo.  
  
 No debe emplear supresiones en código fuente en compilaciones de lanzamiento para evitar distribuir los metadatos de supresión en código fuente accidentalmente.  Debido al costo de procesamiento de la supresión en código fuente, el rendimiento de la aplicación también se puede degradar si se incluyen los metadatos de supresión en el código fuente.  
  
> [!NOTE]
>  No es necesario que controle mediante código estos atributos por sí mismo.  Para obtener más información, vea [Cómo: Suprimir advertencias mediante el elemento de menú](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  El elemento de menú no está disponible para el código C\+\+.  
  
## Atributo SuppressMessage  
 Si hace clic con el botón secundario del mouse en una advertencia de análisis de código en la **Lista de errores** y hace clic en **Suprimir mensajes**, se agrega un atributo **SuppressMessage** al código o al archivo de supresiones globales del proyecto.  
  
 El atributo **SuppressMessage** tiene el formato siguiente:  
  
```vb  
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>  
```  
  
```c#  
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]  
  
```  
  
 \[C\+\+\]  
  
```  
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")  
  
```  
  
 Donde:  
  
-   **Rule Category**: categoría en la que se define la regla.  Par obtener más información sobre las categorías de reglas de análisis de código, vea [Análisis de código de las advertencias de código administrado](../code-quality/code-analysis-for-managed-code-warnings.md).  
  
-   **Rule Id**: identificador de la regla.  Admite un nombre corto y uno largo para el identificador de la regla.  El nombre corto es CAXXXX; el nombre largo es CAXXXX:NombreDeArchivoDescriptivo.  
  
-   **Justification**: texto usado para documentar la razón por la que se suprime el mensaje.  
  
-   **Message Id**: identificador único de un problema para cada mensaje.  
  
-   **Scope**: destino en el que se suprime la advertencia.  Si no se especifica el destino, se establece en el destino del atributo.  Los ámbitos admitidos incluyen los siguientes:  
  
    -   Module  
  
    -   Espacio de nombres  
  
    -   Recurso  
  
    -   Tipo  
  
    -   Miembro  
  
-   **Target**: identificador usado para especificar el destino en el que se suprime la advertencia.  Debe contener un nombre de elemento completo.  
  
## Uso de SuppressMessage  
 Las advertencias de análisis de código se suprimen en el nivel al que se aplica una instancia del atributo **SuppressMessage**.  El propósito de esto es acoplar herméticamente la información de supresión al código donde se produce la infracción.  
  
 La forma de supresión general incluye la categoría de regla y un identificador de la regla, que contiene una representación legible opcional del nombre de la regla.  Por ejemplo,  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 Si hay motivos de limitación del rendimiento para minimizar los metadatos de supresión del código fuente, se puede omitir el nombre de la regla propiamente dicho.  La categoría y el identificador de regla constituyen en conjunto un identificador de regla suficientemente único.  Por ejemplo,  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 No se recomienda este formato debido a los problemas del mantenimiento.  
  
## Suprimir varias infracciones contenidas en el cuerpo del método  
 Los atributos sólo se pueden aplicar a un método y no se puede incrustar dentro del cuerpo del método.  Sin embargo, puede especificar el identificador como identificador del mensaje para distinguir varias apariciones de una infracción dentro de un método.  
  
 [!code-cpp[InSourceSuppression#1](../code-quality/codesnippet/CPP/in-source-suppression-overview_1.cpp)]
 [!code-vb[InSourceSuppression#1](../code-quality/codesnippet/VisualBasic/in-source-suppression-overview_1.vb)]
 [!code-cs[InSourceSuppression#1](../code-quality/codesnippet/CSharp/in-source-suppression-overview_1.cs)]  
  
## Código generado  
 Los compiladores de código administrado y algunas herramientas de otros fabricantes generan código para facilitar el desarrollo rápido de código.  El código generado por un compilador que aparece en los archivos de código fuente suele ir marcado con el atributo **GeneratedCodeAttribute**.  
  
 Puede elegir si desea suprimir las advertencias y los errores de análisis del código generado.  Para obtener información sobre cómo suprimir tales advertencias y errores, vea [Cómo: Suprimir advertencias de análisis de código en código generado](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).  
  
 Observe que el análisis de código obvia **GeneratedCodeAttribute** cuando se aplica a un ensamblado completo o a un parámetro único.  Estas situaciones se dan en raras ocasiones.  
  
## Supresiones de nivel global  
 La herramienta de análisis de código administrado examina los atributos **SuppressMessage** que se aplican en el nivel de ensamblado, módulo, tipo, miembro o parámetro.  También desencadena las infracciones contra los recursos y espacios de nombres.  Estas infracciones se deben aplicar en el nivel global y tienen un ámbito y un destino establecidos.  Por ejemplo, el mensaje siguiente suprime una infracción de espacio de nombres:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  Cuando se suprime una advertencia con ámbito del espacio de nombres, se suprime la advertencia contra el propio espacio de nombres.  No se suprime la advertencia contra los tipos dentro del espacio de nombres.  
  
 Cualquier supresión se puede expresar especificando un ámbito explícito.  Estas supresiones deben residir en el nivel global.  No se puede especificar una supresión de nivel de miembro mediante la decoración de un tipo.  
  
 Las supresiones de nivel global son la única manera de suprimir mensajes que hacen referencia al código generado por el compilador que no se asigna explícitamente al código fuente de usuario proporcionado.  Por ejemplo, el código siguiente suprime la infracción contra un constructor emitido por el compilador:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  El destino siempre contiene el nombre de elemento completo.  
  
## Archivo de supresiones global  
 El archivo de supresión global mantiene supresiones de nivel global o que no especifican un destino.  Por ejemplo, las supresiones por infracciones de nivel de ensamblado se almacenan en este archivo.  Además, algunas supresiones de ASP.NET se almacenan en este archivo porque no hay una configuración de nivel de proyecto para el código subyacente del formulario.  Una supresión global se crea y agrega al proyecto la primera vez que selecciona la opción **En archivo de supresión de proyecto** del comando **Suprimir mensajes** en la ventana Lista de errores.  Para obtener más información, vea [Cómo: Suprimir advertencias mediante el elemento de menú](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  
  
## Vea también  
 <xref:System.Diagnostics.CodeAnalysis>