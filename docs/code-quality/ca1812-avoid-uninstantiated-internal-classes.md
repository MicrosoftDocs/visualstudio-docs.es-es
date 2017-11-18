---
title: 'CA1812: Evitar las clases internas sin instancia | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6f6344b5dca6df21cba4d9a747925a24fffe1025
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: Evitar las clases internas sin instancia
|||  
|-|-|  
|TypeName|AvoidUninstantiatedInternalClasses|  
|Identificador de comprobación|CA1812|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 El código del ensamblado no crea una instancia del tipo del nivel de ensamblado.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Esta regla intenta buscar una llamada a uno de los constructores del tipo y notifica una infracción si no se encuentra ninguna llamada.  
  
 Esta regla no examina los siguientes tipos:  
  
-   Tipos de valor  
  
-   Tipos abstractos  
  
-   Enumeraciones  
  
-   Delegados  
  
-   Tipos de matriz emitidos por el compilador  
  
-   Tipos que no se pueden crear instancias y que definen `static` (`Shared` en Visual Basic) solo los métodos.  
  
 Si aplica <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> al ensamblado que se está analizando, esta regla no se producirá en todos los constructores que se marcan como `internal` porque no se puede saber si un campo está en uso por otro `friend` ensamblado.  
  
 Aunque no se puede evitar esta limitación en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] análisis de código, se producirá el FxCop independiente externo en constructores internos si cada `friend` ensamblado está presente en el análisis.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el tipo o agregue el código que lo utilice. Si el tipo solo contiene métodos estáticos, agregue uno de los siguientes al tipo para evitar que el compilador emita un constructor de instancia público predeterminado:  
  
-   Un constructor privado para tipos que tienen como destino [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] las versiones 1.0 y 1.1.  
  
-   El `static` (`Shared` en Visual Basic) modificador para tipos que tienen como destino [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla. Se recomienda que se suprime esta advertencia en las situaciones siguientes:  
  
-   Se crea la clase a través de métodos de reflexión en tiempo de ejecución como <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.  
  
-   La clase se crea automáticamente en tiempo de ejecución o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Por ejemplo, las clases que implementan <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> o <xref:System.Web.IHttpHandler?displayProperty=fullName>.  
  
-   La clase se pasa como un parámetro de tipo genérico que tiene una nueva restricción. Por ejemplo, en el ejemplo siguiente, se producirá esta regla.  
  
    ```csharp  
    internal class MyClass  
    {     
        public DoSomething()     
        {  
        }  
    }   
    public class MyGeneric<T> where T : new()  
    {  
        public T Create()  
        {  
            return new T();     
        }  
    }  
    // [...]   
    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();  
    mc.Create();  
    ```  
  
 En estas situaciones, se recomienda que suprimir esta advertencia.  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1811: Evitar código privado al que no se llama](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1801: Revisar parámetros sin utilizar](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)